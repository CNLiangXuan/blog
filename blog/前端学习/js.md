## JS

空类型：Undefined Null
使用typeof关键字来进行数据类型检测
语法:typeof 要检测的变量
结果:该变量存储的数据的数据类型

### 转数值

1.Number();

语法:Number(要转换的内容)

结果:转换好数值类型的结果

2.parseInt();

语法:parseInt(要转换的内容)

结果:转换好数值类型的结果

3.parseFloat();

语法:parseFloat(要转换的内容)

结果:转换好数值类型的结果

两者的区别：Number只要有不是数字的就出现NaN，parseInt会把前面的数字转化出来，只有当第一位就不是数字
时才转化为NaN,parseFloat与parseInt一致，但parseFloat可以显示小数

### 转字符串

1.String();

语法:String(要转换的内容)

结果:转换好字符串类型的结果

2. toString();

语法:要转换的内容.toString()

结果:转换好字符串类型的结果
### 转布尔

1.Boolean();

语法:要转换的内容.Boolean()

结果:转换好布尔类型的结果

>注释：false:  0 NaN '' undefined null
其他都转换为true
### 赋值运算符

= ：进行值操作

+= ：加等于运算符

-=  ：减等于运算符

*= ：乘等于运算符

/= ：除等于运算符

%= ：取余等于运算符

### 比较运算符

>︰大于比较

< ：小于比较

>= ：大于等于

<= ：小于等于

== ：等于

**== ： 只比较值是否相等，不考虑数据类型**

=== ：全等于

**=== ： 值和数据类型都相等才等于**

!= ： 不等于比较不考虑数据类型

!== ：不全等于比较考虑数据类型

### 逻辑运算符

与 ：&&

或 ： ||

非 ：！

### 自增自减运算符

++i : 前置++，先自增后运算，参与运算的值为i+1

i++ ：后置++，先运算后++，参与运算的值为i

--i : 前置--，先自减后运算，参与运算的值为i-1

i-- ：后置--，先运算后--，参与运算的值为i
### 函数

```js
function 函数名（）{
    函数内为形参
}
//调用一个函数，添加两个实参，给形参进行赋值
函数名（10，20）
```

### 函数作用域

```js
// 访问：自己有就用自己的，自己没有用父级的，以此类推，到全局都没有就报错
//自己给自己赋值，自己没有给父级的赋值。以此类推，到全局都没有，定义为全局再赋值
```

### 对象

```js
//   创建一个对象
var obj = {
  a: 100,
  b: true,
  c: 'hello world'
}
//  增，向对象内添加一个键值对
obj.name = '小灰狼'
obj['age'] = 18

//  删
delete obj.name
delete obj['age']

//  改
obj.name = '公羊'
obj['age'] = '60'

//  查
console.log(obj.name)
console.log(obj['age'])
```

### 数组

```js
 var arr = [100, 200, 300, 400]
  console.log(arr)
  console.log(arr.length)
  //  修改数组长度
  arr.length = 3
  console.log(arr)
  console.log(arr.length)

//  输出索引为2 的数据
  console.log(arr[2])

//  修改所引的数据
  arr[2] = 3
  console.log(arr[2])
//  数组的遍历
  for (let i = 0; i < arr.length; i ++){
    console.log(arr[i])
  }
```
### 数组常用方法
