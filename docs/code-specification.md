# 单文件开发规范

## css开发规范

在每个vue文件中，我们都会编写css样式，admin系统集成的是less。

### 关闭scope模式

vue提供了scope模式以及普通模式。

我们建议开发人员关闭scope模式，严格按照html结构定义css。

不开启scope模式的理由如下：

#### 一、scope模式会让开发人员容易编写css不规范，因为scope会帮开发人员把范围缩小。

``` html
<style lang="less" scoped>
.title {
  
}
</style>
```
如上图所示，开发人员在css定义上非常随意，如果忘记添加`scoped`属性，会导致样式覆盖其他模块的样式。

#### 二、无法覆盖vue文件引用的组件样式。

有时候我们需要对引入的组件样式做出微调，如果使用 `scoped` 模式将无法修改引入的组件样式。

### 开发规范

在单文件的根目录dom上定义和文件名一致的css，并添加 `-vue` 或者 `-page` 后缀。

以account-info.vue为例：
``` html
<style lang='less'>
.account-info-vue {}
</style>
<template>
  <div class="account-info-vue">
  </div>
</template>
```

添加 `-vue` 后缀主要是为了防止和其他css命名冲突，如果命名为 `account-info`，则有可能和其他组件内的用户信息展示css命名重叠。

## template开发规范

template开发并没有太多的注意事项，大致遵守一下几条即可：

#### 所有的v-for都需要添加key属性

由于 vue2.0 的设计模式，所有的v-for都需要添加key属性，如果没有添加，有可能会产生无法预料的bug。

原则上，同一层级的相同组件也需要添加key属性。


#### 子组件引用使用PascalCase(大写驼峰式)命名规范

``` html
<AccountInfoEdit v-if="tab == 'info'" :account="account"></AccountInfoEdit>

import AccountInfoEdit from './modules/account-info-edit';
```

## js开发规范

#### props定义一定要使用对象模式，如果复杂的参数，需要添加注释。

``` javascript
export default {
  props: {
    account: Object,
    // 是否可以通过点击用户名打开详情
    openLink: {
      type: Boolean,
      default: false
    }
  },
}
```


