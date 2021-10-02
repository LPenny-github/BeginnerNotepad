# main 合併 branch


## 目標

把本地端 branch 版本的工作進度，更新至 main 和 remotes 。


## 步驟

* main 合併 branch

    1.  `git branch -a -v` 或是 `git log` ：確認 main 與 branch 兩者的版本（進度）

    1.  `git checkout main` ：把主場從 branch 轉至 main  

    1.  `git branch -a -v` ：確認你的主場已經成功轉至 main

    1.  `git merge branchName` ：把 branch 的工作進度合併至 main

    1.  `git branch -a -v` ：確認 main 和 branch 工作進度（版本號、版本訊息）相同

* main 推上 remotes

    1.  `git push` ：把本地端 main 的工作進度推上 remotes

    1.  `git branch -a -v` ：確認 main 和 remotes 工作進度（版本號、版本訊息）相同

* 返回 branch 主場

    1. `git checkout branchName` ：把主場從 main 轉至 branch

    1.  `git branch -a -v` ：確認你的主場已經成功轉至 branch


## 參考資料

* 3.2 使用 Git 分支 - 分支和合併的基本用法
  * https://git-scm.com/book/zh-tw/v2/使用-Git-分支-分支和合併的基本用法