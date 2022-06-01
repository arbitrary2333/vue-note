## Vue查漏补缺

1、发送请求的几种方式：

- xhr（new XMLHttpRequest()，xhr.open()，xhr.send()）
- jQuery（$get，$post）
- axios（基于promise）
- fetch（与xhr一样同样是在window对象中）
- Vue-resource

2、配置代理

![1654082271443](C:\Users\86180\AppData\Roaming\Typora\typora-user-images\1654082271443.png)

3、插槽

- 默认插槽：组件标签中写内容，组件中用slot标签放置
- 具名插槽：当一个组件中插槽有多个时，需要定义名字，组件标签增加slot属性，值是自定义名字，组件中的slot标签增加name属性，属性值与自定义的属性值一致
- 作用域插槽

4、VueX

​	工作原理：

​	![1654082652604](C:\Users\86180\AppData\Roaming\Typora\typora-user-images\1654082652604.png)

- actions：用于响应组件中的动作
- mutations：用于操作数据
- getters：用于将store中的数据进行加工（计算属性）

​	搭建vuex环境

​		1>创建文件：src/store/index.js

​		![1654083017610](C:\Users\86180\AppData\Roaming\Typora\typora-user-images\1654083017610.png)

​		2>在main.js中创建vm时传入store配置项

​		![1654083116528](C:\Users\86180\AppData\Roaming\Typora\typora-user-images\1654083116528.png)

​	组件中读取vuex中的数据：$store.state.sum

​	修改vuex的数据：$store.dispatch(’action中的方法名‘,数据)，$store.commit('mutations中的方法名',数据)（若没有网络请求或其他业务逻辑，组件中也可以越过action，即不写dispatch，直接commit）

​	VueX优化

- mapState（从state中读取数据）
- mapGetters（从getters中读取数据）
- mapMutations
- mapActions