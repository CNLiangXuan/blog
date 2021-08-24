## 前言

这里主要讲解 **Breeze Mini** 的LED功能模块，完整代码在工程目录下的 **Modules** 子目录下的 **stm32f10x_module_led.c** 和 **stm32f10x_module_led.h** 中，该代码主要是控制位于四个机臂上的LED的亮灭来提示用户 **Breeze Mini** 的工作状态。

## 相关知识

STM32要实现LED的亮与灭其实就是实现GPIO口的高低电平控制，由于STM32的IO口要相比51要复杂得多，所以为了更好地理解，这里先简单介绍一下STM32的IO口。STM32的GPIO口可以被配置成8种模式：

```c
1. 输入浮空
2. 输入上拉
3. 输入下拉
4. 模拟输入
5. 开漏输出
6. 推挽输出
7. 推挽复用
8. 开漏复用
```

STM32的每个IO口都可以自由编程，但IO口的寄存器必须要按32位字被访问，STM32的IO口很多都是5V兼容的，这些IO口在与5V电平标准的外设连接时很有优势，具体哪些IO口是5V兼容的可以从芯片的datasheet管脚描述章节查到(I/O Level标有FT的就是5V兼容的)。

STM32的每个IO口都是由7个寄存器控制的，这7个寄存器分别是：

```c
2个32位的数据寄存器IDR和ODR
2个32位的端口配置寄存器CRL和CRH
1个16位的复位寄存器BRR
1个32位的锁存寄存器LCKR
1个32位的置位/复位寄存器BSRR
```

CRL和CRH寄存器控制IO口的模式和输出速率，STM32的IO口位配置表如下所示：

STM32输出模式如下表所示：

### CRL和CRH寄存器

接着再来看看端口低位配置寄存器 **(Config Register Low, i.e. CRL)** 的各位描述，该寄存器的复位值 **0X44444444**，从上图中可以看出，复位值其实就是配置端口为浮空输入模式，而且CRL控制着IO端口的低8个，每个IO端口的位占用CRL的4个位，其中高两位为配置 **CNF**，低两位配置 **MODE**：

```c
CNF
00：通用推挽输出
01：通用开漏输出
10：复用推挽输出
11：复用开漏输出
MODE
00：输入模式
01：输出模式(最大速率10MHz)
10：输出模式(最大速率2MHz)
11：输出模式(最大速率50MHz)
```

CRH的作用和CRL的一样，只是CRL控制的是低8个端口，而CRH控制的是高8个端口，现在讲解如何使用固件库来设置GPIO的工作模式和相关参数，操作GPIO的官方固件库代码在 **stm32f10x_gpio.c** 和 **stm32f10x_gpio.h** 中。在使用固件库开发过程中，操作CRH或者CRL寄存器来配置IO口的模式和速度是通过GPIO初始化函数

```c
void GPIO_Init(GPIO_TypeDef* GPIOx, GPIO_InitTypeDef* GPIO_InitStruct)
```

来实现的，这个函数有两个参数，第一个参数用来指定操作的GPIO，取值范围 **GPIOA~GPIOG**。
!!! info "注意"
    GPIOA~GPIOG只是对于 **STM32F103大容量系列产品来说的**，**Breeze Mini** 所选用的 **STM32F103TBU6** 只有完整的GPIOA口、部分GPIOB和部分GPIOD。
第二个参数为 **初始化结构体指针**，结构体类型为 **GPIO_InitTypeDef**，可以通过双击 **"GPIO_InitTypeDef"** 后右键点击 **"Go to definition of..."** 跳转到其定义处：
```c

typedef struct
{
    uint16_t          GPIO_Pin;
    GPIOSpeed_TypeDef GPIO_Speed;
    GPIOMode_TypeDef  GPIO_Mode;
}GPIO_InitTypeDef;
```

上面定义的初始化GPIO的结构体有三个成员变量，从变量名字可以得知其分别表示 **GPIO的端口**、**GPIO的工作速度** 和 **GPIO的工作模式**。这也可以从另一方面告诉我们初始化GPIO口的操作就是设置这些成员变量的值。通过 **初始化结构体GPIO_InitTypeDef** 来初始化GPIO的一般格式为：

```c
GPIO_InitTypeDef GPIO_InitStructure;
GPIO_InitStructure.GPIO_Pin   = GPIO_Pin_5;
GPIO_InitStructure.GPIO_Mode  = GPIO_Mode_Out_PP;
GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
GPIO_Init(GPIOA, &GPIO_InitStructure);
```

这段代码和我们前面所预测的实现是一样的，这段代码先定义了一个GPIO口的初始化结构体 **GPIO_InitTypeDef** 类型的变量 **GPIO_InitStructure**，然后第2行设置待配置管脚为 **GPIOA第5个端口**，第3行设置端口工作在 **推挽输出模式**，第4行设置端口最大工作速度为 **50MHz**。第5行则调用函数对设置好的参数进行初始化。

如果想知道`GPIO_Mode`成员变量都支持哪些值，可以双击 **"GPIO_Mode_Out_PP"** 后右键点击 **"Go to definition of..."** 跳转到其定义处：

```c
typedef enum
{ 
    GPIO_Mode_AIN         = 0x0,   //模拟输入
    GPIO_Mode_IN_FLOATING = 0x04,  //浮空输入
    GPIO_Mode_IPD         = 0x28,  //下拉输入
    GPIO_Mode_IPU         = 0x48,  //上拉输入
    GPIO_Mode_Out_OD      = 0x14,  //开漏输出
    GPIO_Mode_Out_PP      = 0x10,  //推挽输出
    GPIO_Mode_AF_OD       = 0x1C,  //开漏输出
    GPIO_Mode_AF_PP       = 0x18   //复用推挽
}GPIOMode_TypeDef;
```

使用同样的方法可以得到GPIO端口工作速度的定义：

```c
typedef enum
{ 
    GPIO_Speed_10MHz = 1,
    GPIO_Speed_2MHz, 
    GPIO_Speed_50MHz
}GPIOSpeed_TypeDef;
```

至于如何快速定位配置参数比如(GPIO_Speed_10MHz)的取值范围等技巧在 **开发常用技巧(Keil)** 中有详细的介绍，还不太清楚的用户可以再去了解一下。

### IDR寄存器

IDR(Input Data Register)是端口输入数据寄存器，是只读的，高16位保留，只用了低16位，且只能以16位的格式读出值。
以下是该寄存器各位的描述：

要想知道某个IO口的高低电平状态，就可以按16位的格式读这个寄存器，然后再查需要的位的状态即可。在固件库中操作IDR寄存器来获得IO端口电平的函数是：

```c
uint8_t GPIO_ReadInputDataBit(GPIO_TypeDef* GPIOx, uint16_t GPIO_Pin)
```

这样读取GPIOA的第5个端口的电平状态的代码是：

```c
GPIO_ReadInputDataBit(GPIOA, GPIO_Pin_5);
```

返回值为 **Bit_SET(高电平)** 或 **Bit_RESET(低电平)**

### ODR寄存器

ODR(Output Data Register)是端口输出数据寄存器，可读可写，只使用了低16位，当读寄存器时读出的是当前IO口的输出高低电平状态，当写寄存器时可以控制IO口的输出高低电平，该寄存器各位描述如下所示：

在固件库中操作ODR寄存器来设置和读取IO输出电平的函数是：

```c
void GPIO_Write(GPIO_TypeDef* GPIOx, uint16_t PortVal)
```

### BSRR寄存器

BSRR(Bit Set Reset Register)寄存器是端口位设置/清除寄存器，具有和ODR寄存器类似的作用，以下是该寄存器的各位描述：
比如要设置GPIOA的第5个端口的值为1，则只需要向GPIOA的BSRR寄存器的 **低16位** 的第5位写1：

```c
GPIOA -> BSRR = 1 << 5;
```

如果要置GPIOA的第5个端口的值为0，则只需向GPIOA的BSRR寄存器的 **高16位** 的第5位写1：

```c
GPIOA -> BSRR = 1 << (16 + 5);
```

注意向该寄存器写0是无效的，所以可以直接通过对1移指定位数来实现。

### BRR寄存器

BRR(Bit Reset Register)寄存器是端口位清除寄存器，和BSRR高16位的功能是一样的。在固件库中操作BSRR和BRR寄存器进而来设置GPIO输出状态的函数是：

```c
void GPIO_SetBits(GPIO_TypeDef* GPIOx, uint16_t GPIO_Pin)
void GPIO_ResetBits(GPIO_TypeDef* GPIOx, uint16_t GPIO_Pin)
```

在具体利用固件库操作GPIO的输出状态时常用的固件库函数是`GPIO_SetBits`和`GPIO_ResetBits`。

## 硬件连接

**Breeze Mini** 硬件上4个LED分别连接在 **GPIOA.11**、**GPIOA.12**、**GPIOA.8** 和 **GPIOA.15** 上，而且4个LED都是通过电阻上拉到VCC的，该部分原理图如下所示：
![breeze_embedded_led_sch](./images/led_sch.png)

## 软件设计
完整代码在工程目录下的 **Modules** 子目录下的 **stm32f10x_module_led.c** 和 **stm32f10x_module_led.h** 中，先简单介绍一些函数：

### LED初始化

```c
void LED_Init(void)
{
    GPIO_InitTypeDef GPIO_InitStructure;
    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOA | RCC_APB2Periph_AFIO, ENABLE);
    GPIO_InitStructure.GPIO_Pin   = GPIO_Pin_11 | GPIO_Pin_12 |
                                    GPIO_Pin_8  | GPIO_Pin_15;
    GPIO_InitStructure.GPIO_Mode  = GPIO_Mode_Out_PP;
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init(GPIOA, &GPIO_InitStructure);
    // When hardware disables the JATG, don't disable the SWD meanwhile.
    // Otherwise the chip will be damaged!!!
    AFIO->MAPR |= AFIO_MAPR_SWJ_CFG_JTAGDISABLE;
    LED_A_OFF;
    LED_B_OFF;
    LED_C_OFF;
    LED_D_OFF;
}
```

注意在配置STM32任意一个外设的时候，**都要先使能外设的时钟**，由于GPIOA是挂载在高速APB2总线上的外设，所以上面代码就调用了 ==RCC_APB2PeriphClockCmd== 函数来使能GPIOA时钟，对时钟部分还不太清楚的读者可以到 **STM32驱动开发-系统时钟树** 部分再了解一下。

在使能完成GPIOA的外设时钟后，将 **GPIOA.11**、**GPIOA.12**、**GPIOA.8** 和 **GPIOA.15** 分别设置成 **推挽输出** 模式，**IO口速度** 为50MHz，最后调用

```c
LED_A_OFF;
LED_B_OFF;
LED_C_OFF;
LED_D_OFF;
```

4个宏定义来关闭LED，由于LED是默认是上拉的，所以只有置端口为1才是关闭LED，比如LED_A_OFF的定义是这样的：

```c
#define LED_A_OFF    GPIO_SetBits(GPIOA, GPIO_Pin_11)
```

### LED状态机

## 参考

* [STM32开发指南-库函数版本_V3.1.pdf](https://documents-1256406063.cos.ap-shanghai.myqcloud.com/STM32F1%E5%BC%80%E5%8F%91%E6%8C%87%E5%8D%97-%E5%BA%93%E5%87%BD%E6%95%B0%E7%89%88%E6%9C%AC_V3.1%20.pdf), 正点原子, [ALLENTEK](http://www.alientek.com/).