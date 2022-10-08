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

```js
1.push
 作用：添加新元素至最后
  const res = arr.push('追加的')
  console.log(res)
//  返回值为该数组长度
2.pop()
语法︰数组. pop()
作用︰删除数组最后一个数据
返回值︰被删除的数据
3.unshift()
语法︰数组.unshift(数据)
作用︰将数据添加到数组的最前
返回值︰添加数据后数组最新的长度
4.shift()
语法︰数组.shift()
作用:删除数组最前一个数据
返回值︰被删除的数据
5. reyerse()
语法∶数组.reverse()
作用:将数组反转
返回值︰反转后的数组
6.splice()
语法︰数组.splice(开始索引，多少个，要插入的数据)
开始索引:默认是0
多少个:默认是0
要插入的数据︰默认是没有(从哪删除从哪插入)
作用︰删除数组中若干数据，并选择是否插入新的数据
返回值︰以新数组的形式返回被删除的数据
7. sort()
语法∶
值:排序好的新数组
8. join()
语法∶数组.join(连接符)
作用:将数组用连接符连接成为一个字符串
返回值:连接好的字符串
9.concat()
语法︰数组.concat(其他数组)
作用︰将其他数组和数组拼接在一起
返回值︰拼接好的 新数组
10.slice()
语法︰数组.slice(开始索引，结束索引)
开始索引:默认是0
结束索引︰默认是数组长度
作用︰截取数组中的某些数据
返回值:以新数组的形式返回截取出来的数据
11.indexQf()
语法︰数组.indexOf(数据)
作用:查找数据在数组中的索引位置
返回值:
有该数据，返回第一次出现的索引位置
没有该数据，返回-1
12.forEach()
语法︰数组.forEach( function ( item，index,arr ){})
作用︰遍历数组
返回值︰无
13.map()
语法︰数组.map( function ( item,index,arr ){})
作用:映射数组
返回值︰映射后的新数组
14.filter()
语法︰数组.filter( function ( item，index,arr ) {} )
作用︰过滤数组
返回值∶过滤后的新数组
15.eyery()
语法︰数组.every( function (item,index,arr ) {})
作用︰判断数组是不是每一项都满足条件
返回值:一个布尔值
16.some()
语法︰数组.some( function ( item，index,arr ) {})
作用︰判断数组是不是有某一项满足条件
返回值∶一个布尔值
```

### 字符串常用方法

```js
1.charAt()
语法︰字符串.charAt(索引)作用︰获取对应索引位置的字符
返回值:对应索引位置的字符

2. toLowerCase()
语法∶字符串.toLowerCase()
作用︰将字符串内的字母全部转换成小写
返回值∶转换好的字符串

3. toUppercase()
语法︰字符串.toUpperCase()
作用︰将字符串内的字母全部转换成大写
返回值︰转换好的字符串

4. replace()
语法︰字符串.replace('换下内容'，'换上内容')
作用︰将字符串内第一个满足换下内容的片段替换成换上内容
返回值︰替换好的字符串

5. trim()
语法︰字符串.trim()
作用︰去除字符串收尾的空格
返回值︰去除空格后的字符串

6.split()
语法∶字符串.split(分隔符)
作用︰按照分隔符将字符串切割成为一个数组
返回值︰切割后的数组

7. substr()
语法︰字符串.substr(开始索引,多少个）
8.substring()
语法︰字符串.substring(开始索引,结束索引）
9. slice()
语法︰字符串.slice(开始索引，结束索引）
以上三个
作用︰截取字符串
返回值︰截取出来的字符串
```

### 数字常用方法

```js
1.random()
语法:Math.random()
作用︰获取0 ~1之间的随机小数，
包含0，但是不包含1
返回值:0 ~1之间的随机小数

2 .round()
语法: Math.round(数字)
作用︰对数字进行四舍五入取整
返回值:四舍五入后的整数

3.ceil()
语法: Math.ceil(数字)
作用︰对数字进行向上取整
返回值∶向上取整后的整数
4. floor()
语法: Math.floor(数字)
作用︰对数字进行向下取整
返回值∶向下取整后的整数
5.pow()
语法: Math.pow(底数，指数)
作用︰对数字进行取幂运算
返回值︰取幂后的结果

6.sqrt()
语法: Math.sqrt(数字)
作用:对数字进行二次方根运算
返回值:二次方根后的结果

7.abs()
语法: Math.abs(数字)
作用︰对数字进行绝对值运算
返回值︰绝对值运算后的结果

8.max()
语法: Math.max(数字1，数字2，数字3，... )
作用:获取若干数字的最大值
返回值︰若干个数字中的最大值

9.min()
语法: Math.min(数字1，数字2，数字3，... )
作用:获取若干数字的最小值
返回值︰若干个数字中的最小值

10.PI
语法: Math.PI
作用︰得到一个近似T的值
```

### 时间常用方法

```js
获取当前时间
var time = new Date()
输出一个自设时间
var time = new Date(年,月,日，时，分，秒)

1.时间对象.getFullYear()
获取至时间对象干的年份信息
2．时间对象.getMonth()
获取到时间对象中的月份信息
3．时间对象·getDate()
扶取至时间对象中的曰期信息
4.时间对象·getHours()
获取至到时间对象中的小时信息
5．时间对象.getMinutes()
获取到时间对象中的分钟信息
6．时间对象.getSeconds()
获取到时间对象中的秒钟信息
7.时间对象.getDay()
获取到时间对象中的星期信息
8．时间对象.getTime()
获取到时间对象中的时间戳信息（毫秒）

设置时间信息

1.时间对象.setFullYear()
设置时间对象中的年份信息
2．时间对象.setMonth()
设置时间对象中的月份信息
3．时间对象.setDate()
设置时间对象中的日期信息
4.时间对象.setHours()
设置时间对象中的小时信息
5．时间对象.setMinutes()
设置时间对象中的分钟信息
6．时间对象.setSeconds()
设置时间对象中的秒钟信息
8．时间对象.setTime()
设置时间对象中的时间戳信息
```

### BOM操作

```js
1.获取浏览器窗口尺寸
获取可视窗口宽度: window.innerWidth
获取可视窗口高度: window.innerHeight

2.浏览器的弹出层
提示框:window.alert('提示信息)
询问框: window.confirm('提示信息’)
输入框: window. prompt( '提示信息’)

3.开启和关闭标签页
开启: window.open('地址’)
关闭: window.close()

4、浏览器常见事件
资源加载完毕: window. onload = function (){}
可视尺寸改变: window.onresize = function () {}
滚动条位置改变:window.onscroll = function （{}

5.浏览器的历史记录操作
回退页面: window.history.back()
前进页面: window.history.forward()


6、浏览器卷去的尺寸
卷去的高度∶
document.documentElement.scrollTop
//<!DOCTYPE html>有这个标签时使用1
document.body.scrollTop
可以使用或运算符中和两种写法

卷去的宽度:
document.documentElement.scrollLeft
//<!DOCTYPE html>有这个标签时使用1
document.body.scrollLeft

7、浏览器滚动到
滚动到: window.scrollTo()
参数方式1 : window.scrollTo( left, top )
left :浏览器卷去的宽度
top :浏览器卷去的高度
滚动到: window.scrollTo()
参数方式1 : window.scrollTo(
left, top )
参数方式2 : window.scrollTo(
{
left: XX,
top: yy,
behavior: 'smooth'})
```