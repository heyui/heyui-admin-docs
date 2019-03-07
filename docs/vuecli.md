# vue-cli配置

vue-cli的配置放置在/vue-cli文件夹下，如果选择使用vue-cli，将/vue-cli中的配置文件覆盖根目录即可。

### 启动

```sh
npm run serve
```

### 配置

目前，系统中提供的vue-cli配置如下，如果有其他的扩展配置，请参考vue-cli以及webpack的文档。

vue-cli: https://cli.vuejs.org/

webpack: https://webpack.js.org/

``` javascript
const path = require('path');
const webpack = require('webpack');
const globalVars = require('./src/css/var.js');

module.exports = {
  pages: {
    index: {
      entry: 'src/main.js',
      template: 'index.html',
      filename: 'index.html',
      chunks: ['chunk-vendors', 'chunk-common', 'index']
    }
  },
  css: {
    loaderOptions: {
      // less 设置全局变量，var.js 建议使用less-to-js转换 var.less 文件
      less: {
        globalVars
      }
    }
  },
  configureWebpack: {
    //定义resolve，参考webpack文档 https://webpack.js.org/configuration/resolve/
    resolve: {
      alias: {
        model: path.resolve(__dirname, 'src/js/model/'),
        js: path.resolve(__dirname, 'src/js/'),
        components: path.resolve(__dirname, 'src/components/')
      }
    },
    //定义全局变量, 参考webpack文档 https://webpack.js.org/plugins/provide-plugin
    plugins: [
      new webpack.ProvidePlugin({
        Utils: [path.resolve(__dirname, 'src/js/common/utils'), 'default'],
        Manba: 'manba',
        HeyUI: 'heyui',
        Model: 'js-model',
        G: 'hey-global',
        log: 'hey-log',
        R: [path.resolve(__dirname, 'src/js/common/request'), 'default']
      })
    ]
  },
  devServer: {
    proxy: {
      // 此处应该配置为开发服务器的后台地址
      // '/api': {
      //   target: 'http://xxx.xx.xx'
      // }
    }
  }
};

```