# 新專案加上 git 且連結 GitHub

分為三部分：

## 一、在 GitHub 上開 repo，得到該 repo 的 SSH


## 二、將專案加上 git

用 VS Code 打開專案。打開 TERMINAL，輸入：

1. ls -force ：查看檔案清單，包括被隱藏的檔案
1. git init ：初始化 git <-- 替你的專案加上 git 功能
1. ls -force ：檔案清單應該會多一個 .git 檔案
1. git status ：你會看到全部的檔案都未追蹤
1. code .gitignore ：在專案中加入 .gitignore 檔案
1. 在 .gitignore 檔案中輸入想要忽略的檔案或資料夾，例如：bin/、obj/，存檔
1. git status ：未追蹤的檔案沒有 bin 和 obj
1. git add -A : stage 所有未追蹤的檔案（但不包含 .gitignore 裡的檔案，也就是 bin 和 obj）
1. git status ：成功的話，檔案們會從紅字變成綠字，提示你等待 commit 的檔案
1. git commit -m "Initialize this repository." ：下第一個 commit、鍵入訊息
1. git status ：確認 commit 成功， `On branch master nothing to commit, working tree clean`
1. git log ：確認 commit 訊息，這邊也會顯示 commit 者的基本資訊
1. git branch -M main ：把 `master` 這個本地端的代稱改成 `main` <-- 你也可以不改


## 三、搭建本地端與遠端的友誼之橋

1. git remote -v ：沒有出現任何東西，表示你還沒設定遠端
1. git remote add origin 你的SSH ：設定遠端
1. git remote -v ：將出現遠端的資訊
1. git push -u origin main：搭建本地端與遠端的友誼之橋
1. git branch -a -vv ：確認本地端與遠端的版號、 commit 訊息相同