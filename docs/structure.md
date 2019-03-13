# 系统结构

以下信息是整个系统的文件结构：

```

- js
  - common / 通用
    - ajax / 封装axios
    - request / 封装所有的请求
    - utils / 通用方法
  - model / Js模型
  - config / 配置
    - router-config / 路由配置
    - heyui-config / heyui配置
    - dict-config / 字典配置
    - tree-config / 树配置
    - autocomplete-config / autocomplete配置
    - category-config / category配置
    - menu-config / 系统菜单配置
  - vue
    - components / 通用组件
    - filters / 通用filters
    - directives / 通用directives
  - vuex
    - store

- css
  - app.less / 系统的所有样式引用
  - common.less / 全局使用的样式
  - frame.less / 系统框架使用的样式
  - fonts / 字体库
  - markdown.less / Markdown插件的样式
  - overwrite.less / 对于组件库样式做自定义覆盖
  - richtext-editor.less / 富文本编辑器
  - var.js / 全局变量定义，提供给vue-cli
  - var.less / 全局变量定义，提供给hey-cli

- components
  - App.vue / 项目入口
  - app / 系统的框架文件
  - common / 系统的通用组件
  - common-item / 系统的通用Item组件，比如业务系统的一些Item展示
  - demo-components / demo组件
  - error-pages / 错误页面
  - home / 首页
  - login / 登录

- images / 系统的一些图片

```