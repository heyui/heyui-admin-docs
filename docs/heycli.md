# hey-cli配置

heyui-admin的默认配置为hey-cli，如果你选择使用hey-cli，需要全局安装 hey-cli

```sh
npm install -g hey-cli
```

### 启动

```sh
npm run serve
```

### 配置

目前，系统中提供的hey-cli配置如下，如果有其他的扩展配置，请参考hey-cli的文档。

https://github.com/heyui/hey-cli

``` javascript
const path = require('path');

module.exports = {
  port: 9012, //端口号
  root: 'dist', //打包的目录
  webpack: {
    console: true, // 打包是否保留日志
    publicPath: '/', //公开path
    output: {
      './index.html': {  //输出哪些文件，主要是html，默认会加载和html文件名一样的js文件为入口。支持定义公用包。
        entry: './src/main',
        commons: ['common']
      }
    },
    commonTrunk: {  //公共包定义，可以定义多个
      common: [
        'babel-polyfill',
        'manba',
        'js-model',
        './src/js/common/utils',
        './src/js/common/request',
        'hey-global',
        'hey-log',
        'heyui',
      ]
    },
    //定义resolve，参考webpack文档 https://webpack.js.org/configuration/resolve/
    alias: {
      model: './src/js/model/',
      js: './src/js/',
      components: './src/components/',
    },
    //定义全局变量, 参考webpack文档 https://webpack.js.org/plugins/provide-plugin
    global: {
      Utils: [path.resolve(__dirname, 'src/js/common/utils'), 'default'],
      Manba: 'manba',
      HeyUI: 'heyui',
      Model: 'js-model',
      G: 'hey-global',
      log: 'hey-log',
      R: [path.resolve(__dirname, 'src/js/common/request'), 'default']
    },
    //定义反向代理服务器，https://webpack.js.org/configuration/dev-server/#devserver-proxy
    devServer: {
      proxy: {
        // 此处应该配置为开发服务器的后台地址
        // '/api': {
        //   target: 'http://xxx.xx.xx'
        // }
      },
      historyApiFallback: true
    },
    globalVars: './src/css/var.less',  //定义全局less参数定义，可以在任意less中使用参数
    externals: {}
  },
  // 未做关联引用的文件在build的时候复制到打包的文件夹中
  copy: ['static/images/*', 'call/*', './baidu_verify_7O2vpVMzwg.html']
};

```