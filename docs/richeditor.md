# 富文本编辑器

基于 wangeditor v3.1.1。

wangeditor: http://www.wangeditor.com/

富文本编辑器组件定义文件位置：

> src/components/common/richtext-editor.vue

## 组件说明

### richtext-editor.vue

主要是引用定义wangeditor。

props:
  - value: v-modal绑定的value。
  - type: 编辑的类型，html, text。
  - cache: 是否开启本地存储

方法:
  - setHtml: 更新html。

更多详细信息请参考 [wangeditor 的 API 文档](https://www.kancloud.cn/wangfupeng/wangeditor3/332599)。

## 全局定义

在文件`src/js/components.js`文件中：

``` javascript
Vue.component('RichTextEditor', (resolve) => require(['components/common/richtext-editor'], resolve));
```

如上所示，系统将全局定义 RichTextEditor 组件，并且定义为异步组件，这将意味着，只有调用 RichTextEditor 组件的时候，代码才会加载。

## 调用

``` html
<RichTextEditor v-model="value"></RichTextEditor>
```

更多的实例代码请参考：

> src/components/demo-components/components/richtext-editor.vue