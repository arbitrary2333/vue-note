## Vue查漏补缺

1、路由

- 定义：路由就是一组key-value的对应关系，key为路径，value为组件
- 多个路由需要经过路由器的管理
- SPA（单页面）应用（vue-router专门用来实现SPA单页面应用）

2、对SPA的理解

- 单页web应用
- 整个页面只有一个完整的页面
- 点击页面中的导航链接不会刷新页面，只会做页面的局部刷新

3、router-link的属性active-class，路由被激活时的样式

4、router-link实现切换，router-view指定展示位置

5、注意事项

![1654084279145](C:\Users\86180\AppData\Roaming\Typora\typora-user-images\1654084279145.png)

6、命名路由

​	作用：简化路由的跳转

​	如何使用：

​		1>给路由命名

​		![1654084494161](C:\Users\86180\AppData\Roaming\Typora\typora-user-images\1654084494161.png)

​		2>简化跳转

​		![1654084551077](C:\Users\86180\AppData\Roaming\Typora\typora-user-images\1654084551077.png)

7、路由的props配置

​	作用：让路由组件更方便的接收到参数

![1654084729647](C:\Users\86180\AppData\Roaming\Typora\typora-user-images\1654084729647.png)

8、router-link的replace属性

​	作用：控制路由跳转时操作浏览器历史纪录的模式

​	浏览器的历史记录有两种写入模式：push为追加记录，replace为替换当前记录

​	开启replace：`<router-link replace ></router-link>`

9、keep-alive缓存路由组件

​	作用：让不展示的路由组件保持挂载，不被销毁

​	具体编码：

```html
<keep-alive include="News">
    <router-view></router-view>
</keep-alive>
```

​	注意：include属性的值为组件名，是每个组件中的name属性，如果想有多个组件缓存，需要降值辨伪数组

10、路由组件的两个生命周期

- activated路由组件被激活时触发
- deactivated路由组件失活时触发

11、路由守卫

​	作用：对路由进行权限控制

​	分类：全局守卫、独享守卫、组件内守卫

​	全局守卫：

![1654085574846](C:\Users\86180\AppData\Roaming\Typora\typora-user-images\1654085574846.png)

​	独享路由：在router配置对象中单独写beforeEnter

​	组件内路由：组件内配置beforeRouteEnter(){...}和beforeRouteLeave(){...}

12、路由配置对象中的meta为路由元信息，每个路由对象的一个属性，里面存取权限或网站标题等信息

13、路由中的hash和history的区别

![1654085992212](C:\Users\86180\AppData\Roaming\Typora\typora-user-images\1654085992212.png)

