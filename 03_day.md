## Vue查漏补缺

​	v-on:xxx  或  @xxx  绑定事件

​	事件的回调需要配置在methods对象中，最终会在vm上

2、计算属性：

​	定义：要用的属性不存在，要通过已有属性计算而来

​	原理：底层借助Object.defineproperty方法提供的getter和setter

​	get函数什么时候执行？

​		1>初次读取时会执行一次

​		2>当依赖的数据发生变化时会再次调用

​	优势：与methods实现相比，内部有缓存（可复用），效率更高，调试方便

​	备注：

​		1>计算属性最终会出现在vm上，直接读取使用即可

​		2>如果计算属性要被修改，那必须写set函数去响应修改，且set中要引起所依赖的数据发生变化

​	computed:{	

​		fullName:{

​			get(){

​				return this.xxx+'-'+this.yyy

​			},

​			set(value){				

​			}					

​		}

​	}

3、监听属性：

​	定义：当被监视的属性变化时，回调函数调用

​	监视的属性必须存在，才能进行监视，也可监听computed中的属性

​	监视的两种写法：

​		1>new Vue时传入watch配置

​		2>通过vm.$watch('xxx',{})

​	深度监视：

​		vue自身可以监测对象内部值的变化，但vue提供的watch默认不可以

4、computed与watch区别？

​	1>computed能完成的功能watch都能完成；watch能完成的功能computed不一定能完成

​	2>computed有缓存

​	3>watch可以执行异步任务

5、绑定class样式：

​	字符串写法：适用于样式的类名不确定，需要动态绑定

​		eg：   :class="mood"

​	数组写法：适用于要绑定的样式个数不确定

​		eg：   :class="classArr"------>classArr: [val1, val2, val3]

​	对象写法：样式个数确定，名字确定，但要动态决定用不用

​		eg：   :class="classObj"------>classObj: {key1: true, key2:false}