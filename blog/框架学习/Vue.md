# Vue2.0

## 引入Vue

## Vue拦截原理

当你把一个普通的 JavaScript 对象传入 Vue 实例作为 data 选项，Vue 将遍历此对象所有的 property，并使用 Object.defineProperty 把这些 property 全部转为 getter/setter。Object.defineProperty 是 ES5 中一个无法 shim 的特性，这也就是 Vue 不支持 IE8 以及更低版本浏览器的原因。

这些 getter/setter 对用户来说是不可见的，但是在内部它们让 Vue 能够追踪依赖，在 property 被访问和修改时通知变更。这里需要注意的是不同浏览器在控制台打印数据对象时对 getter/setter 的格式化并不同，所以建议安装 vue-devtools 来获取对检查数据更加友好的用户界面

![](img/01.png)

### Vue的底层原理

每次数据更改的时候，通过set拦截，通知watcher,watcher收录当前状态再页面中所有用到的地方，对所有相关联的组件代码进行更新，而在更新过程中它们会先创建一份新的虚拟DOM对比老的虚拟DOM节点，在对比过程中找出最小的代价的方法来更新虚拟DOM到真实的DOM中。

## Vue模板语法

```js
var vm = new Vue({
        el: "#box",
        data: {
            myname: "Liangxuan",
            myage: 100
        },
        //方法
        methods: {
            handleChange() {
                console.log("handleChange")
                vm.myname = "teichui"
                vm.myage = 18
            }
        //    不操作DOM的情况下改变页面显示
        }
    })
```

可用this替代全局变量vm,this为该对象实例

## 列表渲染

(1)v-for(特殊v-for="n in 10")

a. in

b. of

没有区别

(2)key:

*跟踪每个节点的身份，从而重用和重新排序现有元素

*理想的key值是每项都有的且唯一的id。data.id

虚拟DOM:js对象描述的节点

真实DOM：真实的li标签等

![](img/02.png)

>当节点更新，即数组中元素发生改变时产生新的虚拟DOM，新的虚拟DOM与原有的虚拟DOM做对比然后更新真实DOM，即每次创建先更新虚拟DOM，产生一个小的补丁，再更新真实DOM，若直接创建一个真实的DOM则会非常浪费时间和资源

(3)数组更新检测

a.使用以下方法操作数组，可以检测变动

push() pop() shift() unshift() splice() sort() reverse()

b. filter(), concat()和slice() ,map(),新数组替换旧数组，只有通过原数组等于新数组的赋值方法才能使原数组的值发生改变

c.不能检测以下变动的数组

vm.items[indexOfltem] = newValue

*解决*(1)Vue.set(example1.items, indexOfltem, newValue)

eg:Vue.set(vm.datalist,0,"xiaohong")

(2)splice

vm.datalist.splice(0,1,"xiaoming")表示删除从第0个元素开始的第一个元素，并添加"xiaoming"

(4)应用:显示过滤结果


# Vue3.0

## 数组的更新检测

vm.items[indexOfltem] = newValue可以直接被拦截

## 解决ajax跨域请求问题

1. 删除发送数据的请求开头网址 

```js
 mounted() {
    axios.get('/ajax/moreComingList?token=&movieIds=1479130,1298151,1308442,1203426,1425908,1218073,1336437,248949,1435030,1364066&optimus_uuid=EA12C040BC0111ED8382EBCFDAF31B6680301CCDFA724824A9253933EF5465A4&optimus_risk_level=71&optimus_code=10').then(res => {
      console.log(res.data)
    }) 
  }
  ```

  2. 在vue.config中,当有/ajax出现时，自动请求https://i.maoyan.com

  ```js
  // 配置反向代理
  devServer: {
    proxy: {
      "/ajax": {
        target: "https://i.maoyan.com",
        changeOrigin: true
      }
    }
  }
  ```

  3. 当都请求同一个开头的请求时，可以在前面加上自定义字符串，通过在vue.config中的pathRewrite重写成"^/kerwin":''，即可变回原网址

  ```js
 mounted() {
    axios.get('kerwin/ajax/moreComingList?token=&movieIds=1479130,1298151,1308442,1203426,1425908,1218073,1336437,248949,1435030,1364066&optimus_uuid=EA12C040BC0111ED8382EBCFDAF31B6680301CCDFA724824A9253933EF5465A4&optimus_risk_level=71&optimus_code=10').then(res => {
      console.log(res.data)
    })
  }
  ```

  ```js
  devServer: {
    proxy: {
      // "/ajax": {
      //   target: "https://i.maoyan.com",
      //   changeOrigin: true
      // }

      "/kerwin":{
        target:"https://i.maoyan.com",
        changeOrigin: true,
        pathRewrite:{
          "^/kerwin":''
        }
      }
    }
  }
  ```

  4. 重启服务器，报错消失，拿到跨域数据

  总结：服务器与服务器之间可以通信，本地的文件也可以与本地服务器通信

  @ 别名===> src的绝对路径

  ## vue router配置映射表

  地址与组件之间一一映射

### 3.路由原理:

(1)hash路由==> location.hash 切换

window.onhashchange监听路径的切换

```js
window.onhashchange=()=>{console.log("1111",location.hash)}
```

(2)history路由==> history.pushState 切换

window.onpopstate监听路径的切换

### rounter具体配置过程

1. 找到router文件夹下的index.js,引入所需要的组件

```js
import Vue from 'vue'
import VueRouter from 'vue-router'
import Films from "@/views/Films";
import Cinemas from "@/views/Cinemas";
import Center from "@/views/Center";
```

在main.js中引入`import router from "@/router";`
2. 注册路由插件

```js
Vue.use(VueRouter)  // 注册路由插件，两个全局 router-view router-link
```

3. 

```js
// 配置表
const routes = [
  {
    path: '/films',
    component: Films
  },
  {
    path: '/cinemas',
    component: Cinemas
  },
  {
    path: '/center',
    component: Center
  }
]
```

4. 在app.vue中插入路由容器

```html
<!--  路由容器  -->
    <router-view></router-view>
```

## 重定向

在index.js中

```js
//  重定向
  {
    path: '*',
    redirect:'/films'
  }
```

## 声明式导航

```html
    <!--  声明式导航  -->
    <ul>
      <li>
        <a href="/#/films">电影</a>
      </li>
      <li>
        <a href="/#/cinemas">影院</a>
      </li>
      <li>
        <a href="/#/center">中心</a>
      </li>
    </ul>
```

```html
 <ul>
      <!--   vue-router 声明式导航(3之前，包括3)   -->
      <li>
        <router-link to="/films" active-class="kerwinactive">电影</router-link>
      </li>
      <li>
        <router-link to="/cinemas" active-class="kerwinactive">影院</router-link>
      </li>
      <li>
        <router-link to="/center" active-class="kerwinactive">中心</router-link>
      </li>
    </ul>

    kerwinactive为自定义属性，也可以在style中直接加
    .router-link-active {
                        color: red;
}
```  

```html
      <router-link to="/films" custom v-slot="{navigate,isActive}">
        <li @click="navigate" :class="isActive?'kerwinactive':''">电影</li>
      </router-link>

      <router-link to="/cinemas" custom v-slot="{navigate,isActive}">
        <li @click="navigate" :class="isActive?'kerwinactive':''">影院</li>
      </router-link>

      <router-link to="/center" custom v-slot="{navigate,isActive}">
        <li @click="navigate" :class="isActive?'kerwinactive':''">中心</li>
      </router-link>

以上是新版本插槽写法，在旧版本中使用tag="li"
custom 表示自定义，
在to加上:实现动态绑定，可遍历出这三个节点

<router-link v-for="i in datalist " :to="i.adress" custom v-slot="{navigate,isActive}">
<li @click="navigate" :class="isActive?'kerwinactive':''">{{i.name}}</li>
</router-link>

 datalist: [{adress:"/films",name:"电影"}, {adress:"/cinemas",name:"影院"},{adress:"/center",name:"中心"},]
```

### 嵌套路由

只切换一个组件中的一个组件，在该组件中想切换放入一个容器`<router-view></router-view>`

在index.js中引入

```js
import Films from "@/views/Films";
import Nowplaying from "@/views/films/Nowplaying";
import Comingson from "@/views/films/Comingson";

// 在配置表中的films中加入children属性
    path: '/films',
    component: Films,
    children: [
      {
        path: '/films/nowplaying',
        component: Nowplaying
      },
      {
        path: '/films/comingson',
        component: Comingson
      }
    ],
```

### 编程式导航

列表的详情页跳转,方法一router-link

```html
      <router-link to="/detail">
      {{data}}
      </router-link>
```

2.编程式导航

```html
      <li v-for="data in datalist" :key="data" @click="handleChangePage()">
        {{ data }}
      </li>
```

```js
        methods: {
    handleChangePage() {
    //   location.href = '#/detail'   这个方法只能判断带#的
     this.$router.push('/detail')   //这个方法可以判断是否带#，vue官方方法，与router-link搭配使用
    }
  }
```

### 动态路由

在nowplaying中传入id

```html
      <li v-for="data in datalist" :key="data" @click="handleChangePage(data)">
        {{ data }}
      </li>
```

```js
  methods: {
      handleChangePage(id)
      {
        // location.href = '#/detail'
        console.log(id)
        this.$router.push(`/detail/${id}`)      // 相当于/detail/11111，id会动态切换
      }
    }
```

在index.js中加入动态二级路由

```js
  {
    path: '/detail/:id',  // 动态二级路由,id名字可随意替换
    component: Detail
  },
```
利用生命周期可以拿到动态路由的id

```js
  created() {
    // 当前匹配的路由
    console.log("created",this.$route.params.id)    //route而不是router,id与index.js中自己取的名字匹配
  }
```

### 命名路由

index.js,name属性

```js
  {
    name:'kerwinData',
    path: '/detail/:id',  // 动态二级路由
    component: Detail
  },
```

```js
      //  2-通过命名路由跳转
      this.$router.push({
        name: 'kerwinData',
        params: {
          id
        }
      })
```

### 路由模式

#### hash

- 定义：hash 模式是一种把前端路由的路径用井号 # 拼接在真实 url 后面的模式。当井号 # 后面的路径发生变化时，浏览器并不会重新发起请求，而是会触发 onhashchange 事件。

- hash 可以改变 url ，但是不会触发页面重新加载（hash的改变是记录在 window.history 中），即不会刷新页面。也就是说，所有页面的跳转都是在客户端进行操作。因此，这并不算是一次 http 请求，所以这种模式不利于 SEO 优化。hash 只能修改 # 后面的部分，所以只能跳转到与当前 url 同文档的 url 。

- hash 通过 window.onhashchange 的方式，来监听 hash 的改变，借此实现无刷新跳转的功能。

- hash 永远不会提交到 server 端（可以理解为只在前端自生自灭）

#### History模式

- 定义：history API 是 H5 提供的新特性，允许开发者直接更改前端路由，即更新浏览器 URL 地址而不重新发起请求。

- 与hash的区别：

```
正常页面浏览

https://github.com/xxx 刷新页面

https://github.com/xxx/yyy 刷新页面

https://github.com/xxx/yyy/zzz 刷新页面

改造H5 history模式

https://github.com/xxx 刷新页面

https://github.com/xxx/yyy 前端跳转，不刷新页面

https://github.com/xxx/yyy/zzz 前端跳转，不刷新页面
```

- history的特点

新的 url 可以是与当前 url 同源的任意 url ，也可以是与当前 url 一样的地址，但是这样会导致的一个问题是，会把重复的这一次操作记录到栈当中。
通过 history.state ，添加任意类型的数据到记录中。
可以额外设置 title 属性，以便后续使用。
通过 pushState 、 replaceState 来实现无刷新跳转的功能。

- 存在问题

- 对于 history 来说，确实解决了不少 hash 存在的问题，但是也带来了新的问题。具体如下：

- 使用 history 模式时，在对当前的页面进行刷新时，此时浏览器会重新发起请求。如果 nginx 没有匹配得到当前的 url ，就会出现 404 的页面。

- 而对于 hash 模式来说，  它虽然看着是改变了 url ，但不会被包括在 http 请求中。所以，它算是被用来指导浏览器的动作，并不影响服务器端。因此，改变 hash 并没有真正地改变 url ，所以页面路径还是之前的路径， nginx 也就不会拦截。
因此，在使用 history 模式时，需要通过服务端来允许地址可访问，如果没有设置，就很容易导致出现 404 的局面。

- 两者选择

- to B 的系统推荐用 hash ，相对简单且容易使用，且因为 hash 对 url 规范不敏感；
- to C 的系统，可以考虑选择 H5 history ，但是需要服务端支持；
- 能先用简单的，就别用复杂的，要考虑成本和收益。

### 路由拦截

#### 全局拦截

- meta:路由源信息

```js
  {
    path: '/center',
    component: Center,
    meta: {
      isKerwinRequired: true
    }
  },
  {
    path: '/order',
    component: Order,
    meta: {
      isKerwinRequired: true
    }
  }

//全局拦截
router.beforeEach((to, from, next) => {
  console.log(to)
  if (to.meta.isKerwinRequired) {      // 授权通过
    // 判断本地存储中是否有token
    if (localStorage.getItem('token')) {
      next()
    } else {
      next('/login')
    }
  } else {
    next()
  }

})
```

#### 局部拦截

直接写在center的路由代码中

```js
方法一：
  {
    path: '/center',
    component: Center,
    meta: {
      isKerwinRequired: true
    },
    // 路由独享拦截
    beforeEnter: (to, from, next) => {
      console.log(to)
      if (to.meta.isKerwinRequired) {      // 授权通过
        // 判断本地存储中是否有token
        if (localStorage.getItem('token')) {
          next()
        } else {
          next({
            path: '/login',
            query: {redirect: to.fullPath}
          })
        }
      } else {
        next()
      }
    }
  },

方法二：
在组件中编写路由的生命周期函数
export default {
  name: "Center",
  // 路由的生命周期
  beforeRouteEnter(to,from,next){
    if (localStorage.getItem('token')) {
      next()
    } else {
      next({
        path: '/login',
        query:{redirect: to.fullPath}
      })
    }
  }
}

```

### 路由懒加载

```js
// import Order from "@/views/Order";注释掉
  {
    path: '/order',
    component: ()=> import('@/views/Order'),  // 懒加载,到这个地方才开始导入
    meta: {
      isKerwinRequired: true
    }
  },
```

## rem复习

```html
    <script>
        //          fontsize计算
        document.documentElement.style.fontSize = document.documentElement.clientWidth/750*100+'px'

        // 750为设计稿的要求宽度，100是为了计算方便
    </script>
    <!-- 使用方法 -->
    <style>
  body {
    font-size: 16px;    //还原，不然会撑开
  }

  .box {
  width: 7.5rem;
  height: 200px;
  background-color: yellowgreen;
  }
    </style>
```

> 模块化开发中，只有