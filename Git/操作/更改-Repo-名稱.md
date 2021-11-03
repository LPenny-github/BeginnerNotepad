# 更改 Repo 名稱


## 在 GitHub 更改 Repo 名稱


1. 進入目標 Repo
2. 點 `Settings`
3. 在 Repository name 鍵入 Repo 的新名字，按 `Rename`


## 在 VS Code 更新 URL（若需要）


1. `git remote -v` ：先確定未更動前的目標資料夾。例如：

```
origin  git@github.com:LPenny-github/Notepad.git (fetch)
origin  git@github.com:LPenny-github/Notepad.git (push)
```

2. `git remote set-url origin new_url` ： `orgin` 是 remote 的版本名稱； `new_url` 是從 GitHub 該 repo 首頁的按鈕 `Code` 複製的 SSH。 
    * 例如： git remote set-url origin git@github.com:LPenny-github/BeginnerNotepad.git

3. `git remote -v` ：確認更動（repo 名稱由 Notepad 變為 BeginnerNotepad）是否成功。例如：

```
origin  git@github.com:LPenny-github/BeginnerNotepad.git (fetch)
origin  git@github.com:LPenny-github/BeginnerNotepad.git (push)
```


## 參考資料

* Renaming a repository
  * https://docs.github.com/en/github/administering-a-repository/renaming-a-repository

* [工具方法]_Github已存在檔案的Repository重新命名
  * http://rswong-blog.logdown.com/posts/1757944--github-already-exists-rename-repository-files?fbclid=IwAR18gUkZHTBEFJZnlVOcoqi9w2NuUCHgK1WoZk0dTmtzxxtKJHQOrjvF03w