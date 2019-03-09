# Markdown组件

基于CodeEditor组件做的封装 。

组件定义文件位置：

> src/components/common/markdown-editor

## 组件说明

### markdown-editor.vue

主要是引用了code-editor，以及实时更新展示了生成的html。

props:
  - value: v-modal绑定的value。
  - readonly： 是否展示只读

## 全局定义

在文件`src/js/components.js`文件中：

``` javascript
Vue.component('MarkdownEditor', (resolve) => require(['components/common/markdown-editor'], resolve));
```

如上所示，系统将全局定义 MarkdownEditor 组件，并且定义为异步组件，这将意味着，只有调用 MarkdownEditor 组件的时候，代码才会加载。

## 调用

``` html
<MarkdownEditor v-model="value" :options="data2"></MarkdownEditor>
```

更多的实例代码请参考：

> src/components/demo-components/components/markdown-editor.vue