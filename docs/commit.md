# git commit 规范

本项目 git commit 目前是遵守 Angular 规范。

标准格式如下：

```
<type>(<scope>): <subject> #header
// 空一行
<body>
// 空一行
<footer>
```

> Header 是必需的，Body 和 Footer 可以省略。

## 格式说明
### Header
Header部分只有一行，包括三个字段：type（必需）、scope（可选）和subject（必需）。

#### type
用于说明本次commit的类别，允许使用下面标识

- feat：新功能（feature）
- fix：修补bug
- docs：文档（documentation）
- style： 格式（不影响代码运行的变动）
- refactor：重构（即不是新增功能，也不是修改bug的代码变动）
- test：增加测试
- chore：构建过程或辅助工具的变动
- file: 添加文件素材

#### scope
用于说明 commit 影响的范围，比如Org, Account等等，视项目不同而不同。

#### subject
commit 目的的简短描述，不超过50个字符。

### Body

用于对本次 commit 的详细描述，可以分成多行。

有两个注意点。

- 使用第一人称现在时，比如使用change而不是changed或changes。
- 应该说明代码变动的动机，以及与以前行为的对比。

### Footer

#### 不兼容变动

如果当前代码与上一个版本不兼容，则 Footer 部分以BREAKING CHANGE开头，后面是对变动的描述、以及变动理由和迁移方法。

```
BREAKING CHANGE: isolate scope bindings definition has changed.
```
#### 关闭 Issue
如果当前 commit 针对某个issue，那么可以在 Footer 部分关闭这个 issue 。
```
Closes #234

Closes #123, #245, #992
```

## 提交频率

关于什么时候提交一次：

每次你写完一个功能的时候，就应该做一次提交，这样可以防止代码堆积，容易产生代码冲突的问题。

## Commit示例

```
fix(Home): 修复首页图标展示错位的问题

Closes #12
```

## 参考文档

[阮一峰：Commit message 和 Change log 编写指南](http://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html)