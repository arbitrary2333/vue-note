## Vue查漏补缺

1、vue监测数组的变化的过程（重写数组方法）：

​	1>调用js原生数组的方法

​	2>更新DOM（diff算法比较新旧虚拟DOM树，并更新差异）	

2、Vue监视数据的原理：

​	(1)、Vue会监视data中所有层次的数据

​	(2)、如何监测对象中的数据？

​		通过setter实现监视，且要在new Vue时就传入需要监视的数据

​			1>对象中后追加的属性，Vue默认不做响应式处理

​			2>如需给后添加的属性做响应式，请使用如下API：

​				Vue.set(target，propertyName，value)或

​				vm.$set(target，propertyName，value)

​	(3)、如何监测数组中的数据？

​		通过包裹数组更新元素的方法实现（重写数组方法），本质就是做了两件事：

​			1>调用js原生数组方法对数组进行更新

​			2>重新解析模板，更新视图

​	(4)、在Vue修改数组中的某个元素一定要用如下方法：

​		1>使用这些API：push()、pop()、shift()、unshift()、splice()、sort()、reverse()

​		2>Vue.set()、vm.set()

​	特别注意：Vue.set()和vm.set()不能给vm和vm中的根数据对象添加属性！！！

3、label的使用：

​	与input使用：关联input，当点击账号时也可以获取焦点

​	<label for="demo">账号：</label>

​	<input type="text" id="demo"/>

4、form表单提交跳转需要组织默认行为来防止跳转

​	@submit.prevent="submit"

5、v-model所存储的数据均为字符串（有时前端向后端传递数据需要传Number类型），若想保存Number类型		数据需要用number修饰符：v-model.number="xxx"

6、lazy修饰符使用

​	v-model.lazy=""   ===>   作用：只为data赋一次值，类似防抖

7、trim修饰符使用

​	v-model.trim=""   ===>   作用：去掉前后空格

