# 合併 commit

## 假如你想要把目前還沒 stage 改變（的既有檔案），合併到上一個 commit

按照步驟：

1. `git log` ：看看本地端 Head 與 遠端版本 在哪個節點，看完 按 `q` 退出。

1. `git status` ：應該會出現檔案異動。

1. `git add -A` ：剛好只有一個改變，所以全部 stage。 <-- 視需求調整指令

1. `git status` ：用來確認上個步驟是否成功。

1. `git commit --amend` ：stage changes 而且導向 commit message 頁面，讓你可以更改 上一個 commit message。更改後關閉頁面。

1. `git log` ：確認本地端 Head 的位置，版本號碼也有改變。看完 按 `q` 。