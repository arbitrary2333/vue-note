## Vue查漏补缺

1、组件是什莫？

​	用来实现局部功能效果的代码集合(html,css,js,,image...)

2、模块是什莫？

​	向外提供特定功能的js程序，一般就是一个js文件

3、非单文件组件：

​	一个文件中包含n个组件

4、单文件组件

​	一个文件中只包含1个组件

5、组件：

​	1>使用组件的三个步骤：

​		定义组件（创建组件）、注册组件、使用组件（写组件标签）

​	2>如何定义一个组件:

​		使用Vue.extend(options)创建，其中options和new Vue(options)时传入的配置项几乎完全相同，但也有区别：

​		区别如下：

​			(1)、el不要写------>最终所有的组件都要经过一个vm进行管理，由vm中el决定服务那个容器

​			(2)、data必须写成函数，为什么？------>避免组件被复用时，数据存在引用关系

​		备注：使用template可以配置组件结构

​	3>如何注册组件：

​		1>局部注册：靠new Vue的时候传入components选项

​		2>全局注册：靠Vue.component('组件名'，组件)

​	4>使用组件：

​		<school></school>

​	5>注意：

​		(1)、定义组件时Vue.extend可以省略，可直接写成对象，因此在.vue文件中由export default {}

​		(2)、组件名：

​			一个单词：<school></school>或<School></School>

​			多个单词：<MySchool></MySchool>（有脚手架）或<my-school></my-school>

​	6>关于VueComponent：

​		(1)、school组件本质是一个名为VueComponent的构造函数，且不是程序员定义的，是Vue。extend生成的（详情可见源码，Vue.extend返回了一个VueComponent构造函数）

​		(2)、我们只需要写<school></school>或<school />,Vue解析时会帮我们创建school组建的实例对象，即帮我们执行new Component(options)

​		(3)、关于this指向：

​			<1>、组件配置中：data，method，watch，computed，他们的this均是VueComponent实例对象

​			<2>、new Vue()配置中：data，method，watch，computed，他们的this均是Vue实例对象

​	7>一个重要的内置关系：VueComponent.prototype.__proto__ === Vue.prototype（让组件实例对象可以访问到Vue原型上到属性、方法）

![img](https://img-blog.csdnimg.cn/9f3398cb2cfb4b169951adb53236ad60.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5qC86Zu354uQ5oCd,size_20,color_FFFFFF,t_70,g_se,x_16)

6、单文件组件中的name为开发者工具中所呈现的标签名

7、关于不同版本的vue

​	1>vue.js与vue.rountime.xxx.js的区别？

​		(1)、vue.js是完整版的Vue，包含：核心功能+模板解析器

​		(2)、vue.rountime.xxx.js是运行版的Vue，只包含：核心功能，没有模板解析器

​	2>因为vue.runtime.xxx.js没有模板解析器，所以不能使用template配置项，需要使用render函数接收的createElement函数去指定具体内容（脚手架中main.js中出现的render: h => h(App)）

8、ref属性

​	当在组件标签上写ref属性时，this.$refs.xxx为组件的实例对象

​	当在普通标签上写rerf属性时，this.$refs.xxx为真实DOM元素

9、props

​	接收方式：

​		1>props:["name"]（只接收）

​		2>props:{name: String}（限制类型）

​		3>

```js
props:{
	name:{
		type: String,  //类型
		required: true,  //必要性
		default: '老王'  //默认值
	}
}
```

​	备注：props是只读的，vue底层会检测对props的修改，如果修改了会有警告

​				若业务需要修改，那麽请复制props的内容到data中一份，然后去修改data中的数据

​				props属性比data更早被调用

10、mixin（混合）

​	功能：可以把多个组件公用的配置提取成一个混入对象

​	使用方式：

​		第一步定义混合：	

```js
{
	data(){...},
	methods:{...},
	...
}
```

​		第二步使用混合：

​			(1)、全局混合：Vue.mixin(xxx)

​			(2)、局部混合：mixins:['xxx']

​	注意：当组件中的配置项与混入对象产生冲突时，优先组件中的配置