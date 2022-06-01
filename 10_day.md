## Vue查漏补缺

1、自定义事件

​	作用：一种组件间通信方式，适用于子组件===>父组件

​	使用场景：A是父，B是子，B想给A传递数据，那麽就要在A中给B组件绑定自定义事件（事件回调在A中）

​	绑定自定义事件：

​		1>在父组件中，`<Demo @atguigu="test" /> 或 <Demo v-on:atguigu="test" />`

​		2>在父组件中：

```
<Demo ref="demo" />
。。。。。。
mounted(){
	this.$refs.demo.$on("atguigu", this.test)
}
```

​	触发自定义事件：`this.$emit('atguigu', 数据)`

​	解绑自定义事件：`this.$off('atguigu')`

​	组件上也可以绑定原生DOM事件，需要使用native修饰符

2、$destroy

​	作用：销毁当前实例对象，销毁后所有的组件自定义事件也被销毁，原生事件不受影响，但模板不被vue管理

3、全局事件总线

​	作用：一种组件间通信的方式，适用于任意组件间的通信

​	安装全局事件总线：

```
new Vue({
	......
	beforeCreate(){
		Vue.prototype.$bus = this //安装全局事件总线，$bus为当前应用的vm
	}
})
```

​	使用事件总线

​		1>接收数据：A组件想接收数据，则在A组件中给$bus绑定自定义事件，事件的回调留在A组件当中

```
methods:{
	demo(data){...}
}
......
mounted(){
	this.$bus.$on('xxx', this.demo)
}
```

​		2>提供数据：`this.$bus.$emit('xxx', 数据)`

​	最好在beforeDestroy钩子中，用$off去解绑当前组件所用到的事件

4、消息订阅与发布

​	作用：一种组件间通信的方式，适用于任意组件通信

​	使用步骤：

​		1>安装pubsub

​		2>引入

​		3>接收数据：A组件想接收数据，则在A组件中订阅消息，订阅的回调留在A组件自身	

```
methods(){
	demo(data){...}
}
......
mounted(){
	this.pid = pubsub.subscribe('xxx', this.demo)  //订阅消息
}
```

​		4>提供数据：`pubsub.publish('xxx',数据)`

​		5>最好在beforeDestroy钩子中，用pubsub.unsubscribe(pid)去取消订阅

5、$nextTick

​	作用：Vue解析模板不是同步执行，而是等待一部分代码执行完毕后在解析模板，因此$nextTick里的回调会在解析完模板之后立即执行

​	使用场景：在改变数据后要基于更新后的新DOM进行某些操作时，要在$nextTick所指定的回调中执行

6、Vue封装的过度与动画

​	作用：在操作DOM元素时，在合适的时候给元素添加类名

​	图示：

​		![1654081184103](C:\Users\86180\AppData\Roaming\Typora\typora-user-images\1654081184103.png)	

​	写法：

​		1>准备好样式：

​			元素进入的样式

​				(1)、v-enter：进入的起点

​				(2)、v-enter-active：进入的过程中

​				(3)、v-enter-to：进入的终点

​			元素离开的样式

​				(1)、v-leave：离开的起点

​				(2)、v-leave-active：离开的过程中

​				(3)、v-leave-to：离开的终点

​		2>使用<transition>包裹要过渡的元素，并配置name属性	

```html
<transition name="hello">
    <h1>
        你好呀!!!
    </h1>
</transition>
```

​		3>备注：若有多个元素需要过度，则需要使用<transition-group>，且每个元素都指定key值

​	动画库：animate.css库