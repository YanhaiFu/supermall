## 1. vue介绍

### 1.1 编程范式

命令式编程

**声明式编程**

{{}}

**响应式**

MVVM架构

语法糖：简写



### 1.2 传入Vue实例的options

el：string/HTMLElement

决定之后Vue实例管理哪个DOM

data：Object/Function

组件中data必须是一个函数

methods：{[key:string]:Function}



### 1.3 方法和函数



### 1.4 Vue的生命周期

debug

release

回调



###  1.5 vue的template

代码规范：缩进2个空格

CLI->.editconfig



### 1.6 mustache语法

{{变量或表达式}}



### 1.7 其他指令

v-once

v-html

v-pre

v-cloak	//斗篷

v-bind	:	（语法糖）

​	**动态绑定属性**

​	**Mustache 语法不能作用在 HTML 特性上**

​	{key:value} 对象， value：Boolean

​	**this**

​	绑定样式style

v-on	@





## 2. MVVM

model view view model

view层：

model层：

view-model层：



## 3. v-bind

### 3.1 介绍

（语法糖）

​	**动态绑定属性**

​	Mustache 语法不能作用在 HTML 特性上

​	{key:value} 对象， value：Boolean

​	**this**

### 3.2 绑定样式style

#### 3.2.1 对象语法

:style="{key:value}" 

key：属性名

value：属性值

-或驼峰标识

value在解析时，不加单引号，看作变量；加单引号，看作字符串



#### 3.2.2 数组语法

:style="[]"

[] 数组



## 4. 计算属性

### 4.1 介绍

computed:{}

属性

methods没有缓存，性能比computed低

computed有缓存

let有块级作用域



### 4.2 getter和setter

计算属性一般没有set方法，只有get



### 4.3 计算属性和methods的对比

直接拼接（语法过于繁琐）

​	{{firstName}} {{lastName}}

使用methods

​	{{getFullname()}}

**通过computed**

​	{{fullName}}



view在内部对computed做了一层缓存



## 5. ES6

### 5.1 let/var

var没有块级作用域

 **let有块级作用域** 

闭包：**只有函数有作用域**

ES6之前，if和for都没有块级作用域的概念，必须借助于**function的作用域**来解决应用外面变量的问题。

const let

非立即执行，回调



### 5.2 const

将标识符定为常量（优先使用）

const修饰的标识符必须初始化

**指向的对象不能改变，但可以改变对象内部的属性**



### 5.3 ES6对象字面量增强写法

TypeScript

function() {}

## 6. v-on

### 6.1 介绍 

v-on语法糖 @



### 6.2 v-on参数传递

**事件监听时，方法不需要参数，()可以省略**

如果函数需要参数，但是没有传入，那么函数的形参为**undefined**

浏览器自动生成**event对象**

如果方法本身需要参数，但在事件中省略了小括号，Vue会默认将浏览器产生的**event事件对象**作为参数传入到该方法。

获取浏览器event对象：**$event**



### 6.3 v-on修饰符

#### 6.3.1 .stop

调用event.stopPropagation()

停止事件冒泡



#### 6.3.2 .prevent

调用event.preventDefault()

阻止默认行为

#### 6.3.3 .{keyCode | keyAlias}

只当事件是从**特定键**触发时才触发回调



#### 6.3.4.native

监听组件根元素的原生事件

自定义组件



#### 6.3.5 .once

只触发一次回调



## 7. 条件判断v-if

Vue

虚拟DOM：virtual DOM

出于性能考虑，会尽可能**复用**已经存在的元素。 

render



## 8. v-show

决定一个元素是否渲染

对比v-if

v-if：当条件为false时，元素不会存在于DOM中

v-show：当条件为false时，**style="display:none;"**

频繁使用时，选择v-show

当只有一次切换时，选择v-if



## 9. v-for

### 9.1 v-for遍历数组



### 9.2 v-for遍历对象

返回的三种格式：

value in object

(value, key)

(value, key, index)



### 9.3 v-for绑定key

diff算法

使用key给**每一个节点**做一个**唯一**标识，Diff算法可以正确识别节点。**确保一一对应**。

key主要是为了高效的更新虚拟DOM

按内容绑定。



## 10. 数组中哪些方法是响应式的

响应式的数组方法：

栈方法

push()	//在数组**尾部**添加元素

pop()	//删除数组中的**最后一个**元素

队列方法

shift()	//删除数组中的**第一个**元素

unshift()	//在数组**头部**添加元素

​	

splice()

删除/插入/替换

第二个参数

sort()

reverse()

**注意：通过索引修改数组中的元素不是响应式的。**

通过**splice()**实现。

或者**Vue.set(要修改的对象，索引值，修改后的值)**

**可变参数**，数组

function sum(**...num**) {

}



## 11. JS高阶函数的使用

for(let item in 数组)：得到**索引值**

for(let item of 数组)：得到**对象**

数组操作：

函数式编程

编程范式：

命令式/**声明式**/函数式（第一公民：函数，链式编程）

面向对象（第一公民：对象）/面向过程



### 11.1 .filter()

**filter中的回调函数必须返回一个boolean**。

当返回true时，函数内部会自动将回调的n加入到新的数组中；

当返回false时，函数内部会过滤掉这次的n

  let numsNew = nums.filter(function(n) {

   return n <= 100

  })



### 11.2  .map()

 //map

  let nums2New = numsNew.map(function(n) {

   return n * 2

  })

### 11.3 .reduce()

//对数组中所有的元素进行操作

  let result = nums2New.reduce(function(prev, cur, index, array) {

   return prev + cur

  }, 0)



### 11.4 函数式编程

写法一：

//函数式编程

  const nums = [10, 20, 111, 222, 444, 40, 50]

  let result = nums.filter(function(n) {

   return n <= 100

  })

  .map(function(n) {return n * 2})

  .reduce(function(prev, cur) { return prev + cur})



写法二：

let result = nums.filter(n => n < 100).map(n => n * 2).reduce((prev, cur) => prev + cur)



## 12. v-model的使用和原理

### 12.1 介绍

双向绑定**

event对象

$event

方式一：

<input type="text" :value="message" @input="valueChange">



方式二：

<input type="text" :value="message" @input="message = $event.target.value">



方式三：

<input type="text" v-model="message">



### 12.2  v-model结合radio



### 12.3 v-model结合checkbox

 // isAgree: false //单选框

​    hobbies: []  //多选框



### 12.4 input中的值绑定

input中的id和label中的for

<!-- input中的id和label中的for -->

  <!-- 动态绑定 -->

  <label v-for="hobby of originHobbies" :for="hobby">

   <input type="checkbox" :id="hobby" :value="hobby" v-model="hobbies">{{hobby}}

  </label>

v-bind



### 12.5 v-model修饰符

<!-- 1. 修饰符 lazy -->

  <!-- <input type="text " v-model.lazy="message">{{message}} -->



  <!-- 2. 修饰符 number-->

  <!-- <input type="number" v-model.number="message"> -->

  <!-- <h2>{{typeof(message)}}</h2> -->



  <!-- 3. 修饰符 trim-->

  

## 13. 组件化

### 13.1 介绍

Vue中，任何的应用都会被抽象成一棵组件树

步骤：

1. **创建组件构造器**	Vue.extend()

   const cpnCons = Vue.**extend**({

      //ES6语法

      //``可以用于定义字符串，可以换行

      template: `

         <div>

      <h2>我是标题</h2>
      <p>我是内容，哈哈哈哈哈哈哈哈哈</p>
         <p>我是内容， 呵呵呵呵呵呵呵呵</p>
   </div>

   `

  })

2. **注册组件**   Vue.component()

   //参数：组件标签名，组件构造器

     Vue.component('my-cpn', cpnCons)

3. **使用组件**  在Vue实例的作用范围内使用组件

   <div id="app">
       <my-cpn></my-cpn>
       <my-cpn></my-cpn>
       <my-cpn></my-cpn>
       <my-cpn></my-cpn>
     </div>

``可以用于定义字符串，**可以换行**



### 13.2 全局组件和局部组件

**组件必须挂载**



 //**全局组件**，可以在多个Vue的实例中使用

  //Vue.component('my-cpn', cpnCons)



  const app = new Vue({

   el: "#app",

   data: {

​    message: 'hello'

   },

   //**局部组件**

   components: {

​    //key:value

​    mycpn: cpnCons

   },

   methods: {}

  })



### 13.3 父组件和子组件



### 13.4 注册组件的语法糖

先搜索局部组件，然后搜索全局组件

**全局组件**

  Vue.component('comp', {

   template: `

        <div>

​    <h2>我是标题</h2>

        <p>我是内容，哈哈哈哈哈哈哈哈哈</p>
        <p>我是内容， 呵呵呵呵呵呵呵呵</p>
​    </div>

   `

  })



**局部组件**

const app = new Vue({

   el: "#app",

   data: {

​    message: 'hello'

   },

   components: {

​    'comp': {

​     template: `

        <div>

​    <h2>我是标题</h2>

        <p>我是内容，哈哈哈哈哈哈哈哈哈</p>
        <p>我是内容， 呵呵呵呵呵呵呵呵</p>
​    </div>

   `}

  },

  methods: { }

  })



### 13.5 组件模板抽离



<!-- Vue提供了两种方案来定义HTML模块内容 -->

 <!-- 1. 使用<script>标签，类型必须是text/x-template -->

  <script type="text/x-template" id="cpn">

        <div>

​     <h2>我是标题</h2>

          <p>我是内容， 哈哈哈哈</p>
​    </div>

  </script>



 <!-- 2. 使用<template>标签 -->

 <template id="cpn2">

    <div>

   <h2>我是标题2</h2>
      <p>我是内容， hehehehe</p>
  </div>

 </template>



### 13.6 组件访问数据

#### 13.6.1

**组件不能访问Vue实例**

Vue组件应该有自己保存数据的地方

**Vue.component**('comp', {

   template: '#cpn2',

   //data不能是对象类型

   //**data是一个****函数**，**返回一个per-instance**

   //Vue增强写法

   **data() {**

​    **return {**

​     **title: '我是标题2'**

​    **}**

   }

  })



组件的原型指向Vue



#### 13.6.2 

const obj = {

   count: 0

  }

  //注册全局组件

  Vue.component('counter', {

   template: '#counterTemp',

   **//data是一个函数**

   //返回对象

   //栈空间

   data() {

​	//每次返回都新建对象

​    //**return { count: 0 }**

​    return obj

   },

   methods: {

​    increment() {

​     //this

​     this.count++

​    },

​    decrement() {

​     this.count--

​    }

   }

  })

 

### 13.7 父子组件通信

#### 13.7.1 父传子

通过**props**向**子组件**传递数据

//写法一： 数组

   // props: ['cmovies', 'cmessage']



   //写法二： **对象**

   //支持数据类型验证

   //支持自定义类型

   //String/Number/Boolean/Array/Object/Date/Function/Symbol



   //可提供默认值

   props: {

​    cmovies: {

​     type: Array,

​     default: []

​    },

​    cmessage: {

​     type: String,

​     default: 'aaaaa',

​     //必传属性

​     required: true

​    }

   }



注意：驼峰标识

HTML attributes are case-insensitive

js中，cInfo，需要在HTML中转化为c-info

<!-- use "c-info" instead of "cInfo" -->

  <cpn :c-info="info"></cpn>



<!-- 模板 -->

 <template id="cpn">

  <!-- component template should contain exactly one root element -->

    <div>

   <!-- HTML attributes are case-insensitive -->

   <h2>{{cInfo}}</h2>
  </div>

 </template>



#### 13.7.2 子传父

通过**事件**向**父组件**发送消息

**自定义事件** 

**$emit evets**

v-on既可以用于监听DOM事件，也可以用于子组件的自定义事件

methods: {

​    btnClick(item) {

​     //子组件发射，父组件接收

​     **this.$emit**('item-click', item)

​    }

   }



<!-- 父组件模板 -->

  <div id="app">

  <!-- 监听子组件事件 -->

  <cpn **@item-click**="cpnClick"></cpn>

 </div>



methods: {

​    //子组件触发父组件事件

​    cpnClick(item) {

​     console.log(item)

​    }

   }



注意：

//!!!!

​     data() {

​      return {

​       dnumber1: this.num1,

​       dnumber2: this.num2

​      }

​     }

子组件修改父组件的数据



//监听属性

​     **watch**: {

​      dnumber1(newValue) {

​       this.dnumber2 = this.dnumber1 * 100

​       this.$emit('valuechange', this.dnumber1)

​      },

​     },



#### 13.7.3 父子组件的访问方式

**父组件访问子组件：$children/$refs**

方式一：

this.$children是一个**数组类型**，包含所有子组件对象

类型：VueComponent

方式二：

<cpn ref="aaa"></cpn>

this.$refs.aaa.name

this.$refs是一个对象类型，默认为空，需要通过**在组件中添加ref属性**



**子组件访问父组件：$parent**

用的比较少

组件化，提高复用性



**访问根组件：$root**



## 14. slot-组件的插槽

### 14.1 介绍

使封装的组件具有**扩展性**



### 14.2 具名插槽

<template id="cpn">

    <div>

   <slot name="left"><span>左边</span></slot>

   <slot name="center"><span>中间</span></slot>

   <slot name="right"><span>右边</span></slot>

  </div>

 </template>



<div id="app">
    <cpn>
      <!-- 具名插槽 -->
      <span slot="center">标题</span>
      <button slot="left">按钮</button>
    </cpn>
  </div>



### 14.3  编译作用域

<!-- 父组件模板 -->

  <div id="app">

  <!-- 使用子组件 -->

  <!-- v-show 只是简单地切换元素的 CSS 属性 display -->

  <!-- 使用Vue实例中的isShow,不会使用组件中的数据 -->

  <cpn v-show="isShow"></cpn>

 </div>

父组件模板的所有东西都会在**父级作用域**内编译

子组件模板的所有东西都会在**子级作用域**内编译



### 14.4 作用域插槽

父组件替换插槽的标签，但是内容由子组件来提供

<!-- 子组件模板 -->

 <template id="cpn">

    <div>

   <slot name="slot1" :data="pLanguages"></slot>

   <slot name="slot2" :data="pLanguages"></slot>

   <slot name="slot3" :data="pLanguages"></slot>

  </div>

 </template>



<!-- 父组件模板 -->

 <!-- 属于Vue实例,具有Vue的作用域 -->

  <div id="app">

  <cpn>

   <!-- 获取子组件中的pLanguages -->

   <ul slot="slot1" slot-scope="slot1">

​    <li v-for="item of slot1.data">{{item}}</li>

   </ul>



      <div slot="slot2" slot-scope="slot2">

​    <span>{{slot2.data.join('-')}}</span>

   </div>



      <div slot="slot3" slot-scope="slot3">

​    <span>{{slot3.data.join('*')}}</span>

   </div>

   

  </cpn>

 </div>





## 15. 模块化开发

### 15.1 介绍

前端：三大框架

前后端分离

ajax

问题：全局变量同名



### 15.2 CommonJS

module.exports = {

 add, mul

}

const {add, mul} = require('./mathUtil')



### 15.3 ES6

<script src="./aaa.js" type="module"></script>
// 1. 导出方式一

export {

 flag,

 sum

}



// 2. 导出方式二

export let num1 = 1000



// 3. 导出函数/类

export function mul() {



}



// exprot {mul}



export class Person {

 run() {}

}



// 4. export default

// 只能有一个

const address = '北京'

export default address



// export default function() {

// }



## 16. Webpack

### 16.1 介绍

Webpack是一个开源的前端**打包**工具。Webpack 提供了[前端](https://zh.wikipedia.org/wiki/前端和后端)开发缺乏的[模块](https://zh.wikipedia.org/wiki/模組_(程式設計))化开发方式，将各种静态资源视为[模块](https://zh.wikipedia.org/wiki/模組_(程式設計))，并从它生成优化过的[代码](https://zh.wikipedia.org/wiki/程式碼)。[[1\]](https://zh.wikipedia.org/wiki/Webpack#cite_note-1)

**自动处理模块间的依赖**

Webpack可以从[终端](https://zh.wikipedia.org/wiki/終端)、或是更改 `webpack.config.js` 来设置各项功能。[[2\]](https://zh.wikipedia.org/wiki/Webpack#cite_note-2)

要使用 Webpack 前须先安装 [Node.js](https://zh.wikipedia.org/wiki/Node.js)。Webpack 其中一个特性是使用[加载器](https://zh.wikipedia.org/wiki/載入器)来将资源转化成[模块](https://zh.wikipedia.org/wiki/模組_(程式設計))。开发者可以自定义加载器的顺序、格式来因应项目的需求。

**模块化**

gulp不支持模块化



与grunt/gulp的对比

前端自动化任务管理工具

核心是Task



### 16.2 webpack

#### 16.2.1 安装

webpack依赖node环境

npm工具（node packages manager）



```bash
mkdir webpack-demo
cd webpack-demo
npm init -y
npm install webpack webpack-cli --save-dev
```



#### 16.2.2 loader

```bash
npm install --save-dev style-loader css-loader
npm install --save-dev file-loader
npm install -D babel-loader@7 babel-core babel-preset-es2015
npm install vue
npm install --save-dev vue-loader vue-template-compiler
```

使用步骤：

1. 通过npm安装需要使用的loader
2. 在webpack.config.js中的module关键字下进行配置



#### 16.2.3 在webpack中使用Vue

npm install vue --save 

SPA(single page web application)：单页面

多页面：路由



#### 16.2.4 el和template的区别

template中的内容会替换el



### 16.3 plugin

#### 16.3.1 VueLoaderPlugin 

//webpack.config.js

**const VueLoaderPlugin = require('vue-loader/lib/plugin')**

**plugins: [**

  **// 请确保引入这个插件！**

  **new VueLoaderPlugin()**

 **]**

plugin的使用过程：

1. 通过npm安装需要使用的plugin
2. 在webpack.config.js中配置plugin



#### 16.3.2 BannerPlugin

```js
const webpack = require('webpack')

new webpack.BannerPlugin('最终版权归付沿海所有'),
```



#### 16.3.3 htmlWebpackPlugin

```bash
npm install html-webpack-plugin --save-dev
```

```js
const htmlWebpackPlugin = require('html-webpack-plugin')
```

按照给定模板在dist文件夹下生成index.html



#### 16.3.4 uglifyjs-webpack-plugin

```bash
npm install uglifyjs-webpack-plugin --save-dev
```

```js
const uglifyJsPlugin = require('uglifyjs-webpack-plugin')
```

JS压缩

`uglify-js` only supports JavaScript (ECMAScript 5).

To minify ECMAScript 2015 or above, transpile using tools like [Babel](https://babeljs.io/).



### 16.4  搭建本地服务器

基于node.js，内部使用express框架，服务于某个文件夹，检测到更改后，重新编译，测试时，放到缓存中，build时写入硬盘。

```
npm install webpack-dev-server --save-dev
```

​	"start:dev": "webpack-dev-server --open"



### 16.5  配置文件分离

npm install webpack-merge --save-dev

将生产和开发时的配置分离



## 17. Vue CLI

### 17.1 介绍

Command-Line Interface

Vue CLI是一个官方发布的vue.js项目脚手架

使用vue-cli可以快速搭建Vue开发环境以及对应的webpack配置

依赖：node.js/webpack



### 17.2 安装

```bash
npm install -g @vue/cli
vue --version
npm install -g @vue/cli-service-global

npm install -g @vue/cli-init
```



### 17.3 Vue CLI2

#### 17.3.1 介绍

vue init webpack 项目名称

**注意：创建Vue项目出错，提示vue : 无法加载文件C:\Users\xxx\AppData\Roaming\npm\vue.ps1，因为在此系统上禁止运行脚本。有关详细信息，请参阅 https:/go.microsoft.com/fwlink/?LinkID=135170****

**解决方案：**

1. **以管理员身份运行PowerShell**
2. **执行：get-ExecutionPolicy，回复Restricted，表示状态是禁止的**
3. **执行：set-ExecutionPolicy RemoteSigned**
4. **选择**Y



#### 17.3.2 目录结构

V8引擎：C++

package.json

^	通配符，最后一位可变

~	通配符，最后两位可变



#### 17.3.3 ESlint

npm clean cache -force

C:\Users\74567\AppData\Roaming\npm-cache

开发时依赖

运行时依赖



关闭ESlint：config->index.js

useEslint: false



#### 17.3.4 runtime-compiler和runtime-only

第一种：

**runtime-only：（推荐使用）**

```js
new Vue({
	el: '#app',
    render: h=>h(App)
})
```

**render -> UI**

性能更高，代码量更少

**vue-template-compiler**：开发时依赖。组件中的<template>被渲染成render



第二种：

runtime + compiler：

```js
new Vue({
  el: '#app',
  components: { App },
  template: '<App/>'
})
```

**template -> ast -> render -> vdom -> UI**



#### 17.3.5 render函数

1. 普通用法：

```js
new Vue({
  el: '#app',
  // render: h => h(App)
  render: function(createElement) {
    return createElement('h2', {class: 'box'}, [createElement('h2', {class: 'box'}, ['hello world'])])
  }
})
```

2. 传入组件

   ```js
   const cpn = {
     template: `
       <div>{{msg}}</div>
     `,
     data() {
       return {
         msg: '我是组件message'
       }
     },
   }
   
   /* eslint-disable no-new */
   new Vue({
     el: '#app',
     // render: h => h(App)
     render: function (createElement) {
       //return createElement('h2', {class: 'box'}, [createElement('h2', {class: 'box'}, ['hello world'])])
   
       return createElement(cpn)
     }
   })
   ```

   



### 17.4 Vue CL3配置

vue create supermall

vue ui



## 18. 箭头函数

ES6



## 19. 路由

### 19.1 介绍

路由表：

内网IP：MAC地址

npm使用淘宝镜像

```bash
npm config set registry https://registry.npm.taobao.org
npm config get registry
```



### 19.2 前端渲染和后端渲染

#### 19.2.1 后端渲染

jsp：html+css+java代码（动态从数据库读取数据，并动态渲染）

客户端收到的仅仅是静态网页（HTML+CSS）

映射关系



#### 19.2.2 前端渲染

通过**Ajax**请求数据

后端只负责提供数据



url

**静态资源服务器**返回HTML+CSS+JS

**js代码由浏览器执行，**

**$.ajax(url:api接口)**

**提供API接口的服务器返回数据**



### 19.3 前端路由和后端路由

#### 19.3.1 后端渲染

jsp：html+css+java代码（动态从数据库读取数据，并动态渲染）

客户端收到的仅仅是静态网页（HTML+CSS）

后端处理URL和页面之间的映射关系。通过正则对URL进行匹配。交给**Controller**处理。

缺点：整个页面由后端人员编写维护；Model-View-Controller未分离。



#### 19.3.2 前后端分离

Ajax

后端只提供API来返回数据，前端通过Ajax获取数据，并且可以通过JS将数据渲染到页面上。



#### 19.3.3 单页面富应用阶段

SPA最主要的特点是在前后端分离的基础上加了一层**前端路由**

整个网页只有一个页面



url，

静态资源服务器返回（index.html + css + js）

API服务器（连接数据库）



#### 19.3.4 前端路由

url->通过js抽取**组件**，进行页面渲染

url与页面一一对应



核心：改变URL，但整个页面不进行整体刷新



### 19.4 修改方案

#### 19.4.1 URL的hash（默认）

URL的hash也就是**锚点（#）**，本质上是改变window.location的href属性

可以通过直接赋值location.hash来改变href，但是页面不刷新。



#### 19.4.2 H5的history

第一种：

history.pushState({}, '', 'home')

history.back()：移除栈顶元素

显示栈顶元素

**可以返回前一个页面**



第二种：

history.replaceState({}, '', 'home')

替换

**无法返回前一个页面**



第三种：

history.go()

history.back()等价于history.go(-1)，**出栈**

history.forward()等价于history.go(1)，**入栈**



### 19.5 vue-router

#### 19.5.1 介绍

vue-router是基于路由和组件的。

路由用于设定访问路径，将路径和组件映射起来。

在vue-router的单页面应用中，页面的路径的改变就是组件的切换。



#### 19.5.2 安装和使用

```bash
npm install vue-router --save
```

使用：

1. 导入路由对象，并且调用Vue.use(VueRouter)
2. 创建路由实例，并且传入路由映射配置
3. 在Vue实例中，挂载创建的路由实例



配置vue-router：

 1. 创建路由组件

 2. 配置路由映射：组件和路径映射关系

    ```js
    export default new Router({
      routes: [
        {
          // url
          // 协议头 主机名 path
          path: '/home',
          name: 'home',
          component: Home
        },
        {
          path: '/about',
          name: 'about',
          component: About
        }
      ]
    })
    ```

    

 3. 使用路由：通过<router-link>和<router-view>

```js
<template>
  <div>
    <!-- 该标签是一个vue-router已经内置的组件，会被渲染成一个a标签 -->
    <router-link to="/home">首页</router-link>
    <router-link to="/about">关于</router-link>
    <!-- 显示组件的位置 -->
    <router-view></router-view>
  </div>
</template>
```

在路由切换时，切换的是<router-view>**挂载的组件**，其他内容不会改变。



#### 19.5.3 路由的默认值和修改

```js
export default new Router({
  routes: [
    {
      path: '/',
      redirect: '/home'
    },
    {
      // url
      // 协议头 主机名 path
      path: '/home',
      name: 'home',
      component: Home
    },
    {
      path: '/about',
      name: 'about',
      component: About
    }
  ],
    // URL的hash（#）更改为H5的history
  mode: 'history'	
})
```



#### 19.5.4 router-link的其他属性

默认使用history.pushState()

tag：指定route-link被渲染成的标签类型

replace：使用history.replaceState()，不需要赋值。不会留下history记录。

active-class：当<router-link>对应的路由**匹配成功时**，会**自动**给当前元素设置一个**router-link-active**的class，设置active-class可以修改默认的名称



#### 19.5.5 通过代码跳转

```js
this.$router.push('/home')
this.$router.replace('/home')
```



#### 19.5.6 动态路由

```js
{
      path: '/user/:userId',
      name: 'user',
      component: User
 }

export default {
  name: 'User',
  computed: {
    userId () {
      // 得到处于活跃状态的路由
      return this.$route.params.userId
    }
  }
}

<h2>{{$route.params.userId}}</h2>
```



#### 19.5.7 路由的懒加载

build后，dist中的内容

1. app：业务代码

2. manifest：

3. vendor：第三方

一个js文件。

把不同路由对应的组件分割成不同的代码块，当路由被访问的时候才加载对应的组件。



#### 19.5.8 路由的嵌套

一个路径映射一个组件

步骤：

1. 创建对应的子组件，在路由映射中配置对应的子路由
2. 在组件内部使用<router-view>标签



```js
{
      // url
      // 协议头 主机名 path
      path: '/home',
      name: 'home',
      component: () => import('../components/Home'),
      children: [
        {
          path: '/',
          redirect: 'news'
        },
        {
          path: 'news',
          component: () => import('../components/HomeNews')
        },
        {
          path: 'message',
          component: () => import('../components/HomeMessage')
        }
      ]
    },
```

```js
<template>
  <div>
    <h2>我是首页</h2>
    <p>我是首页内容，哈哈哈哈哈</p>
    <router-link to="/home/news">新闻</router-link>
    <router-link to="/home/message">消息</router-link>
    <router-view></router-view>
  </div>
</template>
```



#### 19.5.9 参数传递



## 20. tabbar

### 20.1 实现思路

TabBar中定义插槽，flex布局评分TabBar

自定义TabBarItem，可以传入图片和文字

### 20.2 组件封装

