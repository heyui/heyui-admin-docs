# eslint与编辑器插件

## HeyUI开发插件

推荐用户安装heyui组件库开发插件：

heyui-snippets: [HeyUI开发插件](https://marketplace.visualstudio.com/items?itemName=vvpvvp.heyui-snippets)

## eslint

heyui-admin系统已经配置好了eslint的标准，如果你对标准有其他的要求，可以修改`.eslintrc.js`文件。

### 如何使用？

下载好项目后，在根目录中执行 `npm install` 即可开启。

主要为以下几个依赖包：

``` 
"@vue/eslint-config-standard": "^4.0.0",
"babel-eslint": "^10.0.1",
"eslint": "^5.3.0",
"eslint-plugin-html": "^5.0.3",
"eslint-plugin-import": "^2.16.0",
"eslint-plugin-vue": "^5.2.2",

```

## 编辑器

推荐使用vscode编辑器。

主要是 heyui-admin 系统主要是通过 vscode 编辑器编辑的，如果有什么问题，可以直接沟通解决。

系统配置了`vscode`的编辑配置，具体可以参考 `.vscode/settings.json` 文件。

> settings.json 中已经开启了 eslint.autoFixOnSave 配置，所以保存的时候会对文件执行一次 eslint fix。

## 文件格式化插件

推荐用户安装一下插件：

Vetur: [vue编辑插件](https://marketplace.visualstudio.com/items?itemName=octref.vetur)

ESlint: [eslint插件](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

Prettier - Code formatter: [代码格式化工具，vetur内置格式化工具](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)


系统已经针对这两种插件做好配置，详细配置请参考 `.prettierrc.js`, `.vscode/settings.json` 文件。

### 格式化标准

系统已经将文件格式化的标准与eslint的标准保持一致了，所以，当你对文件做完格式化的时候，文件将符合eslint要求的标准。

`editor.formatOnSave` 暂时未开启，你可以按照你的开发需求在 `.vscode/settings.json` 中修改此配置。
