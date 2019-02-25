# 全局变量

系统对一些基础的调用定义了全局变量，这样就可以在 `js` 或者 `vue` 文件中直接调用。

### Utils
继承扩展hey-utils方法库，可以在 src/js/common/utils 定义公共方法

js中可以直接调用:

``` javascript
let a = 1;
Utils.isString(a)
// false
```

### HeyUI
heyui组件库  

js中可以直接调用:

``` javascript
HeyUI.$Message("成功")
```

### Model
前端数据模型，js-model  
相关文档：[https://www.npmjs.com/package/js-model](https://www.npmjs.com/package/js-model)

### G
前端全局常量以及全局事件，hey-global  
相关文档：[https://www.npmjs.com/package/hey-global](https://www.npmjs.com/package/hey-global)


``` javascript
G.set('env', {
  fileOs: 'http://www.download.com',
  socketOs: 'ws://www.socket.com',
});

// 获取环境变量
const env = G.get('env');
// {
//   fileOs: 'http://www.download.com',
//   socketOs: 'ws://www.socket.com',
// }

let todoTrigger = G.addlistener('NEW_TODO', (data)=>{
  console.log(`new todo: ${date.message}`)
});

G.trigger('NEW_TODO', {message: 'go home'});
// new todo: go home
```


### log
简写console.log -> log，hey-log

``` javascript
log('打印日志')
```

### R
src/js/common/request 文件，前端所有的请求定义。

参考`app-frame.vue`文件中，直接引用接口请求

``` javascript
R.User.info().then((resp) => {
  if (resp.ok) {
    //
  }
})
```