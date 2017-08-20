---
layout: post
title:  "Git命令总结" 
---

<br />

*记录一下不太常用的Git命令．*

 - 重建代码历史
   - git checkout --orphan latest_branch（新建orphan分支）
   - git add -A（将所有更改加入到暂存区）
   - git commit -am "Init message."（提交到本地仓库）
   - git branch -D master（删除原分支）
   - git branch -m master（重命名现分支）
   - git push -f origin master（强行推到远端仓库）
 - 修改前次Commit注释
   - git commit --amend （修改前次Commit注释）
   - git push -f （强行推到远端仓库）
 - 已经Commit但没有Push，想撤销Commit
   - git log（查看log，找到Commit的代号）
   - git reset --hard CommitId（把头重置到某次Commit）