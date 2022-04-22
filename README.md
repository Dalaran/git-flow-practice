#a git flow practice demo

###Steps


```bash
# 省略了一些git pull检查, 删除分支的步骤
$ git init
$ git remote add origin https://github.com/Dalaran/git-flow-practice.git && git pull origin main
$ git checkout -b develop && git push -u origin develop
# 新建feature: 排行榜功能
$ git checkout -b feature/rank-module develop && git push -u origin feature/rank-module
$ echo "实现排行榜功能" > rank-module.txt
$ git add rank-module.txt && git commit -m "finish:feature:排行榜功能"
# 拉取最新develop分支=>合并进该分支
$ git checkout develop && git merge feature/rank-module && git push origin develop
# 新建release: v1.0.0
$ git checkout -b release/1.0.0 develop 
# 测试完后, 合并到 main&develop分支中
$ git checkout main && git pull && git merge release/1.0.0 && git push -u origin main 
$ git checkout develop && git merge release/1.0.0 && git push -u origin develop
# 添加v1.0.0标签
$ git tag -a v1.0.0 main -m "Feature:新增排行榜功能" && git push --tags
# 新建feature: 任务模块
$ git checkout -b feature/task-module develop && git push -u origin feature/task-module
# 新建hotfix: 排行榜bug
$ git checkout -b hotfix/rank-module_player_cannot_claim_reward_bug main
$ echo "修复排行榜玩家无法领取奖励的BUG" >> rank-module.txt
$ git add rank-module.txt && git commit -m "hotfix:rank-module:修复玩家无法领奖励的BUG"
# 测试完后, 合并到 main&develop分支中
$ git checkout main && git merge hotfix/rank-module_player_cannot_claim_reward_bug  && git push origin main
$ git checkout develop && git merge hotfix/rank-module_player_cannot_claim_reward_bug && git push origin develop
# 添加v1.0.1标签
$ git tag -a v1.0.1 main -m "Bugfixes:修复玩家无法领取奖励的BUG" && git push --tags
# 继续完成任务模块功能
$ git checkout feature/task-module 
$ echo "实现任务模块功能" > task-module.txt
$ git add task-module.txt && git commit -m "finish:feature:任务模块"
# 合并任务模块进develop分支
$ git checkout develop && git merge feature/task-module && git push origin develop
# 新建release: v1.1.0
$ git checkout -b release/1.1.0 develop
# 测试完后, 合并到 main&develop分支中
$ git checkout main && git merge release/1.1.0 && git push -u origin main 
$ git checkout develop && git merge release/1.1.0 && git push -u origin develop
$ git tag -a v.1.1.0 main -m "Feature:新增任务模块" && git push --tags 
```