# 1、vue-router中的导航钩子（ 导航守卫 ）
① 全局前置守卫

② 全局解析守卫

③ 全局后置钩子

④ 路由独享的守卫

⑤ 组件内的守卫
* beforeRouteEnter
* beforeRouteUpdate (2.2 新增)
* beforeRouteLeave

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
① $route是 **路由信息对象**

② $router是 **路由实例**

# 4、vue-router路由的两种模式