# 数据请求封装

系统的所有请求都封装在 request.js 文件中，而 request.js 中调用的方法都使用的 ajax.js 封装。

## ajax.js

### 方法

- get(url, param, extendParam)
- post(url, param, extendParam)
- postJson(url, param, extendParam)
- patchJson(url, param, extendParam)
- delete(url, extendParam)

### 防止重复请求机制

除了get方法，其他方法都已经添加了去除重复请求的机制。

``` javascript
if (this.isRequesting(url)) {
  return new Promise((resolve, reject) => { reject(new Error('This request is requesting')); });
}
```

该机制可以让开发人员在表单提交的时候，不需要做特殊的防止重复请求的处理。

如果你确定一个请求可以重复请求，比如说，复杂的搜索使用post请求，可以传递 extendParam = {repeatable: true}

``` javascript
search(params) {
  return Ajax.postJson(`/search/project`, params, {repeatable: true});
}
```

### 返回结果封装

所有的请求结果都是统一封装，所以在调用请求方法的时候，不需要添加catch处理。

统一封装的结构为：

``` javascript
{
  ok: true,
  body: {},
  meta: {},
  msg: ''
}
```

接口的一些报错将做统一的处理：

``` javascript
return new Promise((resolve) => {
  return axios.request(params).then((response) => {
    that.deleteRequest(params.url);
    let data = response.data;
    let status = response.status;
    // 如果后端统一封装返回，即所有的请求都是200, 错误码由返回结果提供，则使用以下代码获取状态
    // if (status == 200) {
    //   status = data.status;
    // }
    if (status != 200) {
      if (status == 401) {
        window.top.location = '/login';
        return;
      }
      if (status == 500) {
        HeyUI.$Message.error('后台异常');
      } else if (status == 404) {
        HeyUI.$Message.error('请求不存在');
      } else if (status != 200) {
        HeyUI.$Message.error(data._msg || '请求异常');
      }
    }
    data.ok = data.status == 200;
    resolve(data);
  }).catch(() => {
    that.deleteRequest(params.url);
    resolve({
      ok: false
    });
  });
});
```

## request.js

### 定义

``` javascript
import Ajax from './ajax';

const Request = {
  // 定义模块
  User: {
    // 模块下面的方法
    info() {
      return Ajax.get('/account/info');
    }
  }
};

export default Request;
```

### 请求调用

request.js 已经定义为全局变量 R，所以可以直接调用：

``` javascript
R.User.info().then((resp) => {
  if (resp.ok) {
    // 执行代码
    this.$Message.success('保存成功');
  }
  // 无论结果成功或者失败，都执行的代码
  this.loading = false;
});
```
