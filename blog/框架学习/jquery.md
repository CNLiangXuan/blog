## jQuery

### jQuery选择器

```js
<!-- 注意：不管使用任何选择器，获取到的元素都是一个元素的集合 -->
//  id选择器
console.log($('#box'))
//  类名选择器
console.log($('.a'))
//  标签名选择器
console.log($('li'))
//  结构选择器
console.log($('li:nth-child(odd)'))
```

#### jQuery筛选器

语法: $(‘选择器’).筛选器名称()

```js
    console.log($('li').last())
    console.log($('li').first())

    //eq(索引)
    //注意：索引从0开始，一次+1
    console.log($('li').eq(3))
    //4.next()
    console.log($('span').next())
    //5.nextAll()
    console.log($('span').nextAll())
    //6.prev()
    console.log($('span').prev())
    // 7.prevAll()前面所有
    console.log($('span').prevAll())

    //8.parent()获取父元素
    console.log($('span').parent()) 

    //9.parents()逐层获取所有父元素结构，知道获取到html
    console.log($('span').parents())

    //10.拿到该元素的所有兄弟元素
    console.log($('li').siblings())

//    11.find()在所有后代元素中查找该元素
    console.log($('ul').find('i'))
```
### 操作文本内容

```js
  1.html()
  等价于我们原生js中的innerHTM
  1-1.html()获取，读取标签
  console.log($('div').html())

  1-2. html()设置
  语法:元素集合.html(你要设置的内容)
 可以识别并解析html字符串,可创建标签
$('div').html('<h2>我是后来设置的内容</h2>')

  2.text()
  等价于我们原生JS中的innerText
  2-1.text()获取，不会读到标签
console.log($('div').text())

  2-2.text()设置
  语法:元素集合.text(你要设置的内容)
  注意:不可以识别并解析html结构字符串，不可创建标签
  console.log($('div').text('<h2>我是后来设置的内容</h2>'))

  3.val()
  等价于我们原生JS 中value
  3-1.val()获取
  console.log($('input').val())

  3-2.val()设置
  语法:元素集合。val(你要设置的内容)
  作用:用来设置该表单元素的 value 值
  console.log($('input').val('你好世界'))
```

### 操作元素类名

```js
1. addclass()
  语法:元素集合.addclass(需要添加的类名)
$('div').addClass('e')

2.removeclass()
语法:元素集合.removeclass(你要删除的类名)
$('div').removeClass('b')

3.toggleclass()
语法:元素集合.toggleclass(你要切换的类名)
切换:如果本身有这个类名，那么就是删除，如果本身没有这个类名，那么就是添加
const btn = document.querySelector('button')
btn.onclick = function (){
  $('div').toggleClass('box')
}
```

### 操作元素样式方法

``` js
// 1.css获取样式
// 注意:可以获取到元素的行内样式，也可以获取到元素的非行内样式
// 语法:元素集合.css(你要获取的样式名称)
// 返回值:该样式的样式值
console.log($('div').css('width'))
console.log($('div').css('height'))
console.log($('div').css('background-color'))

// 2.css设置样式
// 语法:元素集合.css(样式名，样式值)
// 注意:当你需要给一个元素设置样式值为px单位的时候，可以省略单位不写
console.log($('div').css('width',300))
console.log($('div').css('background-color','green'))

// 3。css批量设置样式
// 语法:元素集合.css({你所有需要设置的样式})
$('div').css({
    width:260,
    height:320,
    opacity:0.68,
    'background-color':'pink'
})
```

### 操作元素属性

```js
// 1。attr()
// =>可以进行设置和获取元素的属性
// =>注意:一般用于操作元素的自定义属性
// =>注意:attr操作的所有属性都会直接出现在元素的标签身上
// =>获取:
//  ->语法:元素.attr(你要获取的属性名)
//  ->返回值:该属性名对应的属性值
// 2.removeAttr()
// =>对元素的属性进行删除操作
//         =>语法:元素集合.removeAttr(你要删除的属性名)

//1-1.attr() 获取
// console.log($('div').attr('hello'))
// console.log($('div').attr('id'))

//1-2.attr() 设置
// $('div').attr('a',100)
// $('div').attr('id','container')

/*
    1.prop()
    +可以获取和设置元素的属性+注意:
    =>当prop设置元素的原生属性，会直接响应在元素标签身上
    =>当prop设置元素自定义属性，不会直接响应在元素标签身上,会响应在元素对象身上
    +注意:prop方法不能获取元素标签身上的自定义属性，只能获取prop方法自己设置的自定义属性
    +prop(）设置
    =>语法:元素集合.prop(属性名，属性值)
    +prop(）获取
    =>语法:元素集合.prop(你要获取的属性名)
    =>返回值:该属性对应的值

    2.removeProp()
    +用来删除元素属性的方法+注意:
    =>不能删除原生属性
    =>只能删除由prop方法设置的自定义属性
    +语法:元素集合。removeProp(你要删除的属性名)


    */
let div_prop = $('div')
//1-1 prop(）设置
div_prop.prop('id','container')
div_prop.prop('a',100)
console.log(div_prop.prop('id'))
console.log(div_prop.prop('hello'))
console.log(div_prop.prop('a'))

div_prop.removeProp('id')
//不能删除原生属性
div_prop.removeProp('a')
//删除自定义属性
console.log(div_prop.prop('a'))

```

### 获取元素的尺寸

```js
/*注意：
  * 1.不管该元素是否隐藏，都能获取到该元素的值
  * 2.不管盒子模型是什么状态，拿到的尺寸区域不变

  * */
  //1.width()和height()
  //获取到的就是元素内容区域的尺寸
  $('div').width()
  $('div').height()

  //2.innerHeight()和innerWidth()，获取到边框内的内容
  console.log($('div').innerHeight())
  console.log($('div').innerWidth())

 // 3.outerWidth()和outerHeight()，获取到包括边框的尺寸
 console.log($('div').outerWidth())
 console.log($('div').outerHeight())

//4.outerWidth(true)和outerHeight(true)拿到的包含你设置的margin尺寸值
  console.log($('div').outerWidth(true))
  console.log($('div').outerHeight(true))

```

### 获取元素偏移量

```js
    /*  1.offset()
      获取元素相对于页面左上角的坐标位置
      注意:返回值是一个对象数据类型，{ top: yyy, left: xxx }*/

    console.log('div: ',$('div').offset())
    console.log('p: ',$('p').offset())
    console.log('span: ',$('span').offset())

    // 2.position()
    //获取元素定位
    //注意:如果你设置的是 right和 bottom，会自动帮你换算成left和top 的值给到你
    console.log($('span').position())
```

### 事件绑定

```js
/*   
 1.on()方法绑定事件
    1-1。基础绑定事件
    语法:元素集合.on('事件类型'，事件处理函数)

    1-2。事件委托绑定事件
    语法:元素集合.on('事件类型'，选择器，事件处理函数)
    把事件绑定给div元素，当你在div 内的p元素触发事件的时候,执行事件处理函数
    事件委托，把p元素的事件委托给了div 元素来绑定
    1-3。批量绑定事件
    语法:元素集合.on({ 事件类型1:处理函数，事件类型2:处理函数})
    注意:不能进行事件委托了
    */
$('div').on('click', function () { console.log('我是div的点击事件') })
$('div').on('click','p', function () {console.log('我是委托形式的事件')})

$('div').on({
    click: function () {
        console.log('点击事件')
    },
    mouseover: function () {
        console.log('鼠标移入事件')
    },
    mouseout: function () {
        console.log('鼠标移出事件')
    }
    }
)

// 2. one()
// 用来绑定事件，和on方法绑定事件的方式是一样的
// 区别:one方法绑定的事件，只能执行一次
// 1-2。事件委托绑定事件
// 语法:元素集合.on('事件类型'，选择器，事件处理函数)
// 1-3。批量绑定事件
// 语法:元素集合.on({ 事件类型1:处理函数，事件类型2:处理函数})
// $('div').one('click', 'p', function () { console.log('事件委托') })
// $('div').one('click', function (){console.log('基础绑定')})

$('div').one({
    click: function () {
        console.log('点击事件')
    },
    mouseover: function () {
        console.log('鼠标移入事件')
    },
    mouseout: function () {
        console.log('鼠标移出事件')
    }
})

// 3. hover()
// 注意:jQuery里面一个特殊的事件
// 语法:元素集合.hover(移入时触发的函数，移出时触发的函数)
// 当你只传递一个函数的时候，会在移入移出都发,也不能做事件委托

$('div').hover(
    function () { console.log('函数1') },
    function () { console.log('函数2') }
)

// 4。常用事件函数
// jQuery把我们最长用到的一些事件，单独做成了事件函数我们通过调用这些事件函数，来达到绑定事件的效果
// click()， mouseover(), mouseout(),change(),
$('div').click(function (){ console.log('点击事件') })
```

### 事件解绑和触发

```js
//准备事件处理函数
function handlerA() { console.log('我是handlerA事件处理函数') }
function handlerB() { console.log('我是handlerB事件处理函数') }
function handlerC() { console.log('我是handlerC事件处理函数') }

//  给div元素绑定事件
  $('div')
  .click(handlerA)
  .click(handlerB)
  .click(handlerC)

  // 1。off()事件解绑Ⅰ
  // 1-1。解绑全部事件处理函数
  // 语法:元素集合.off(事件类型)
  // 会把div 的click事件对应的所有事件处理函数全部移除
  // 1-2。解绑指定的事件处理函数
  // 语法:元素集合.off(事件类型，要解绑的事件处理函数)
  // 会把div 的click事件对应的 handlerB事件处理函数移除
   $('div').off('click',handlerB)

  // 2.trigger()事件触发使用代码的方式,来触发事件
  // 语法:元素集合.trigger(事件类型)就会触发该元素的该事件
setInterval(function () {
//  每1000秒触发一次div的click事件
  $('div').trigger('click')
},1000)
```
### 动画

#### 基本动画

```js
/*
  基本动画
  1。show()显示
  2.hide(）隐藏
  3.toggle()切换
          =>本身如果是显示的,就隐藏
          =>本身如果是隐藏的，就显示
  +对于以上三个运动函数,有共同的参数
          =>第一个表示运动时间
          =>第二个表示运动曲线
          =>第三个表示运动结束的回调函数
*/

  $('div').show(1000,'linear', function () {console.log('show结束了') })
  $('div').hide(1000,'linear', function () {console.log('hide结束了') })
  $('div').toggle(1000,'linear', function () {console.log('toggle结束了') })

```

#### 折叠动画

```js
    /*
      1。slideDown()显示
      2。slideUp(）隐藏
      3.slideToggle()切换
          =>本身如果是显示的,就隐藏
          =>本身如果是隐藏的，就显示
      +对于以上三个运动函数,有共同的参数
          =>第一个表示运动时间
          =>第二个表示运动曲线
          =>第三个表示运动结束的回调函数
    */
$('div').slideDown(1000,'linear', function () {console.log('show结束了') })

```

#### 渐隐渐显动画

```
1.fadeIn()显示
2.fadeOut(）隐藏
3.fadeToggle()切换
4.fadeTo(运动时间，指定的透明度，运动曲线，运动结束的回调函数)
$('div').fadeTo(1000,0.5,'linear', function () {console.log('运动到了指定透明度')})})

```

#### 综合动画

```js
/*  综合动画
  +animate()
  =>第一个参数:要运动的样式，以一个对象数据类型传递
  =>第二个参数:运动时间
  =>第三个参数:运动曲线
  =>第四个参数:运动结束的回调函数
  +注意;
=>关于颜色相关的样式是不能运动的
=>关于transform相关的样式是不能运动的

*/
$('div').animate({
    width:500,
    height:600,
    'border-radius':'50%'
  },1000,'linear',function (){console.log('运动结束了')})
```

#### 结束动画

```js
 结束动画
  +需要用到运动结束的函数
  1.stop()
  =>当任何一个元素，执行了stop方法以后
  =>会立即结束当前的所有运动，目前运动到什么位置，就停留在什么位置
  2. finish( )
  =>放任何一个元素，执行了finish 方法以后
  =>会立即结束当前的所有运动，直接去到动画的结束位置
 $('div').stop().toggle(2000)
$('div').stop()
$('div').finish()
```

### jQuery的ajax请求

```js
jQuery 的ajax请求
+注意;
  =>因为发送ajax请求，不是操作 DOM
  =>不需要依赖选择器去获取到元素
  => 他的使用，是直接依赖jQuery或者$变量来使用
  ->语法:$.ajax({ 本次发送ajax的配置项})
    +配置项:
  1.url:必填,表示请求地址
  2.method:选填，默认是 GET，表示请求方式
  3. data:选填，默认是''，表示携带给后端的参数
  4.async:选填，默认是true，表示是否异步
  5.success:选填,表示请求成功的回调函数
  6.error:选填,表示请求失败的回调函数

  $.ajax({
  url: '1.txt',
  success: function (res){
  //  res 接受的就是后端相应的结果
    console.log(res)
  }
})
```

