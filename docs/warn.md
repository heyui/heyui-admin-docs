# 开发注意事项

## 连接后台配置

如果你开发的前端代码，需要连接自己的后端服务，请按照以下步骤进行修改：

### 删除本地mock服务

`HeyUI Admin` 的代码是直接开启了本地Mock的，所以第一步将本地mock服务关闭。

所以，请屏蔽或者删除 `app.js` 文件中的以下代码。

``` javascript
// 使用mock文件， 自己开发的时候请删除
require('./mock')
```
### 一、配置反向代理地址

打开 `hey.conf.js` 文件，参考给出的示例，配置出devServer。

``` javascript
devServer: {
  proxy: {
    // 此处应该配置为开发服务器的后台地址
    '/api': {
      target: 'http://xxx.xx.xx'
    }
  },
  // 开启单页应用
  historyApiFallback: true
}

```
注意： 后台的服务最好是以`/api`前缀开始

### 重启启动

由于修改了`hey.conf.js`配置文件，请重新启动服务。

## 二、页面加载Api控制

这个时候，重启刷新页面后，页面会一直处于loading的状态。

这是由于 HeyUI Admin 系统已经将获取用户信息以及字典的规则写好了，有可能后端还没有提供这些接口，或者接口不一致。

打开  `app-frame.vue` 文件

### 如果后端已经提供相关的接口


