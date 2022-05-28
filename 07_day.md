## Vue查漏补缺

1、v-clock指令（没有值）

​	1>本质是一个特殊属性，Vue实例创建完毕并接管容器后，会删掉v-clock

​	2>使用css配合v-clock可以解决网速慢时页面展示{{xxx}}的问题		

2、v-once指令（没有值）

​	1>v-once所在节点在初次渲染后，就视为静态内容了

​	2>以后数据的改变不会引起v-once所在结构的更新，可以用于性能优化

3、v-pre指令（没有值）

​	1>跳过所在节点的编译过程

​	2>可利用他跳过没有：没有指令语法，没有插值语法的节点会加快编译

4、自定义指令

​	1>定义语法：

​		(1)、局部指令：

```javascript
new Vue({
    directives:{指令名：配置对象（或属性值为回调函数）}
})
```

​		(2)、全局指令

```javascript
Vue.directive(指令名，配置对象（或回调函数）)
```

​	2>配置对象中常用的三个回调

​		(1)、bind：指令与元素成功绑定时调用

​		(2)、inserted：指令所在元素被插入页面时调用

​		(3)、update：指令所在模板被重新解析时调用

​	3>备注

​		(1)、指令定义时不加v-，但使用时要加v-

​		(2)、指令名如果是多个单词，要使用kebab-case命名方式，不要使用camelCase命名

​		(3)、三个回调的this为window

​		(4)、directives对象里的函数何时被调用：指令与元素成功绑定时；指令所在的模板被重新编译时

5、template

​	完全替换el配置所在的标签

6、生命周期

​	![img](https://img-blog.csdnimg.cn/e4a8169c832443f2a78c6a1ae42a87b3.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5qC86Zu354uQ5oCd,size_20,color_FFFFFF,t_70,g_se,x_16)	

​	注意：销毁阶段需调用vm.$destroy才可执行beforeDestroy与destroyed生命周期函数

