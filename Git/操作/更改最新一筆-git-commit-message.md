# 更改最新一筆 git commit message

兩個方法：

1. 下指令 `git commit --amend -m "我才是最新版的訊息"`
2. 下指令 `git commit --amend`，接著在編輯器中更新你的指令

## 資料來源

* 【狀況題】修改 Commit 紀錄
  * https://gitbook.tw/chapters/using-git/amend-commit1.html

* Git - 怎麼修改最新一筆 git message?
  > 透過 --amend Git 在背後的運作，其實是會產生一個新的 commit 來取代掉舊的 commit，所以如果你 git log 注意看，前後的 commit id (SHA1 checksum) 是會不一樣的！
  * https://www.fooish.com/posts/how-to-change-a-commit-message.html