## Vue查漏补缺

1、插件引入

​	功能：用于增强vue

​	本质：包含install方法的一个对象，install第一个参数为Vue，第二个以后的参数是插件使用者传递的数据

​	定义插件：		

```javascript
对象.install = function(Vue, options){
	// 1.添加全局过滤器
	Vue.filter(...)
	
	// 2.添加全局指令
	Vue.directive(...)
	
	// 3.配置全局混入
	Vue.mixin(...)
	
	// 4.添加实例方法
	Vue.prototype.$myMethod = function(){...}
	Vue.prototype.$myProperty = xxx
}
```

​	使用插件：Vue.use()

2、scoped

​	作用：让样式在局部生效，防止冲突

​	简版：nanoid库

3、uuid库

​	作用：生成全球唯一的字符串，常用作生成数据标识

4、props适用于：

​	1>父组件===>子组件 通信

​	2>子组件===>父组件 通信 （要求父先给子传递一个函数）	

5、props注意：

​	1>使用v-model时要切记，v-model绑定的值不能是props传过来的值，因为props是不可以修改的

​	2>props传过来的若是对象类型的值，修改对象中的属性时Vue不会报错，但不推荐这样做

