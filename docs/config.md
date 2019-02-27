# 系统参数配置

```
- config / 配置
  - router-config / 路由配置
  - heyui-config / heyui配置
  - dict-config / 字典配置
  - autocomplete-config / autocomplete配置
  - category-config / category配置
  - tree-config / 树配置
  - menu-config / 系统菜单配置
```


## heyui配置

``` javascript

// 定义系统的字典
const staticDict = dictConfig();
Object.keys(staticDict).forEach((key) => {
  HeyUI.addDict(key, staticDict[key])
});

// 定义全局的字典结构，请根据系统的设计设置
HeyUI.config('dict.keyName', "key");
HeyUI.config('dict.titleName', "title");

// 设置系统中的 autocomplete, tree, category 配置，系统中可以直接使用config引用
HeyUI.config("autocomplete.configs", autocompleteConfig());
HeyUI.config("tree.configs", treeConfig());
HeyUI.config("category.configs", categoryConfig());

// 定义 menu 组件的基础参数
HeyUI.config('menu', {
  keyName: 'key',
  titleName: 'title',
  childrenName: 'children'
});
```

tree-config, menu-config, autocomplete-config, category-config 请参考 heyui 官方文档。


## 路由配置

路由使用的是官方的： `vue-router`

vue-router 相关文档：[https://router.vuejs.org/zh](https://router.vuejs.org/zh/)

### Router定义

路由主要是定义系统中的所有router，目前系统中定义的都是异步加载的，建议系统主要的页面直接引用。

``` javascript
import Login from 'components/home/index';

{
  path: '/home',
  name: 'Home',
  // 异步加载
  component: (resolve) => require(['components/home/index'], resolve),
  // 直接引用
  component: Login,
  meta: {title: '首页', icon: 'icon-monitor'}
}
```


### Router 事件定义

``` javascript
router.beforeEach((to, from, next) => {
  HeyUI.$LoadingBar.start();
  // 自定义title，根据 router 中定义的meta 来更新
  if (to.meta && to.meta.title) {
    document.title = to.meta.title + ' - 管理应用';
  } else {
    document.title = '管理系统';
  }
  next();
})
router.afterEach(() => {
  HeyUI.$LoadingBar.success();
  // 页面的滚动置顶
  document.documentElement.scrollTop = 0;
  document.body.scrollTop = 0;
  // baidu 统计，如果有自己的统计，请至index.html修改至自己的埋点
  if( window._hmt) {
    window._hmt.push(['_trackPageview', window.location.pathname]);
  }
});
```

### 配合webpack

``` javascript
devServer: {
  // 需要开启historyApiFallback
  historyApiFallback: true
},
```
