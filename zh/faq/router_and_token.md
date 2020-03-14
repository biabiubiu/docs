# 这是我遇到的一个问题:
![tu](question.gif)

1. 我的自定义router插件代码:
```javascript
export default ({ app }) => {
  app.router.beforeEach((to, from, next) => {
    if (to.path === '/login') return next();

    if (process.client) {
      let t = window.sessionStorage.getItem('token');
      if (!t) {
        next('/login');
        return;
      }
    }

    next();
  });
}

```

2. 在没有获取到token的情况下,我访问其它页面, 会先跳到其它页面,延迟1s左右后,才会跳回/login

3. 请问一下,像这种问题我应该怎么解决?
