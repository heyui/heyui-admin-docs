# 贡献指南

首先感谢你使用 heyui admin。

如果你愿意为 heyui admin 贡献代码或提供建议，请阅读以下内容。

## Issue 规范

- 在提交 issue 之前，请搜索相关内容是否已被提出。
- 请说明 heyui、vue、hey-cli 或者 vue-cli 的版本号，并提供操作系统和浏览器信息。
- 推荐使用 codepen 生成在线 demo，这能够更直观地重现问题。

## Pull Request 规范

在修改之前，请先 fork 一份到自己的项目下，不要直接在仓库下建分支。

### git commit

修改的内容请按照一次需求修改一次 commit 来进行。

如果一次修改产生多个commit，请在 merge 之前合并 commit，确保 commit 记录的整洁。

commit message 请按照 [git commit 规范](/#commit) 执行。

如果是修复 bug，请在 commit message 中添加 Close #1 bug 关联信息。

### 提交dev分支

所有的 PR 请提交至 dev 分支，提交 master 将会被直接关闭。

### 注意事项

提交 PR 前请 rebase 代码，确保提交后无冲突代码。