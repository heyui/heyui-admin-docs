# 系统命名规则

## 命名类型
总共有三种命名方式：
- PascalCase: 大写驼峰式，比如：`MyClass`
- camelCase: 小写驼峰式，比如：`myClass`
- kebab-case: 小写短横线，比如：`my-class`

## 命名原则
文件或文件夹的命名遵循以下原则：

- 定义类的，统一使用PascalCase(大写驼峰式)命名规范，比如model文件夹中的数据模型定义
- 文件夹统一使用kebab-case(小写短横线)命名规范
- 其他组件或类的，统一使用kebab-case(小写短横线)命名规范

基本原则就是大多数文件以及文件夹都使用kebab-case(小写短横线)命名规范。

## Why?

为什么除了前端数据模型，我们都使用kebab-case(小写短横线)命名规范？

第一，使用kebab-case命名的文件夹比camelCase命名的文件夹看起来更清晰

第二，不同的操作系统对于文件名的大小写处理方式不一致，我们出现很多次本地开发正常，发布失败的情况。

## 文件夹命名规范

文件夹全部使用kebab-case(小写短横线)命名规范。

其实，前期我们在通用组件定义的时候，全部使用的是PascalCase(大写驼峰式)命名规范的。

```
- src / components
  - common
    - SubMenu.vue
    - SysTabs
      - index.js
      - sysTabs.vue
      - utils.js
```

类似上图，会同时存在 `SysTabs`文件夹、 `index.js`、 `sysTabs.vue` 这三种命名规范放在一起，看起来很奇怪。

所以，我们将通用组件也使用kebab-case(小写短横线)命名规范。

```
- src / components
  - common
    - sub-menu.vue
    - sys-tabs
      - index.js
      - sys-tabs.vue
      - utils.js
```

但是针对调用方便的情形，我们在`src/js/vue/components.js`中定义通用组件的时候，使用 PascalCase(大写驼峰式) 命名规范。

``` javascript
import SubMenu from 'components/common/sub-menu';
import SearchFilter from 'components/common/search-filter';

Vue.component('SubMenu', SubMenu);
Vue.component('SearchFilter', SearchFilter);
Vue.component('Qiniu', (resolve) => require(['components/common/qiniu'], resolve));
```


## 文件命名规范

### *.js文件命名规范

除了 `src/js/model` 中的数据模型定义，其他地方都使用kebab-case(小写短横线)命名规范。

> 注意：model中的文件夹也应该使用kebab-case(小写短横线)命名规范。

### *.vue文件命名规范

统一使用kebab-case(小写短横线)命名规范。

### *.less文件命名规范

统一使用kebab-case(小写短横线)命名规范。