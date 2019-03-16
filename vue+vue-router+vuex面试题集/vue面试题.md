# 1、对于MVVM的理解
**MVVM 是Model-View-ViewModel的缩写**  
**Model** 代表数据模型，可以在Model中定义数据修改和操作的业务逻辑  
**View** 代表UI组件，负责将数据模型转化成UI展现出来  
**ViewModel** 监听模型数据的改变和控制视图行为、处理用户交互，用来连接Model和View

# 2、vue的生命周期
**beforeCreate（创建前）** 初始化实例后 数据观测和事件配置之前调用  
**created（创建后）** 实例创建完成后调用   
**beforeMount（载入前）** 挂载开始前被用  
**mounted（载入后）** el被新建vm.$el替换并挂在到实例上之后调用  
**beforeUpdate（更新前）** 数据更新时调用  
**updated（更新后）** 数据更改导致的DOM重新渲染后调用  
**beforeDestroy（销毁前）** 实例被销毁前调用  
**destroyed（销毁后）** 实例销毁后调用

① 什么是vue的生命周期？
> vue实例从创建到销毁的过程，就是生命周期。从开始创建、初始化数据、编译模块、挂载DOM到渲染、更新DOM到渲染、销毁等一系列过程，称为vue的生命周期

② vue生命周期的作用是什么？
> vue的生命周期中有多个事件钩子，让我们在控制整个vue实例的过程时更容易形成好的逻辑

③ vue的生命周期总共有几个阶段？
> 总共分为8个阶段：创建前/创建后，载入前/载入后，更新前/更新后，销毁前/销毁后

④ 第一次页面加载会触发哪几个钩子？
> beforeCreate，created，beforeMount，mounted

⑤ dom渲染在哪个生命周期完成
> dom渲染在mounted中完成

# 3、vue实现数据双向绑定的原理
vue实现数据双向绑定主要是：采用数据劫持结合发布者-订阅者模式的方式，通过Object.defineProperty（）来劫持各个属性的setter，getter，在数据变动时发布消息给订阅者，触发相应监听回调。当把一个普通 Javascript 对象传给 Vue 实例来作为它的 data 选项时，Vue 将遍历它的属性，用 Object.defineProperty 将它们转为 getter/setter。用户看不到 getter/setter，但是在内部它们让 Vue 追踪依赖，在属性被访问和修改时通知变化。

vue的数据双向绑定 将MVVM作为数据绑定的入口，整合Observer，Compile和Watcher三者，通过Observer来监听自己的model的数据变化，通过Compile来解析编译模板指令（vue中是用来解析 {{}}），最终利用watcher搭起observer和Compile之间的通信桥梁，达到数据变化 —>视图更新；视图交互变化（input）—>数据model变更双向绑定效果。

# 4、vuejs的两个核心是什么？
数据驱动和组件系统

# 5、vue组件间的参数传递
① 父组件与子组件传值
> 父组件传给子组件：子组件通过props方法接受数据  
> 子组件传给父组件：$emit方法传递参数

② 非父子组件间的数据传递，兄弟组件传值
> eventBus，创建一个事件中心，相当于中转站，可以用它来传递事件和接收事件

# 6、vue常用的事件修饰符
**prevent** 提交事件不再重载页面  
**stop** 阻止单击事件冒泡  
**self** 当事件发生在该元素本身而不是子元素的时候会触发  
**capture** 事件侦听，事件发生的时候会调用
**once** 事件将只会触发一次

# 7、vue中子组件调用父组件的方法
第一种方法是直接在子组件中通过this.$parent.event来调用父组件的方法  
第二种方法是在子组件里用$emit向父组件触发一个事件，父组件监听这个事件  
第三种是父组件把方法传入子组件中，在子组件里直接调用这个方法

# 8、vue如何监听键盘事件中的按键？
在vue中，已经为常用的按键设置了别名，这样我们就无需再去匹配keyCode，直接使用别名就能监听按键的事件，且vue中还支持组合写法  
`<input @keyup.enter="function">`
别名|实际键值
:--|:--:
.delete|delete（删除）/BackSpace（退格）
.tab|Tab
.enter|Enter（回车）
.esc|Esc（退出）
.space|Space（空格键）
.left|Left（左箭头）
.up|Up（上箭头）
.right|Right（右箭头）
.down|Down（下箭头）
.ctrl|Ctrl
.alt|Alt
.shift|Shift
.meta|(window系统下是window键，mac下是command键)
.alt.67|Alt + C（组合写法）

# 9、vue更新数组时触发视图更新的方法
参考博客 [vue数组对象修改触发视图更新](https://www.cnblogs.com/mengff/p/8482867.html)

# 10、什么是vue的计算属性？
在模板中放入太多的逻辑会让模板过重且难以维护，计算属性里可以完成各种复杂的逻辑，包括运算、函数调用等，只要最终返回一个结果就可以且可以重复调用，计算属性的好处如下：  

① 使得数据处理结构清晰  
② 依赖于数据，数据更新，处理结果自动更新  
③ 计算属性内部this指向vm实例  
④ 在template调用时，直接写计算属性名即可  
⑤ 常用的是getter方法，获取数据，也可以使用set方法改变数据  
⑥ 相较于methods，不管依赖的数据变不变，methods都会重新计算，但是依赖数据不变的时候computed从缓存中获取，不会重新计算。

# 11、v-if和v-show的区别
v-if按照条件是否渲染，v-show是display的block或none

# 12、v-on可以绑定多个方法吗？
可以绑定多个方法  
`<input v-on:keyup.enter="submit" v-on:focus="onFocus">`


