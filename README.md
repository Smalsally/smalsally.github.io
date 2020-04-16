Less 是一门 CSS 预处理语言，它扩充了 CSS 语言，增加了诸如变量、嵌套、运算符、混合（mixin）、继承、函数等功能。详情可参考：https://less.bootcss.com/

1、cookie，sessionStorage，localStorage是存放在客户端，session对象数据是存放在服务器上，实际上浏览器和服务器之间仅需传递session id即可，服务器根据session-id找到对应的用户session对象，session存储数据更安全一些，一般存放用户信息，浏览器只适合存储一般的数据；

2、cookie数据始终在同源的http请求中携带，在浏览器和服务器来回传递，里面存放着session-id、sessionStorage，localStorage仅在本地保存；

3、大小限制区别，每条cookie长度不能超过4kb（否则会被截掉），localStorage在谷歌浏览中2.6MB；

4、数据有效期不同，cookie在设置的（服务器设置）有效期内有效、不管窗口和浏览器关闭，sessionStorage仅在当前浏览器窗口关闭前有效、关闭即销毁（临时储存），localStorage始终有效（除非主动删除数据）；

5、localStorage和sessionStorage不会随着http 发送到服务器端，所以安全性相对于cookie来说会比较高一点，不会担心截获，但仍然存在伪造问题。

ps: cookie 保存位置：如果没有设置过期时间，则保存在内存中，浏览器关闭即销毁；
                    如何设置了过期时间，则保存在系统硬盘中，即到期后才销毁


token、cookie、session三者的理解：
    1、token就是令牌，比如你授权(登录)一个程序时,他就是个依据,判断你是否已经授权该软件（最好的身份认证，安全性好，且是唯一的）用户身份的验证方式；

    2、cookie是写在客户端一个txt文件，里面包括登录信息之类的，这样你下次在登录某个网站，就会自动调用cookie自动登录用户名服务器生成，发送到浏览器、浏览器保存，下次请求再次发送给服务器（存放着登录信息）；
缺点：1.数量和长度的限制，每个特定的域名下最多生成20个cookie（chorme和safari没有限制）；2.安全性问题
优点：保存客户端数据，分担了服务器存储的负担；

    3、session是一类用来客户端和服务器之间保存状态的解决方案，会话完成被销毁（代表的就是服务器和客户端的一次会话过程）cookie中存放着sessionID，请求会发送这个id，sesion因为request对象而产生；
    

TCP三次握手：
   客服端发c起请求连接服务器端s确认，服务器端也发起连接确认客服端确认。

   第一次握手：客服端发送一个请求连接，服务器端只能确认自己可以接受客服端发送的报文段；
   
   第二次握手： 服务端向客服端发送一个链接，确认客服端收到自己发送的报文段；
   
   第三次握手： 服务器端确认客服端收到了自己发送的报文段；

get/post的区别：
   . get是从服务器上获取数据，post是像服务器传送数据；
   
   . get请求可以将查询字符串参数追加到url的末尾,post是放在请求体中；
   
   . get请求可以被浏览器缓存、收藏、记录，post不会；
   
   . get提交的数据大小有限制，（因为浏览器对url的长度有限制），post的方法提交的数据没有限制;
   
   . get需要request.queryString来获取变量的值，而post方式通过request.from来获取变量的值;
   
   . get的方法提交数据，会带来安全问题，比如登录一个页面，通过get的方式提交数据，用户名和密码就会出现在url上,post比get安全性更高;
   
 js中深拷贝和浅拷贝的区别？
   答：简单点来说，就是假设B复制了A，当修改A时，看B是否会发生变化，如果B也跟着变了，说明是浅拷贝，如果B没变，那就是深拷贝。
       深入点来说，就是B复制了A，如果B复制的是A的引用，那就是浅拷贝，如果B复制的是A的本体，那就是深拷贝。
   
vue知识点：

 1、第一次页面加载会触发哪几个钩子？
   答：会触发 下面这几个beforeCreate, created, beforeMount, mounted 。
   
 2、Vue与Angular以及React的区别？
 
   1、与AngularJS的区别：
   相同点： 都支持指令：内置指令和自定义指令；都支持过滤器：内置过滤器和自定义过滤器；都支持双向数据绑定；都不支持低端浏览器。
   不同点： 
     AngularJS的学习成本高，比如增加了Dependency Injection特性，而Vue.js本身提供的API都比较简单、直观；
  在性能上，AngularJS依赖对数据做脏检查，所以Watcher越多越慢；Vue.js使用基于依赖追踪的观察并且使用异步队列更新，所有的数据都是独立触发的；
     
   2、与React的区别：
   相同点: 
     React采用特殊的JSX语法，Vue.js在组件开发中也推崇编写.vue特殊文件格式，对文件内容都有一些约定，两者都需要编译后使用；中心思想相同：一切都是组件，
   组件实例之间可以嵌套；都提供合理的钩子函数，可以让开发者定制化地去处理需求；都不内置列数AJAX，Route等功能到核心包，而是以插件的方式加载；在组件开发中都支持mixins的特性。
   不同点： React采用的Virtual DOM会对渲染出来的结果做脏检查；Vue.js在模板中提供了指令，过滤器等，可以非常方便，快捷地操作Virtual DOM。
   
3、vue.js的两个核心是什么？
   答：数据驱动、组件系统
   
   
 父组件向子组件传值？
  父组件通过标签属性传值，子组件通过props接收值
  
  子组件向父组件传值？
    父组件通过V-On绑定属性事件，子组件通过this.$emit("方法名"，"参数")来触发父组件的方法
    
    
  兄弟组件之间传值或多级组件之间传值？
   1、先传给父组件，再有父组件传给子组件；
   2、建立一个公共组件，比如bus组件，两个子组件分别引入bus组件，然后通过 bus.$emit("方法名"，"参数") 来发送数据，通过 bus.$on("方法名"，"参数")来监听数据；
  
   
4、 es6有哪些新语法，和es5有什么区别？
   答：. 新增let、const变量，箭头函数，模板字符串，class类，模块化，promise；
       . ES5 reuqire,react,createclass
      
   let、const、var三者的区别？
   答：var声明的是一个变量，存在变量提升（即变量可以在声明之前使用，但值为undefined）；
       let作用域是块级作用域，不存在变量声明提前；不能重复定义；不会成为全局对象的属性（如：let a =3, console.log(window.a) // undefined）;
       const一般声明的是常量，一旦声明，常量的值就不能改变(必须初始化 如：const b; //报错，必须初始化;)；不存在变量声明提前；   
       
  箭头函数和普通函数的区别？
   答：1、箭头函数是匿名函数，不能作为构造函数，不能使用new;
       2、箭头函数没有原型属性；
       3、箭头函数的this永远指向其上下文的this（指向的是定义它的对象，而不是使用时所在的对象），任何方法都改变不了其指向，如 call(), bind(), apply()；
       4、普通函数的this指向调用它的那个对象。
       
   call()方法返回的结果是打散的参数，apply()返回的是数组，bind（）返回的是函数
       
5、promise:是一个对象，可以获取异步操作的消息，有三种状态：pending(进行中)，resolved(成功), rejected(失败）,一旦状态改变（从pending变为Resolved和从pending变为Rejected),就不会再变。
   promise 对象用then方法，有两个回调函数作为参数，第一个是成功时的回调，第二个是失败时的回调（可选的），两个函数都接受promise对象传出的对象作为参数.
   Promise对象.then(function(){
   // success
   },function(){
   //failure
   });
   
 6、如何实现vue前端跨域，用proxyTable解决
    答：打开config下面的index.js，找到proxyTable，添加以下代码即可：
    '/api': { //替换代理地址名称
      target: 'http://api.douban.com/', //代理地址
     changeOrigin: true, //可否跨域
     pathRewrite: {
     '^/api': '' //重写接口，去掉/api
    }
}
配置完之后需要重启下项目 npm run dev，重启之后，就可以调用，实现跨域了（参考链接地址：https://www.cnblogs.com/zlfProgrammer/p/7997936.html）

7、vue 设置每个页面的title
  答：由于vue文件中只有一个Index.html 文件，title 显示需要通过vue-router来设置
  1：router目录中的index.js里面添加meta属性
  export default new Router({
    // mode: 'history',
  routes: [
      {
      path: '/',
      name: 'Home',
      component: function(resolve){ require(['../components/model/index_home.vue'],resolve)},
      meta: {
        title: '锦穗'
      }
    },{
        //腕表
      path:'/watchPage',
      name:'watchPage',
      component:function(resolve){ require(['../components/model/watchPage/watchPage.vue'],resolve)},
      meta: {
        title: '腕表'
      }
    }]
})
 2：在main.js  在每一个meta里面设置页面的title名字，最后在遍历
 router.beforeEach((to, from, next) => {
  /* 路由发生变化修改页面title */
  if (to.meta.title) {
    document.title = to.meta.title
  }
  next()
})
Vue.beforeEach(function(to,form,next){}) /*在跳转之前执行*/
Vue.afterEach(function(to,form))/*在跳转之后判断*/
在路由跳转的时候，我们需要一些权限判断或者其他操作。这个时候就需要使用路由的钩子函数。
beforeEach函数有三个参数：to:router即将进入的路由对象； from:当前导航即将离开的路由； next:Function,进行管道中的一个钩子，如果执行完了，则导航的状态就是 confirmed （确认的）；否则为false，终止导航。
afterEach函数不用传next()函数； 

 什么是vue生命周期？
  答：vue实例从创建到销毁的过程，就是生命周期。从开始创建、初始化数据、编译模板、挂载dom->渲染、更新->渲染、销毁等一系列过程，称为vue的生命周期。
  
vue生命周期的作用是什么？
  它的生命周期中有多个事件钩子，让我们在控制整个vue实例的过程中更容易形成好的逻辑。
  
 vue双向数据绑定的原理？
   就是利用object.defineProperty()这个方法重新定义对象，获取属性值(get)和设置属性值(set)的操作来实现的。
   
 mvvm的理解？
  Model代表数据模型 （也可以在Model中定义数据修改和操作的业务逻辑），
  View 代表ui视图 （它负责将数据模型转化成ui展现出来）
  ViewModel 负责监听数据的改变和控制视图的更新，处理用户交互的。在 Mvvm 架构下，View和Model之间并没有直接联系，而是通过ViewModel进行交互，Model和
  ViewModel之间的交互是双向的，因此View数据的变化会同步到Model中，而Model数据的变化也会立即反应到View上。
这种模式实现了 Model 和 View的数据自动同步，因此开发者只需要专注对数据的维护操作即可，而不需要自己操作dom。
  
  
 v-if和v-show区别？
  v-if 按照条件是否渲染；v-show 是display的block或none
  
 怎么定义vue-router的动态路由？怎么获取传过来的值？
   在router目录下的index.js文件中，对pash 属性加上/:id, 使用router对象的params.id获取。
   
 Vue中如何监控某个属性值的变化？
  可以通过 computed 来实现。利用计算属性的特性来实现的，当依赖改变时，便会重新计算一个新值。
  
 简述vue的响应式原理？
   当一个VUE实例创建时，vue会遍历data选项的属性，用object.defineProperty将它们转为 getter/setter 并且在内部追踪相关依赖，在属性被访问和修改时通知
   变化。每个组件实例都有相应的watcher 程序实例，它会在组件渲染的过程中把属性记录为依赖，之后当依赖项的setter被调用时，会通知watcher重新计算，从而使
   它关联的组件得以更新。

8、Vue-router 中hash模式和history模式的区别？
   答：hash模式url里面永远带着#号，我们在开发当中默认使用这个模式。那么什么时候要用history模式呢？如果用户考虑url的规范那么就需要使用history模式，
  因为history模式没有#号，是个正常的url适合推广宣传。当然其功能也有区别，比如我们在开发app的时候有分享页面，那么这个分享出去的页面就是用vue或是react做的，咱们把这个页面分享到第三方的app里，
  有的app里面url是不允许带有#号的，所以要将#号去除那么就要使用history模式，但是使用history模式还有一个问题就是，在访问二级页面的时候，做刷新操作，会出现404错误，那么就需要和后端人配合让他配置一下apache或是nginx的url重定向，重定向到你的首页路由上就ok啦。

                         hash与history的区别
 	          hash	                 history
url显示:	  有#，很Low	             无#，好看
回车刷新:	可以加载到hash值对应页面	  一般就是404掉了
支持版本:	支持低版本浏览器和IE浏览器	HTML5新推出的API（pushState与replaceState）

总结：
hash模式其实是利用了window可以监听onhashchange事件，也就是说你的url中的哈希值（#后面的值）如果有变化，前端是可以做到监听并做一些响应，这么一来，即使前端并没有发起http请求他也能够找到对应页面的代码块进行按需加载。
history模式里面的2个api作用就是可以将url替换并且不刷新页面,http并没有去请求服务器该路径下的资源，一旦刷新就会显示404。这就需要服务器端做处理，将不存在的路径请求重定向到入口文件（index.html）。
pushState方法不会触发页面刷新，只是导致history对象发生变化，地址栏会有反应。

传统的路由指的是：当用户访问一个url时，对应的服务器会接收这个请求，然后解析url中的路径，从而执行对应的处理逻辑。这样就完成了一次路由分发。
而前端路由是不涉及服务器的，是前端利用hash或者HTML5的history API来实现的，一般用于不同内容的展示和切换。

注意：history模式下，build之后本地 index.html 打开是无效的。 hash模式下，build之后本地 index.html 打开正常！

9、vue中keep-alive的用法？
  答：它是vue的一个内置组件用来缓存组件内容的状态，避免重新渲染（在开发vue项目的时候，有一部分组件是没必要多次渲染的）
  具体用法参考链接： https://blog.csdn.net/fu983531588/article/details/90321827
  
10、 vue跳转不同页面的多种方法？ 
答： <!-- 直接跳转 -->
<router-link to='/testDemo'>
    <button>点击跳转2</button>
</router-link>
 
<!-- 带参数跳转 -->
<router-link :to="{path:'地址',query:{setid:123456}}">
    <button>点击跳转1</button>
</router-link>
 
<router-link :to="{name:'testDemo',params:{setid:1111222}}">
    <button>点击跳转3</button>
</router-link>
----------------------------------------------------------------------------------------------------
2：this.$router.push() 方法
举例：
<template>
    <div id='test'>
        <button @click='goTo()'>点击跳转4</button>
    </div>
</template>
<script>
    export default{
        name:'test',
        methods:{
            goTo(){
                //直接跳转
                this.$router.push('/testDemo');
 
                //带参数跳转
                this.$router.push({path:'/testDemo',query:{setid:123}});   结果为：http://localhost:8080/#/testDemo?setid=123
                this.$router.push({name:'test',params:{setid:111}});   结果为：http://localhost:8080/#/test/111
                this.$router.push({params:{setid:111}});   结果为：http://localhost:8080/#/111 (注意和上一个区别)
            }
        }
    }
</script>

11、vue中scoped深度作用选择器用法？
  如果你希望 scoped 样式中的一个选择器能够作用得“更深”，例如影响子组件，你可以使用 >>> 操作符：
  如：<style scoped>
        .a >>> .b { /* ... */ }
      </style>
上述代码将会编译成： .a[data-v-f3f3eg9] .b { /* ... */ }
有些像 Sass/less 之类的预处理器无法正确解析 >>> 这种情况下你可以使用 /deep/ 或 ::v-deep 操作符,两者都是 >>> 的别名，同样可以正常工作;


   
 其他知识点：
 
 CSS部分：
 
   css选择符有哪些？哪些属性可以继承？
    1.id选择器（ # myid）
    2.类选择器（.myclassname）
    3.标签选择器（div, h1, p）
    4.相邻选择器（h1 + p）
    5.子选择器（ul > li）
    6.后代选择器（li a）
    7.通配符选择器（ * ）
    8.属性选择器（a[rel = "external"]）
    9.伪类选择器（a: hover, li:nth-child）
    可继承的样式： font-size font-family color, text-indent（首行文本的缩进）;
    不可继承的样式：border padding margin width height ;

 
  1、CSS中link 和@import的区别是？
  答：. link属于HTML标签，而@import是CSS提供的;
      . 页面被加载时，link会同时被加载, 而@import被引用的CSS会等到引用它的CSS文件被加载完再加载;
      . @import是css2.1后提出的(ie5以上才能识别)，而link是不存在兼容问题；
      . js操作DOM，可以使用link改变样式，无法使用@import的方式使用样式
      
   标准盒模型和IE盒模型的区别?
   ps: 每个元素都可以看成是一个容器或一个盒子,这个盒子由4个部分组成：margin,padding,boder,内容；
     答：标准盒模型元素内容的宽=内容的宽 box-sizing:content-box;
         IE盒模型元素内容的宽=元素内容的宽+border+padding  box-sizing:border-box;
         
    em和rem的区别？
    em: 元素的字体大小是根据父元素字体大小设置的;
    rem: 元素的大小是由根元素去决定的；
    
   display:none和visible:hiddlen区别？
    使用 display:none属性后，HTML元素（对象）的宽度、高度等各种属性值都将“丢失”;
    而使用visibility:hidden属性后，元素虽然不在页面中显示，但它所占据的空间位置仍然存在；也就是说它仍具有高度、宽度等属性值；
    
   position的absolute与fixed共同点与不同点：
     共同点： 1、改变行内元素的呈现方式，display被置为block；
             2、让元素脱离文档流，不占据空间；
	     3、默认会覆盖到非定位元素上
     不同点： absolute的”根元素“是可以设置的，而fixed的”根元素“固定为浏览器窗口。当你滚动网页时，fixed元素与浏览器窗口之间的距离是不变的；
     
     
     
   
  JS部分：
  
  null和underfind区别？
   undefined表示缺少值，也就是它应该有值，但没有定义。典型用法：
   （1）变量被声明了，但没有赋值时，就等于undefined。
    (2）调用函数时，应该提供的参数没有提供，该参数等于undefined。
    (3）对象没有赋值的属性，该属性的值为undefined。
    (4）函数没有返回值时，默认返回undefined。
   null表示没有对象，即该处不应该有值 (也就是 空，没有)。典型用法是：
   （1） 作为函数的参数，表示该函数的参数不是对象。
   （2） 作为对象原型链的终点。
   
  使用es6中的set实现数组去重：
    const uniqueArray = new Set([1,2,2,2,3,4,5,5,6,7,9,9,8]);
     console.log(uniqueArray)   // 1, 2, 3, 4, 5, 6, 7, 9, 8
     
   set的其他使用方法有:
    . add(value) 添加某个值; 例：const newSetObject = new Set(1);newSetObject.add('Raymon') //1,Raymon
    . has(value) 检查是否存在某个值,返回值为布尔类型；  例：const numbersSet = new Set([1,2,3,4,5]);numberSet.has(4); // true
    . delete(value) 删除某个值，删除成功返回true，否则返回false； 例：const numbersSet = new Set([1,2,3,4,5])；numbersSet.delete(2) //true; console.log(numbersSet) // 1,3,4,5
    . clear(value) 清除所有数据；没有返回值；
    . size属性表示set集合中有多少个元素  （注意：NaN被Set认为是相同的,{}被认为是不同的）
        例如：var set = new Set([{},{}])；set  //{{},{}}；set.size  // 2
             var set = new Set([NaN,NaN])；set  //{NaN}；set.size  // 1
	  
    遍历器：keys()：返回键名的遍历器。
           values()：返回键值的遍历器。
           entries()：返回键值对的遍历器。
           forEach()：使用回调函数遍历每个成员
  举例说明：![Image](https://github.com/Smalsally/status/blob/master/image/bianliqi.png)

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text



