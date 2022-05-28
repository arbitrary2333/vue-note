## Vue查漏补缺

1、虚拟DOM中key的作用：

​	key是虚拟DOM对象的标识，当数据发生变化时，Vue会根据新数据生成新的虚拟DOM，随后Vue进行新旧虚拟DOM的差异比较

2、用index作为key可能会引发的问题

​	1>若对数据进行：逆序增加、逆序删除等破坏顺序的操作

​			会产生没有必要的真实DOM更新==>界面效果没问题，但效率低

​	2>如果结构中还包含输入类DOM（input输入框）

​			会产生错误DOM更新==>界面有问题

3、vue更新时的一个问题

​	对对象的监听，通过事件将属性值修改成对象

4、Vue监测数据的原理

​	data==>_data的过程：vue底层封装了Observer(观察者)构造函数，Observer为封装的Object.defineproperty()，将data对象中的内容递归进行调用defineproperty方法，对对象与数组均有效果

​	data==>加工data（实例化Observer）==>vm._data = data

```javascript
let data = {
    name: "LLH",
    age: 23
}
//创建一个监视的实例对象，用于监视data中属性的变化
let obs = new Observer(data)
//准备一个vm实例对象
let vm = {}
//多等为将obs赋值给前面所有的变量
vm._data = data = obs
function Observer(obj){
    let keys = Object.keys(obj)
    keys.forEach((k) => {
        Object.defineProperty(this, k, {
            get(){
                return obj[k]
            },
            set(val){
                obj[k] = val
            }
        })
    })
}
```

5、Vue.set(target, property, value)或this.$set()

​	向响应式对象中添加一个property，并确保这个新的property同样是响应式，且触发视图更新

​	注意：对象不能是vue实例或者vue中的data