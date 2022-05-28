## Vue查漏补缺

1、el的两种写法：

​	new Vue时传入el属性

​	先创建Vue实例，再通过vm.$mount('#root')挂载

2、data的两种写法：

​	对象式

​	函数式

​	用到组件时必须用函数式

3、重要原则：由vue管理的函数一定不要使用箭头函数

4、MVVM模型

​	M：模型：对应data中的数据

​	V：视图：模板

​	VM：视图模型：Vue实例对象	

5、data中所有属性最后都出现在了vm身上

6、vm上所有的属性以及Vue原型上所有属性，在vue模板中可以直接使用

7、Object.defineProperty(person，‘age’，{

​			value: xxx   //值

​			enumerable: true   //是否可枚举

​			writable:true   //是否可修改

​			configurable: true    //是否可删除

​			get(){

​				return xxx

​			}

​			set(value){

​				number = value

​			}

​	})

8、vue中的数据代理

​	通过vm对象来代理data对象中属性的操作（读/写）

​	好处：更加方便的操作data中的数据

​	基本原理：

​		通过Object.defineProperty()把data对象中所有属性添加到vm上，

​		为每一个添加到vm上的属性，都指定一个getter/setter。

​		在getter和setter内部去操作data中对应的属性	

​	![1650861037221](C:\Users\86180\AppData\Roaming\Typora\typora-user-images\1650861037221.png)

9、事件的回调需要配置在methods对象中，最终会在vm上

10、vue中的事件修饰符（例如：@click.stop）

​	prevent：阻止默认事件

​	stop：阻止事件冒泡

​	once：事件只触发一次

​	capture：使用事件的捕获模式

​	注意：修饰符可以连续写（例如：@click.prevent.stop）

11、vue中常用的按键别名（例如：@keyup.enter）

​	1>回车——>enter

​	删除——>delete

​	退出——>esc

​	空格——>space

​	换行——>tab

​	注意：按键别名可以连续写（例如：@keyup.ctrl.y）

​	2>vue未提供别名的按键用按键原始的key值去绑定，但要转换为kebab-case（短横线命名）

​	3>系统修饰符：ctrl，alt，shift，meta，需配合keydown使用（keyup会触发按键默认行为）		

​	4>定制按键别名：Vue.config.keyCodes.自定义键名 = 键码