# Code Review

## 目的

- 提高代码质量，查漏补缺。
- 相互学习。
- 促进项目内知识流动，防止对某个个人过分依赖。

## Commit Message 规范

规定格式如下：

```
$(scope): $(subject)

$(description)
```

- `$(scope)`：必需，取决于具体项目，一般为项目功能模块的名字，用来描述本次 commit **影响的范围**，比如 https://github.com/nodejs/node/commits/master ，后加入项目的新成员应遵循已有的 scope 约定。建议使用首字母小写的驼峰命名。`bug` 、 `hotfix` 、 `task` 、 `change` 、`refactor` 等等描述的都不是影响范围，故不能用作 scope 。除取决于具体项目的模块名之外，可以使用 `base` 表示基础结构、框架相关的改动。
- `$(subject)`：必需，50 个字符左右的简要说明，首字母小写，通常是动宾结构，描述做了什么事情，动词用一般现在时，禁止出现 *update code* ， *fix bug* 等无实际意义的描述，好的例子： *select connector by sorting free memory* （不需要形如 *update about how to select connector ...* 的啰嗦写法）, *fix sucess tip can not show on IE8* （不需要形如 *fix bug of ...* 的啰嗦写法）。
- `$(description)`：可选，详细说明，建议使用列表罗列要点。

## 流程

1. 提交者发起 topic 分支到目标分支的 Merge Request 。
    - 代码变动要尽量小且专注于一个任务，不要攒的很大，或者做多个任务，要保证审查者可以较快、较容易的 Review 。
    - 如果与目标分支有冲突，提交者应该自己使用 `git rebase` 或 `git merge`（共享分支的情况）解决。
    - 交给别人之前一定要自己先 Review 一遍，别人只是帮你查漏补缺，对自己的代码负责，不要浪费别人的时间。
    - 发起后，要在 GitLab 或者其它 Review 工具上 double check 变更集。
2. 审查者 Review 代码。
    - 对 [编写整洁的代码](#编写整洁代码) 中各项要求进行检查
    - 在任何有疑问或建议的地方留 comment。
    - 从中学习一些好的东西。
    - 完成后，如果有问题需要修复，留 comment “Reviewed and waiting for fix”，否则进行第 4 步。
3. 提交者响应 comments 。
    - 确实有问题的，修复之。如果该分支未被其他人使用，应使用 `git commit --amend` 提交以减少不必要的 commit 历史。
    - 不同意的，讨论。
    - 完成后，留 comment “Fixed”，审查者再次检查，回到第二步。
4. 审查者确认没有问题之后，将 Merge Request 转发给目标分支的维护者进行合并。
