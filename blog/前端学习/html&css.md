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

### CSS内部样式

```html
在head标签内书写
<style>
修饰对象（如h1）:{
    属性(如color)="red";
                }
</style>
```

### CSS外部

在外部创建单独css文件eg:index.css
后在head里引入

```html
1.<style>
  @import url(index.css);//引入文件名
</style>

2.<link rel="stylesheet" type="text/css" href="index.css">//兼容性较好
```

### 扩展知识点：link和import之间的区别？

差别1：本质的差别：link属于XHTML标签，而@import完全是CSS提供的一种方式。

差别2：加载顺序的差别：当一个页面被加载的时候（就是被浏览者浏览的时候），link引用的CSS会同时被加载，而@import引用的CSS会等到页面全部被下载完再被加载。所以有时候浏览@import加载CSS的页面时开始会没有样式（就是闪烁），网速慢的时候还挺明显。

差别3：兼容性的差别：@import是CSS2.1提出的，所以老的浏览器不支持，@import只有在IE5以上的才能识别，而link标签无此问题。

### CSS行内

```html
<h1 style="color:red;">标题</h1>
```

**优先级就近原则：!important>行内>内部>外部**

eg: color:red!important;

### 类选择器

```html
<style>
    .aa {
        color: blue;
        background-color: lightpink;
    }

    .bim {
        background-color: aquamarine;
    }

</style>

<div>aaaaa-11111</div>
<div class="bim aa">aaaaa-22222</div>
<div class="bim">aaaaa-33333</div>
<div class="bim">aaaaa-44444</div>
<div>aaaaa-55555</div>
```

类选择器也遵循就近原则:当有标签冲突时，优先选择离下面最近的标签，上面案例选择.bim

### id选择器

一个div唯一一个id，否则会造成信息丢失

```html
<style>
    #box1:{
        color: red;    
    }
</style>

<div id="box1">11111111</div>
```

### 通配符选择器

语法:*{属性:属性值;}

说明:通配选择符的写法是“*”，其含义就是所有元素。

```html
*{
margin:O; 
padding:0;
}代表清除所有元素的默认边距值和填充值;，几乎只用此功能
```

### 群组选择器

语法:选择符1，选择符2，选择符3....属性:属性值;}例:

```html
 #top1,#nav1，h1{
 width:960px;
 }
 ```

 说明:当有多个选择符应用相同的声明时，可以将选择符用“，”分隔的方式，合并为一组。margin:0 auto;实现盒子的水平居中

 ### 包含选择器/后代选择器

 语法:选择符1 选择符2{属性:属性值}//此处用空格代替","

说明:含义就是选择符1中包含的所有选择符2;

用法:当我的元素存在父级元素的时候，我要改变自己本身的样式，可以不另加选择符，直接用包含选择器的方式解决。如:结构: 

```html
<ul class="list">
    <li></li>
    <li></li>
    <li></li>
</ul>
样式:.list li{background:red;}
```

### 伪类选择器

**语法︰**

a:link{属性:属性值;}超链接的初始状态;

a:visited{属性:属性值;}超链接被访问后的状态;

a:hover{属性:属性值;}鼠标悬停，即鼠标划过超链接时的状态;

a:active{属性:属性值;}超链接被激活时的状态，即鼠标按下时超链接的状态;Link--visited--hover--active。

A)当这4个超链接伪类选择符联合使用时，应注意他们的顺序，正常顺序为: a:link,a:visited,a:hover,
a:active,错误的顺序有时会使超链接的样式失效;

B)为了简化代码，可以把伪类选择符中相同的声明提出来放在a选择符中;例如: a(colorred;) athover(color.
green;}表示超链接的初始和访问过后的状态一样，鼠标划过的状态和点击时的状态一样。

```html
<style>
  a:link{
      color: aqua;
  }/*初始*/
  a:visited{
      color: blue;
  }/*访问后*/
  a:hover{
      color: brown;
  }/*悬停*/
  a:active{
      color: cadetblue;
  }/*激活*/
</style>
```

### 选择器的权重

|个数  | 选择器 |权重，cSs中用四位数字表示权重，权重的表达方式如:0，0，0,|
|---   |----   |----                                                |
|2|Class选择器(类选择器)|0001|
|3| id选择器 |0010|
|4|4包含选择符|为包含选择符的权重之和|
|5|内联样式|1000|
|6|6 !important|10000|

csS选择器解析规则1:相同权重的选择符，样式遵循就近原则:哪个选择符最后定义，就采用哪个选择符样式。

csS选择器解析规则2:相同权重的选择符，样式遵循就近原则:哪个选择符最后定义，就采用哪个选择符样式。

所以元素选择器权重最低

包含选择符：即嵌套中权重较大

###  文本属性

|   |属性 |功能|说明|
|---|---- |---|---|
|1|font-size |字体大小|单位是px，浏览器默认是16px,设计图常用字号是12px|
|2|font-family |字体|当字体是中文字体、英文字体中有空格时，需加双引号；多个字体中间用逗号链接,先解析第1个字体,如果没有解析第2个字体,以此类推|
|3|color |颜色|color:red;  color:#ff0;  color:rgb(255,0,0);  0-255|
|4|font-weight |加粗|加粗font-weight:bolder(更粗的)/bold（加粗）/normal（常规），400正常font-weight:100-900; 100-500不加粗   600-900加粗|
|5|font-style |倾斜|font-style：italic(斜体字)/oblique(倾斜的文字)/normal（常规显示）;|
|6|text-align |文本水平对齐|text-align:left;   水平靠左text-align：right；   水平靠右text-align：center；   水平居中text-align:justify;水平2端对齐，但是只对多行起作用。|
|7|line-height |行高|line-height的数据=height的数据，可以实现单行文本垂直居中|
|8|text-indent |首行缩进|text-indent可以取负值；    text-indent属性只对第一行起作用|
|9|letter-spacing|字间距 |控制文字和文字之间的间距|
|10|text-decoration |文本修饰|text-decoration:none没有/underline下划线/overline上划线/line-through删除线，若要同时使用则要用空格隔开  text-decoration : underline overline line-through；|
|11|font |文字简写|font是font-style font-weight font-size / line-height font-family 的简写。    font:italic  800 30px/80px "宋体"；   顺序不能改变 ,必须同时指定font-size和font-family属性时才起作用|
|12|text-transform |字母大小写|            /*text-transform: capitalize;首字母大写*/           /* text-transform: lowercase;全部小写*/           /* text-transform: uppercase;全部大写*/|

#### 字体粗细

```html
<!--
100  :细体;lighter

400  :正常;normal

700  :粗体;bold

900  :更粗体（主要起强调）;bolder

-->
```

### 列表属性

||属性|描述|说明|
|---|---- |---|---|
|1|list-style-type |定义列表符合样式 |list-style-type:disc(实心圆)/circle(空心圆)/square(实心方块)/none(去掉符号) |
|2|list-style-image |将图片设置为列表符合样式 |list-style-image:url(); |
|3|list-style-position |设置列表项标记的放置位置 |list-style-position：outside；列表的外面 默认值list-style-position：inside；列表的里面 |
|4|list-style |简写(合并写法) |list-style:none; 去除列表符号 |

### 背景属性

||属性|描述|说明|
|---|---- |---|---|
|1|background-color |背景颜色 |background-color：red； | 
|2|background-image |背景图片 |background-image:url(); | 
|3|background-repeat |背景图片的平铺 |background-repeat:no-repeat不平铺/repeat默认平铺/repeat-x  水平平铺/repeat-y 竖直平铺； | 
|4|background-position |背景图片的定位 |background-position：水平位置    垂直位置；可以给负值 | 
|5|background-attachment |背景图片的固定 |background-attachment : scroll (滚动)/ fixed（固定，固定在浏览器窗口里面，固定之后就相对于浏览器窗口了） ; | 
|6|background-size |背景大小 |见代码 | 

```html
background-position: center -20px;//背景图片的定位
/*
1.20px 20px
2.10% 10%
3.left center right
top center bottom
*/

background-size: contain;/*设置背景大小*/
/*
1.400px 400px
2.100% 100%
3.cover:把背景图像扩展至足够哒，以使背景图像完全覆盖背景区域。
也许无法显示在背景定位区域中
4.contain:把图像扩展至最大尺寸，以使其宽度和高度完全适应内容区域。若铺不满、
则留白
*/
```

### 背景复合属性

```html
/*
 1.用空格隔开
 2.顺序可换
 3.可以只取一个值，放在后面能覆盖前面的值
 background-size属性只能单独使用
*/
/*复合写法*/
.box6{
    width: 600px;
    height: 600px;
    background: url("img/0.jpg") no-repeat center fixed yellow;
}
```

### 浮动属性

||属性|描述|说明|
|---|---- |---|---|
|1|float |float：left； |元素靠左边浮动 |
|2|float |float：right； |元素靠右边浮动 |
|3|float |float：none； |元素不浮动 |

|浮动的作用1： |定义网页中其它文本如何环绕该元素显示 |
|--|---|
|浮动的作用2： |就是让竖着的东西横着来 |

 1、浮动会脱离网页文档，与其他不浮动的元素发生重叠
      
 2、但是不会与文字发生重叠，文字会环绕浮动元素显示

||属性|描述|说明|
|---|---- |---|---|
|1|clear |Clear：none； |允许有浮动对象 | 
|2|clear |Clear：right； |不允许右边有浮动对象 | 
|3|clear |Clear：left； |不允许左边有浮动对象 | 
|4|clear |Clear:both; |不允许有浮动对象 | 

清除浮动只是改变元素的排列方式，该元素还是漂浮着，不占据文档位置。

### 盒子的边距设计

```html
    padding: 40px 10px 30px 20px;
    /*
    内边距
    1. 1个值，上下左右边距一样
    2. 2个值，上下，左右
    3. 3个值，上 左右 下
    4. 4个值， 上 右 下 左
    */
}
padding属性
/*
1.背景色蔓延到内边距
2.设置单一方向：padding-方向：top bottom left right
*/
padding-top: 10px;
```

### 内边距边框border

```html
复合属性（四条边相同）：border: 10px dotted red;/*边框属性，背景色也能蔓延到边框*/
/*样式：solid实线 double双线 dashed虚线 dotted点状线*/
/*
border包含
border-width
border-style
border-color
*/
/*拆分使用*/可同时改变四个边
border-width: 10px 20px 30px 40px;
border-color: red darkblue darkgoldenrod aquamarine;
border-style: solid dashed double dotted;
```

### 外边距margin

```html
margin: 50px 100px 10px 20px; /*外边距设置，从上开始的顺时针方向记忆*/
/*可以取1-4个值
    1. 1个值，上下左右边距一样
    2. 2个值，上下，左右
    3. 3个值，上 左右 下
    4. 4个值， 上 右 下 左*/
    
    margin-left: -200px; /*单一方向设置，支持负值*/
    margin: 0 auto;屏幕居中，横向居中
```

**特性问题**

1.兄弟关系，两个盒子垂直外边距与水平外边距问题

（1）垂直方向取最大值

（2）水平方向相加

**2.父子关系，给子加外边距，但作用于父身上了，怎么解决？**

```html
/*padding-top: 100px;/*方法1.改变父盒子内边距，但因内边距包含盒子，此时父盒子由原来的长500->600，应再将height减为400*/
/*border: 1px solid transparent;方法2.给父盒子设置边框，减去边框的高度,transparent透明*/
/* margin-top: 100px;*/
/*float: left;方法3.给子盒子或父盒子加float*/
overflow: hidden;/*方法4.bfc*/
```

### PS工具使用

```html
ps====图片处理软件(美工来做图, 前端来测量 吸取颜色 切图)

   拿到设计稿之后：使用ps打开
      1、图片上面右键-=====打开方式ps
      2、ps里 文件=>打开
   图片放大和缩小
      ctrl++
      ctrl+-
      alt+滚动
   图片的移动
      按住空格,鼠标变为小手,拖动图片

   如何调整出来标尺
      ctrl+r
      作用：拖动参考线方便测量
      视图里面找到标尺，把对勾勾选上    
   测量图片大小
      使用矩形选框工具（左侧竖着第二个）
      如何查看数据大小（窗口-----信息面板====wh）
      如何修改测量单位：
         在标尺上面右键取修改单位====像素
      ctrl+d===取消选区

      选完后,想调整大小, 可以右键->变换选区

   吸取颜色
      使用吸管工具  I
      吸取颜色完成后，点击左下角的背景色，会右弹窗，在弹窗里面右#十六进制的颜色值可以让你复制

   截图
      1、使用快捷键截图===每次只能截取一个
         使用选框工具框选尼亚截取的区域
            ctrl+c=======ctrl+n=======回车=======ctrl+v=======ctrl+s
                        回车======回车
      2、切片工具 (裁剪工具进行切换)
         使用切片工具框选你要留住的区域，点击文件，存储为web所用格式，弹窗里面点击存储，
         弹窗======格式:仅限图像，切片:所有用户切片
```

#### 解决文字段落与图片空隙
```html
img {
    display: block; /*将img转化为block以匹配p标签的格式，消除图片与文字之间空隙*/
}
```

### 溢出属性（容器的)

```html
overflow:visible/hidden(隐藏)/scroll/auto(自动)/inherit;
visible:默认值，溢出内容会显示在元素之外;
hidden:溢出内容隐藏;
scroll:滚动，溢出内容以滚动方式显示;
auto:如果有溢出会添加滚动条，没有溢出正常显示;
inherit:规定应该遵从父元素继承overflow属性的值。
overflow-x:X轴溢出;
overflow-y:Y轴溢出
```

### 空余空间

```html
white-space: normal/nowrap/pre 预留格式/pre-wrap /pre-line /inherit 该属性用来设置如何处理元素内的空白;
normal:默认值，空白会被浏览器忽略，
nowrap:文本不会换行，文本会在同一行上继续，直到遇到<br/>标签为止;
pre：显示空格 回车，不换行
pre-wrap：显示空格 回车，换行
pre-line：不显示空格 ，显示回车，换行
<pre></pre>                该标签可预留回车空格等格式
```

### 省略号显示

```html
text-overflow:clip/ellipsis ;
clip:默认值，不显示省略号(.…..) ;
ellipsis:显示省略标记;
当单行文本溢出显示省略号需要同时设置以下声明:
1、容器宽度:width: 200px;
2、强制文本在一行内显示:white-space: nowrap;
3、溢出内容为隐藏:overflow: hidden;
4、溢出文本显示省略号:text-overflow: ellipsis;
```

### 定位

| |书写语法 |说明 |文档流 |偏移位置（top  left  right  bottom）时候的参照物 |层叠顺序（z-index）|
|---|---|---|----|---|----|
|1|position：static； |默认值 |默认 |默认 | |
|2|position：absolute； |绝对定位 |脱离 |A）当没有父元素或者父元素没有定位，参照物是浏览器窗口的第一屏   B）有父元素且父元素有定位，父元素 |z-index属性是不带单位的，并且可以给负值，没有设置z-index时，最后写的对象优先显示在上层，设置后，数值越大，层越靠上； |
|3|position：relative； |相对定位 |不脱离 |自己的初始位置 |同上 |
|4|position：fixed |固定定位 |脱离 |浏览器的当前窗口 |同上 |
|5|position: sticky; |粘性定位 |可以做吸顶效果，粘性定位是css3.0新增加的，兼容不好 | | |

**让盒子处于中心位置的方法**

```html
left: 50%;
/* 左移原来一半 */
margin-left: -30px;
/* 设置为盒子的宽度一半 */
```

#### 层级

```html
z-index: -1;/*层级，谁的数值大谁在前*/

有父子盒子时，给子盒子设置负层级可让它在下面
```

### 让行内元素显示为块元素的一些方法

1.display: block;

3.float: left;

2.absolute

### 绘制一个三角形

```html
div{
  width: 0;
  height: 0;
  /*画出三角形写法1
  border-left: 20px solid red;
  border-top: 20px solid rgba(0,0,0,0);/*透明
  border-right: 20px solid rgba(0,0,0,0);
  border-bottom: 20px solid rgba(0,0,0,0);
  */
  写法2
  border: 20px solid transparent;
  border-top: 20px solid red;
}
```

### 定位与浮动区别

```html
float: left;文字环绕效果，半脱离
position: absolute;/*不环绕，被覆盖，全脱离*/
```