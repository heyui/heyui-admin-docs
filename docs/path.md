# 路径别名

系统对一些基础的路径定义了别名，这样就可以文件中直接调用。

具体配置请参考脚手架配置。

### js

定义为：`src/js/`

系统中直接调用:

``` javascript
import dictConfig from 'js/config/dict-config';
```
### components

定义为：`src/components/`

系统中直接调用:

``` javascript
import AccountInfoShow from 'components/demo-components/modules/account-info-show';
```
### model

定义为：`src/js/model`

系统中直接调用:

``` javascript
import Login from 'model/login/Login';
```

如果你需要再添加其他的路径别名，请参考脚手架的文档，自行配置。