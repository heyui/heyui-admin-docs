# 快速上手

## 前序准备

本地环境需要安装 `node`、`npm` 和 `git`。

我们的技术栈基于 `ES2015+`、`Vue2.0`、`HeyUI`、`Hey-Cli` ，提前了解和学习这些知识会非常有帮助。

## 安装

从 github 仓库中直接下载最新的 heyui admin 代码。

``` shell
$ git clone --depth=1 https://github.com/heyui/heyui-admin my-project
$ cd my-project
```

## 本地开发

### 使用 hey-cli 脚手架

#### 安装 hey-cli 脚手架

确保本地已经安装 hey-cli 脚手架，并且安装版本 1.13.0+。

如未安装，请执行一下命令

``` shell
$ npm install -g hey-cli
```

hey-cli文档：[https://github.com/heyui/hey-cli](https://github.com/heyui/hey-cli)


#### 1、安装依赖

``` shell
$ npm install
```
#### 2、启动服务


``` shell
$ npm run serve
```

浏览器将自动打开 http://localhost:9012

### 使用 vue-cli 脚手架

Admin 系统也集成了 vue-cli 的配置，按照以下步骤，即可直接使用vue-cli@3.0

#### 1、将vue-cli文件夹下的配置复制至根目录

系统已经将配置都集成完了，所以只需要将配置文件拷贝至根目录即可

#### 2、安装依赖

``` shell
$ npm install
```
#### 3、启动服务


``` shell
$ npm run serve
```