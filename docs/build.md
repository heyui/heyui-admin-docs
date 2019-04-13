# 构建与发布

## 构建之前

构建之前，你需要将系统中的一些配置修改为自己系统的配置。

### index.html

#### 修改header信息

``` html
<title>HeyUI Admin管理平台</title>
<meta name="keywords" content="heyui,hey,ui,vue,es6" />
<meta name="description" itemprop="description" content="HeyUI Admin管理平台" />
```

#### 修改统计信息

index.html 中已经添加了百度统计，你可以按照自己的需求修改统计代码。

``` html
<script>
// baidu 统计

if(window.location.hostname == 'admin.heyui.top'){
  var _hmt = _hmt || [];
  (function() {
    var hm = document.createElement("script");
    hm.src = "https://hm.baidu.com/hm.js?dc337e576ecea81b5da68a42b8e7f75a";
    var s = document.getElementsByTagName("script")[0]; 
    s.parentNode.insertBefore(hm, s);
  })();
}
</script>
```

### router-config

#### 修改titile定义

``` javascript
router.beforeEach((to, from, next) => {
  HeyUI.$LoadingBar.start();
  if (to.meta && to.meta.title) {
    document.title = to.meta.title + ' - 管理应用';
  } else {
    document.title = '管理系统';
  }
  next();
});
```

## 构建

不管使用的是`hey-cli`还是`vue-cli`构建与发布都已经在`package.json`中定义好了，使用相同的命令即可。

最重要的是注意配置publicPath属性，按照系统的需求配置。

```
npm run build
```

### 部署

我们提供了一个简单的nginx配置示例：

``` shell
server {
    listen       80;
    server_name  www.a.com;

    # 开启gzip
    gzip on;
    gzip_min_length 1k;
    gzip_buffers 4 16k;
    gzip_comp_level 2;
    gzip_types text/plain application/javascript application/x-javascript text/css application/xml text/javascript application/x-httpd-php image/jpeg image/gif image/png;
    gzip_vary off;
    gzip_disable "MSIE [1-6]\.";
    
    # 反向代理配置
    location /api {
        proxy_pass http://localhost:8080/api;
        proxy_set_header Host $http_host;
    }
    location / {
        root   /usr/share/nginx/folder;
        # 单页应用都跳转 index.html
        try_files $uri $uri/ /index.html;
        index  index.html index.htm;
    }
}
```
