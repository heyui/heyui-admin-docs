# 百度地图

基于百度地图的API做的封装 。

组件定义文件位置：

> src/components/common/baidu-map

## 组件说明

### load.js

主要是针对baidu地图的js文件引用，这里做了load的处理，所以只有当使用百度地图的组件时，js才会做加载动作。

``` javascript
export default function() {
  return new Promise(function (resolve, reject) {
    var script = document.createElement("script");
    script.type = "text/javascript";
    script.src = `//api.map.baidu.com/getscript?v=2.0&ak=20qOZbvLhZnFinXiG1NfGPLC&t=${new Date().getTime()}`;
    script.onerror = reject;
    document.head.appendChild(script);
    script.onload = () => {
      resolve();
    }
  })
}
```

### baidu-map.vue

这里主要做两个动作：
- 加载百度的javascript代码
- 初始化map实例，并通过load事件传递回组件。

**加载api会首先判断是否已经加载完毕，防止重复加载**

``` javascript
mounted() {
  if (typeof BMap != 'undefined') {
    this.init();
  } else {
    load().then(resp => {
      this.init();
    });
  }
},
```
**初始化map实例，这里由于地图的使用方式非常多种，所以不做任何处理，直接load事件回去，让调用的地方做地图的处理**

``` javascript
init() {
  this.$nextTick(() => {
    let map = new BMap.Map(this.$el);
    this.$emit('load', map);
  });
}
```

#### props

原则上，地图的宽度应该根据父层的宽度自适应，所以只提供了一个传递一个height的参数

- height: 地图的高度


## 全局定义

在文件`src/js/components.js`文件中：

``` javascript
Vue.component('BaiduMap', (resolve) => require(['components/common/baidu-map'], resolve));
```

如上所示，系统将全局定义 BaiduMap 组件，并且定义为异步组件，这将意味着，只有调用 BaiduMap 组件的时候，代码才会加载。

## 调用

``` html
<BaiduMap @load="initMap"></BaiduMap>
```

更多的实例代码请参考：

> src/components/demo-components/components/baidu-map.vue