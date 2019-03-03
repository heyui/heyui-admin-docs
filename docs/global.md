# 全局变量

系统对一些基础的调用定义了全局变量，这样就可以在 `js` 或者 `vue` 文件中直接调用。

具体配置请参考脚手架配置。

### Utils
继承扩展hey-utils方法库，可以在 src/js/common/utils 扩展定义公共方法。

hey-utils: [https://www.npmjs.com/package/hey-utils](https://www.npmjs.com/package/hey-utils)

系统中直接调用:

``` javascript
let a = 1;
Utils.isString(a)
// false
```

### HeyUI
heyui组件库  

系统中直接调用:

``` javascript
HeyUI.$Message("成功")
```

### Model
前端数据模型  
js-model：[https://www.npmjs.com/package/js-model](https://www.npmjs.com/package/js-model)

### G
前端全局常量以及全局事件  
hey-global：[https://www.npmjs.com/package/hey-global](https://www.npmjs.com/package/hey-global)


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
引用 src/js/common/request 文件，包含了前端所有的请求定义。

参考`app-frame.vue`文件中，直接引用接口请求

``` javascript
R.User.info().then((resp) => {
  if (resp.ok) {
    //
  }
})
```


`request.js`文件

``` javascript
import Ajax from './ajax';

const Request = {
  User: {
    info(){
      return Ajax.get('/account/info');
    }
  },
  Dict: {
    get(){
      return Ajax.get(`/dict`);
    },
  },
  Home: {
    getMessageList() {
      return Ajax.get(`/home/messages`);
    }
  },
  Login: {
    login(param){
      return Ajax.postJson("/login", param);
    },
    logout(param){
      return Ajax.post("/logout", param);
    }
  }
};

export default Request;
```