# 1、vue-router中的导航钩子（ 导航守卫 ）
> 详情查看官网 [导航守卫](https://router.vuejs.org/zh/guide/advanced/navigation-guards.html)

① 全局前置守卫
* 可以使用 router.beforeEach 注册一个全局前置守卫，每个守卫方法接收三个参数
    * `to`：Route：即将进入的目标路由对象
    * `from`：Route: 当前导航正要离开的路由
    * `next`：Function：一定要调用该方法resolve这个钩子。执行效果依赖next方法的调用参数。可以控制路由的跳转
        * `next()`: 进行管道中的下一个钩子。如果全部钩子执行完了，则导航的状态就是 confirmed (确认的)
        * `next(false)`: 中断当前的导航。如果浏览器的 URL 改变了 (可能是用户手动或者浏览器后退按钮)，那么 URL 地址会重置到 from 路由对应的地址
        * `next('/')` 或者 `next({ path: '/' })`: 跳转到一个不同的地址。当前的导航被中断，然后进行一个新的导航。你可以向 next 传递任意位置对象，且允许设置诸如 replace: true、name: 'home' 之类的选项以及任何用在 router-link 的 to prop 或 router.push 中的选项
        * `next(error)`: (2.4.0+) 如果传入 next 的参数是一个 Error 实例，则导航会被终止且该错误会被传递给 router.onError() 注册过的回调


② 全局解析守卫 `router.beforeResolve`

③ 全局后置钩子 `router.afterEach`，不会接受 next 函数也不会改变导航本身
```
router.afterEach((to, from) => {
  // ...
})
```
④ 路由独享的守卫 `beforeEnter`，与全局前置守卫的方法参数是一样的
```
router.afterEach((to, from, next) => {
  // ...
})
```

⑤ 组件内的守卫
* beforeRouteEnter
    * 在渲染该组件的对应路由被 confirm 前调用
    * 不能访问组件实例 `this`，因为当守卫执行前，组件实例还没被创建
* beforeRouteUpdate (2.2 新增)
    * 在当前路由改变，但是该组件被复用时调用
    * 举例来说，对于一个带有动态参数的路径 /foo/:id，在 /foo/1 和 /foo/2 之间跳转的时候，由于会渲染同样的 Foo 组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用
    * 可以访问组件实例 `this`
* beforeRouteLeave
    * 导航离开该组件的对应路由时调用
    * 可以访问组件实例 `this`

# 2、完整的导航解析流程
> 详情查看官网 [完整的导航解析流程](https://router.vuejs.org/zh/guide/advanced/navigation-guards.html#%E7%BB%84%E4%BB%B6%E5%86%85%E7%9A%84%E5%AE%88%E5%8D%AB)
1. 导航被触发。
2. 在失活的组件里调用离开守卫。
3. 调用全局的 beforeEach 守卫。
4. 在重用的组件里调用 beforeRouteUpdate 守卫 (2.2+)。
5. 在路由配置里调用 beforeEnter。
6. 解析异步路由组件。
7. 在被激活的组件里调用 beforeRouteEnter。
8. 调用全局的 beforeResolve 守卫 (2.5+)。
9. 导航被确认。
10. 调用全局的 afterEach 钩子。
11. 触发 DOM 更新。
12. 用创建好的实例调用 beforeRouteEnter 守卫中传给 next 的回调函数。

# 3、$route和$router的区别
① $route是 **路由信息对象**，包括path，params，hash，query，fullPath，matched，name等路由信息参数

② $router是 **路由实例**，包括了路由的跳转方法，钩子函数等

# 4、vue-router路由的两种模式
* hash 模式（默认）
* history 模式