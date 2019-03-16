# 1、对于MVVM的理解
**MVVM是Model-View-ViewModel的缩写**  
**Model** 代表数据模型，可以在Model中定义数据修改和操作的业务逻辑  
**View** 代表UI组件，负责将数据模型转化成UI展现出来  
**ViewModel** 监听模型数据的改变和控制视图行为、处理用户交互，用来连接Model和View

# 2、vue的生命周期
**beforeCreate（创建前）**  
**created（创建后）**  
**beforeMount（载入前）**  
**mounted（载入后）**  
**beforeUpdate（更新前）**  
**updated（更新后）**  
**beforeDestroy（销毁前）**  
**destroyed（销毁后）**

1)、什么是vue的生命周期？
> vue实例从创建到销毁的过程，就是生命周期。从开始创建、初始化数据、编译模块、挂载DOM到渲染、更新DOM到渲染、销毁等一系列过程，称为vue的生命周期

2)、vue生命周期的作用是什么？
> vue的生命周期中有多个事件钩子，让我们在控制整个vue实例的过程时更容易形成好的逻辑

3)、vue的生命周期总共有几个阶段？
> 总共分为8个阶段：创建前/创建后，载入前/载入后，更新前/更新后，销毁前/销毁后

4)、第一次页面加载会触发哪几个钩子？
> beforeCreate，created，beforeMount，mounted

5)、dom渲染在哪个生命周期完成
> dom渲染在mounted中完成

# 3、vue实现数据双向绑定的原理
vue实现数据双向绑定主要是：采用数据劫持结合发布者-订阅者模式的方式，通过Object.defineProperty（）来劫持各个属性的setter，getter，在数据变动时发布消息给订阅者，触发相应监听回调。当把一个普通 Javascript 对象传给 Vue 实例来作为它的 data 选项时，Vue 将遍历它的属性，用 Object.defineProperty 将它们转为 getter/setter。用户看不到 getter/setter，但是在内部它们让 Vue 追踪依赖，在属性被访问和修改时通知变化。

vue的数据双向绑定 将MVVM作为数据绑定的入口，整合Observer，Compile和Watcher三者，通过Observer来监听自己的model的数据变化，通过Compile来解析编译模板指令（vue中是用来解析 {{}}），最终利用watcher搭起observer和Compile之间的通信桥梁，达到数据变化 —>视图更新；视图交互变化（input）—>数据model变更双向绑定效果。

# 4、vue组件间的参数传递
 1)、父组件与子组件传值
> 父组件传给子组件：子组件通过props方法接受数据  
> 子组件传给父组件：$emit方法传递参数

2)、非父子组件间的数据传递，兄弟组件传值
> eventBus，创建一个事件中心，相当于中转站，可以用它来传递事件和接收事件

# 5、vue常用的修饰符
**prevent** 提交事件不再重载页面  
**stop** 阻止单击事件冒泡  
**self** 当事件发生在该元素本身而不是子元素的时候会触发  
**capture**  事件侦听，事件发生的时候会调用
