# html&css 笔记

## 标签

### 1、文本标题（h1-h6）

```html
<h1>一级标题</h1>
```

> 注:文本标题标签自带加粗，有自己的文本大小，并且独占一行，有默认间距

### 2、段落文本(p)

```html
<p>段落文本内容</p>
```

标识一个段落(段落与段落之间有段间距)

### 3、换行(br)

```html
<br / >
```

换行是一个空标记(强制换行)

### 4、水平线

```html
<hr />空标记
```

### 5、加粗有两个标记(推荐strong)

```html
<b>加粗内容</b>只是显示加粗
<strong>强调的内容</strong>突出的文本
```

### 6、倾斜有两个标记(推荐em)

```html
<em>强调文本</em>
<i>倾斜文本</i>
```

### 7、删除线有两个标记(推荐del)

```html
<s>文本</s>删除线
<del>文本</del>删除线
```

### 8、扩展

```html
<u>文本</u>下划线
<sub> </sub>下标
<sup></sup>上标
```

### 9、`<常规标记>`也叫双标记

```html
<标记></标记>
<标记属性=“属性值”属性=“属性值”></标记>
```

标记也可叫标签或叫元素

例如: `<head> </head>`

### 10、空标记也叫单标记`<标记/>`

`<标记属性=“属性值”/>`，例如:`<br />`

### 11、hr标签

```html
<hr color= " red" width="300px"  align="right">
color=====颜色
width=====宽度
align=====对其方式 (默认为居中，这里可填left或right)
noshade===取消阴影
```

### 11、特殊符号

<>： `&lt;`左尖角号`&gt;`右尖角号

空格：

`&nbsp;`该空格占据宽度受字体影响明显而强烈

`&emsp;`占据的宽度正好是1个中文宽度,且基本上不受字体影响(一半使用这个)

版权：

`&copy;`©

商标:

`&trade; `™

`&reg;` ®

表情:

`&#128512`

### 12、div标签

没有具体含义，用来划分页面的区域，独占一行。

### 13、span标签

没有实际意义，主要应用在对于文本独立修饰的时候，内容有多宽就占用多宽的空间距离。
### 14、列表

**有序列表**

```html
<ol>
<li> abc </li>                    //ol中间只能放li,数字是自动生成的，但li中可放置任意标签
</ol>                    
ol的属性：type = 1   a  A   i  I               //可更换排序方法，i,I分别为大小写罗马数字
         start = 数字                        //可指定从哪个数字或字母开始排序
<ol type = "1" start = "3">                   //按照3.4.5.。。。。排序
```

**无序列表**

```html
<!--
1.ol中间只能放li,数字是自动生成的，但li中可放置任意标签
2.默认是实心圆点
3.type = disc,circle,square,none(用的最多)
-->
<ul>
<li>  abc </li>
</ul>
```

**自定义列表**

```html
<dl>
  
<dt>
 可以是文字也可以图
</dt>
   
<dd>
相关文字
</dd>

</dl>
```

### 15、图片

```html
<!--
    1.code.gif
    2. ./code.gif      //1.2均表示从当前目录下的图片
    3. ./img/1.png     //img文件夹与html文件同级
    4. ../code.gif     //返回上一级文件夹再寻找图片 ..同linux为上一级的意思
-->
<img src="code.gif">
<img src="./code.gif">
<img src="./img/1.png">
<img src="../img/1.png">
图片的标签属性
<img  src="图片路径"  
 title="鼠标悬停上去之后的提示信息"
 alt="图片不显示之后（加载失败）的提示信息"
 width=“200px”           //px为分辨率
 height=“200px”/>
 ```

 **路径分类：绝对路径、相对路径**

 1、绝对路径

绝对路径是指文件在硬盘上真正存在的路径。例如“bg.jpg”这个图片是存放在硬盘的“E:\book\网页布局代码\第2章”目录下，那么 “bg.jpg”这个图片的绝对路径就是“E:\book\网页布\代码\第2章\bg.jpg"。

注意：绝对路径在实际的开发过程中很少去使用，如果使用“E:\book\网页布\代码\第2章\bg.jpg”来指定背景图片的位置，在自己的计算机上 浏览可能会一切正常，但是上传到Web服务器上浏览就很有可能不会显示图片了，绝对路径可以使用“\”或“/”字符作为目录的分隔字符

2、相对路径(常用)

相对路径，就是相对于自己的目标文件位置。

1)当当前文件与目标文件在同一目录下，直接书写目标文件的文件名+扩展名；
`<img src="pic4.gif" />`

2)当当前文件与目标文件所处的文件夹在同一目录下，写法如下：
文件夹名/目标文件全称+扩展名；  `<img src="img/pic.png“/>`

3)当当前文件所处的文件夹和目标文件在同一目录下，写法如下：
../目标文件文件名+扩展名；`<img src="../小可爱.png" />`

### 16、超链接标签

```html
<a  href=“路径”  title=“鼠标悬停上去之后的提示信息”  target=“规定在何处打开文档">内容</a>
```

Target属性：规定在何处打开文档。

target=“_self“  默认值

target=“_blank“  新窗口打开

### 表格

```html
<table>
    <tr>
        <td>1</td>
        <td>2</td>
    </tr>
    <tr>
        <td>3</td>
        <td>4</td>
    </tr>
</table>
```

#### table单元格的属性

```html
宽度  width                                //可取像素值或百分比（相对于父元素）
高度  height                               //可取像素值或百分比（相对于父元素）
边框  border
边框颜色  bordercolor
背景颜色   bgcolor   
水平对齐  align=“left或right或center”

cellspacing="单元格与单元格之间的间距“

cellpadding="单元格与内容之间的空隙" 
```

#### tr行属性

```html
属性
高度  height

背景颜色   bgcolor   
文字水平对齐  align=“left或right或center”
文字垂直对齐  valign=“top或middle或bottom"
```

#### 单元格td属性

```html
宽度  width                    //改变一整列
高度  height                    //改变一整行
背景颜色   bgcolor   
文字水平对齐  align=“left或right或center”
文字垂直对齐  valign=“top或middle或bottom";
```

#### 单元格的合并

 ```html
Colspan=“所要合并的单元格的列数” 必须给td。
Rowspan=“所要合并的单元格的行数” 必须给td。
```

### 表单

```html
<form method=“get或者post” action=“向何处发送表单数据”>
<input />
属性   type 定义输入框的类型
文本框  type="text“       
密码框  type=“password“

提交框  type=“ submit“  和 <button>提交按钮</button>  一样
按钮框  type=“button“  单纯的按钮
重置框  type=“reset”清空的效果
属性   placeholder  描述输入字段预期值的简短的提示信息。兼容到IE8以上

属性   name 必须设置，否则在提交表单时，用户在其中输入的数据不会被发送给服务器

属性   value             按钮名称
<form/>
```

#### Form当中method的post和get的区别？

1. get是从服务器上获取数据，post是向服务器传送数据。

2. get是把参数数据队列加到提交表单的ACTION属性所指的URL中，值和表单内各个字段一一对应，在URL中可以看到。post是通过HTTP post机制，将表单内各个字段与其内容放置在HTML HEADER内一起传送到ACTION属性所指的URL地址。用户看不到这个过程。

3. 对于get方式，服务器端用Request.QueryString获取变量的值，对于post方式，服务器端用Request.Form获取提交的数据。

4. get传送的数据量较小，不能大于2KB。post传送的数据量较大，一般被默认为不受限制。但理论上，IIS4
（Internet Information Service 互联网信息服务）中最大量为80KB，IIS5中为100KB

5. get安全性非常低，post安全性较高。但是执行效率却比Post方法好。