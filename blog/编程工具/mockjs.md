# MockJs

## mock

### 安装

在安装node.js的基础上，在终端中输入npm install mockjs

导入:var Mock =require ( 'mockjs ')

使用:var data = Mock.mock ( {....} )

//data为虚拟的数据

### Mock.js的语法规范

Mock.js的语法规范包括两部分:

#### 1.数据模板定义规范(Data Template Definition，DTD)

数据模板中的每个属性由3部分构成:属性名(name)、生成规则(rule)、属性值(value):

```'name|rule':value```

**属性值是字符串 String**

```
1. 'namelmin-max': string

通过重复string生成一个字符串,重复次数大于等于min,小于等于max。

2.'name|count: string

通过重复string 生成一个字符串,重复次数等于count。
```

**属性值是数字Number**

1.'name/min-max': number

生成一个大于等于min、小于等于max的整数，属性值number只是用来确定类型。

#### 2.数据占位符定义规范（Data Placeholder Definition，DPD)

占位符只是在属性值字符串中占个位置，并不出现在最终的属性值中

```
@占位符
@占位符(参数[,参数])
```

```
@id():得到随机的id
@cname():随机生成中文名字
@date('yyyy-MM-dd'):随机生成日期
@paragraph():描述
@email():邮箱地址
```

jQuery与mock运用模板

```js
if (MOCK === 'true'){
    var data = Mock.mock('/user/userInfo', 'get', {
        id: "@id()", //得到随机的id
        username: "@cname()", //随机生成中文名字
        date: "@date()", //随机生成日期
        avator: "@image('200x200','#50B347','#fff','avatar')", //生成图片，参数：size,background,foreground,text
        description: "@paragraph()", //描述
        ip: "@ip()", //IP地址
        email: "@email()" //email
    })
    console.log(data)
}
```
```html
<!DOCTYPE html>
<html lang="">
<head>
    <meta charset="utf-8">
    <title></title>
    <script src="https://cdn.bootcss.com/jquery/2.2.4/jquery.min.js"></script>
    <script src="https://cdn.bootcss.com/Mock.js/1.0.0/mock-min.js"></script>
</head>

<body>
<script> MOCK = 'true'</script>
<script src="mock/index.js"></script>
<script>
    $.ajax({
        url: '/user/userInfo',
        dataType:'json',
        success: (data) =>{
            console.log(data)
        }
    })
</script>

</body>
</html>
```


1.定义接口路由，在接口中并返回mock模拟的数据

2.在vue.config.js中配置devServer，在before属性中引入接口路由函数

3.使用axios调用该接口，获取数据