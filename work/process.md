# 基本原则
- 优先级: Story > Bug (P1 > P2 > P3 > P4)
- Story title [截止日期] {title}
- P1 Bug 当天完成
- P2 Bug 尽快完成

# 如何提交一个 commit
  1. git add .
  2. git commit -m '{scope}: {message}'
  3. 有新的 change 如果需要合并到上一个 git commit --amend, 否则重复 2
  4. git fetch
  5. git rebase origin/develop
  6. 如果有冲突, 解决冲突, git rebase --continue
  7. git push 如果有必要 加上 -f

# 如何提交 merge request

# 如何完成Story / Task (假设 n 人天的 story)
  - 流程:
    1. 接收到 assigned story
    2. 前面 n-1 天完成 story 的功能, 并把代码 merge 进 target branch
    3. 第 n 天过一遍整体改动
    4. 把 story assign 给我
