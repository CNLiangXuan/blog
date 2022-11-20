# Node.js学习笔记

## node基础模块化

```js
引入其他的模块

在node中，通过require()函数来引入外部的模块
require()可以传递一个文件的路径作为参数，node将会自动根据该路径来引入外部模块这里路径，如果使用相对路径，必须以.或..开头,为模块标识

模块化

-在Node中，一个js文件就是一个模块
-在Node中，每一个js文件中的js代码都是独立运行在一个函数中
而不是全局作用域，所以一个模块的中的变量和函数在其他模块中无法访问

模块分成两大类
  核心模块
    -由node引擎提供的模块
    -核心模块的标识就是，模块的名字

  文件模块
    -由用户自己创建的模块
    -文件模块的标识就是文件的路径（绝对路径，相对路径)
        相对路径使用.或..开头

在node中有一个全局对象global，它的作用和网页中window类
在全局中创建的变量都会作为global的属性保存
在全局中创建的函数都会作为global的方法保存

当node在执行模块中的代码时，它会首先在代码的最顶部，添加如下代码
function (exports,require, module,_filename,_ dirname) {
在代码的最底部，添加如下代码
}

```

## exports和module.exports

### 变量存储在堆栈中的关系

![](img/06.png)

new一个对象相当于在堆内存中开辟一个存储空间，在栈内存中存储的是堆内存的地址，obj2 = obj相当于他们指向同一堆内存地址，所以改变obj2的值，obj的值也会变。 若obj2 = null则obj的值不变，此时相当于更改变量。

-通过exports只能使用.的方式来向外暴露内部变量

**exports.XXX=XXXX**

-而module.exports既可以通过.的形式,也可以直接赋值

**module.exports.XXX=XXXX**

**module.exports = {}**


```js
// 可被调用
module.exports  = {
    name : "孙悟空",
    age : 18,
    sayName : function () {
        console.log('我是孙悟空')
    }
}

// 不可被调用
exports  = {
    name : "孙悟空",
    age : 18,
    sayName : function () {
        console.log('我是孙悟空')
    }
}
```

## 包简介

CommonJS的包规范由包结构和包描述文件两个部分组成。

```
包结构
包实际上就是一个压缩文件，解压以后还原为目录。符合规范的目录，应该包含如下文件∶
- package.json   描述文件
- bin---可执行二进制文件
- lib ---js代码
- doc---文档
- test---单元测试


包描述文件
-描述包的相关信息，以供外部读取分析
```

