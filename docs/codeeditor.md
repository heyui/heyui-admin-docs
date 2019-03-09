# 代码编辑器

基于 brace v0.11.1，本身基于ace编辑器。

brace: https://github.com/thlorenz/brace

ace: https://ace.c9.io/

代码编辑器组件定义文件位置：

> src/components/common/code-editor

## 组件说明

### code-editor.vue

主要是引用定义brace。

``` javascript
this.editor = ace.edit(this.$el);
```

### props

主要props:

- mode: 代码种类，比如：java, javascript, sql, markdown
- value: v-model绑定的value

其他参考props文件：

> src/components/common/code-editor/props.js


## 全局定义

在文件`src/js/components.js`文件中：

``` javascript
Vue.component('CodeEditor', (resolve) => require(['components/common/code-editor'], resolve));
```

如上所示，系统将全局定义 CodeEditor 组件，并且定义为异步组件，这将意味着，只有调用 CodeEditor 组件的时候，代码才会加载。

## 调用

``` html
<CodeEditor v-model="value" :mode="mode"/>
```

更多的实例代码请参考：

> src/components/demo-components/components/code-editor.vue