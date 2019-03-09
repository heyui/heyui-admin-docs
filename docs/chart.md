# 图表组件

基于 ECharts v4.1.0+ 。

echarts: https://www.echartsjs.com/

图表组件定义文件位置：

> src/components/common/chart

## 组件说明

### 入口文件

index.js

``` javascript
import ECharts from './echarts';

require('echarts/lib/chart/line');
require('echarts/lib/chart/pie');
require('echarts/lib/chart/radar');
require('echarts/lib/chart/bar');
require('echarts/lib/component/tooltip');

export default ECharts;
```

如上所示，图表组件并不是加载所有的组件，只使用了几个简单的图表，这样引用能够减小组件的大小。

### echart.vue

主要是引用定义echart，以及自定义完成的主题theme。

props:
  - initOptions: 用来初始化 ECharts 实例。
  - options: ECharts 实例的数据。修改这个 prop 会触发 ECharts 实例的 setOption 方法。
  - group: 实例的分组，会自动绑定到 ECharts 组件的同名属性上。
  - autoresize: 这个 prop 用来指定 ECharts 实例在组件根元素尺寸变化时是否需要自动进行重绘。

方法:
  - mergeOptions: 提供了一个更贴切的名称来描述 setOption 方法的实际行为。
  - appendData
  - resize
  - dispatchAction
  - showLoading
  - hideLoading
  - convertToPixel
  - convertFromPixel
  - containPixel
  - getDataURL
  - getConnectedDataURL
  - clear
  - dispose

更多详细信息请参考 [ECharts 的 API 文档](https://www.echartsjs.com/api.html#echarts)。

### 主题

系统已经提供了一个完整的主题文件：

> src/components/common/chart/theme.js

如果你需要自定义主题的话，请至 ECharts 官网进行配置生成。

## 全局定义

在文件`src/js/components.js`文件中：

``` javascript
Vue.component('Chart', (resolve) => require(['components/common/chart'], resolve));
```

如上所示，系统将全局定义 Chart 组件，并且定义为异步组件，这将意味着，只有调用Chart组件的时候，代码才会加载。

## 调用

``` html
<Chart :options="data2"></Chart>
```

更多的实例代码请参考：

> src/components/demo-components/components/chart.vue