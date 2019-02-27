# 样式

```
- css
  - app.less / 系统的所有样式引用
  - common.less / 全局使用的样式
  - frame.less / 系统框架使用的样式
  - fonts / 字体库
  - markdown.less / Markdown插件的样式
  - overwrite.less / 对于组件库样式做自定义覆盖
  - richEditor.less / 富文本编辑器
  - var.js / 全局变量定义，提供给vue-cli
  - var.less / 全局变量定义，提供给hey-cli
```

## 组件库主题 / 全局变量

### hey-cli

如果你使用的是hey-cli脚手架，可以通过修改  `var.less` 自定义主题。

如果是更加细化的调整，建议在 `overwrite.less` 文件中，对样式进行覆盖。

### vue-cli

如果你使用的是vue-cli脚手架，可以通过修改  `var.js` 自定义主题。

由于系统 var.less 中存在一系列的继承，并且js的可读性很差，所以还是建议修改 `var.less` 文件，然后使用 `less-to-js` 工具转换成 `var.js` 文件


``` shell
$ npm install -g less-to-js
$ cd src/css
$ lesstojs var.less > var.js

```

如果是更加细化的调整，建议在 `overwrite.less` 文件中，对样式进行覆盖。

## 自定义样式

如果你还需要做更多的样式定义，建议新增less文件，并在app.less中引用。

例：自定义Form附加样式

在 css 文件夹中新增 form.less 文件

``` css
.form-section {
  .fort-section-title {

  }
}
```

在 app.less 中引入 form.less 文件

``` css
@import (less) "./form.less";
```



