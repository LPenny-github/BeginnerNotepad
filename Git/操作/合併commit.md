# 合併 commit

## 假如你想要把目前還沒 stage 改變（的既有檔案），合併到上一個 commit

按照步驟：

1. `git log` ：看看本地端 Head 與 遠端版本 在哪個節點，看完 按 `q` 退出。

1. `git status` ：應該會出現檔案異動。

1. `git add -A` ：剛好只有一個改變，所以全部 stage。 <-- 視需求調整指令

1. `git status` ：用來確認上個步驟是否成功。

1. `git commit --amend` ：stage changes 而且導向 commit message 頁面，讓你可以更改 上一個 commit message。更改後關閉頁面。

1. `git log` ：確認本地端 Head 的位置，版本號碼也有改變。看完 按 `q` 。

---
---

## 假如你想要合併多個 commit

### 方法一： `git rebase -i HEAD~3`

1. `git log` ：看看本地端 Head 與 遠端版本 在哪個節點，看完 按 `q` 退出。

假如結果看來像這樣，而目標是合併此三個 commit：

```txt
commit 3bbfe6b0d4b480ff3cf97105ca7d47e5098e934d (HEAD -> test)
Author: OYah <OYah@gmail.com>
Date:   Fri Oct 15 04:28:08 2021 +0800

    add 3.md

commit 2d09439af94e0b15f4746a51aa271a28e510625b
Author: OYah <OYah@gmail.com>
Date:   Fri Oct 15 04:27:45 2021 +0800

    add 2.md

commit 17b70a8337b1687352a900f18906df3237d61dd0
Author: OYah <OYah@gmail.com>
Date:   Fri Oct 15 04:27:09 2021 +0800

    add 1.md
```

2. `git rebase -i HEAD~3` ：合併包含目前 HEAD 所在的三個 commit。

會跳出標籤名為 git-rebase-tode 的檔案，內容是那三個 commit 和一些說明：

（**注意**：編排方式是時序 前 -> 後，與 `git log` 的編排方式 後 -> 前，正好相反）

```txt
pick 17b70a8 add 1.md
pick 2d09439 add 2.md
pick 3bbfe6b add 3.md

# Rebase de322ea..3bbfe6b onto de322ea (3 commands)
#
# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup [-C | -c] <commit> = like "squash" but keep only the previous
#                    commit's log message, unless -C is used, in which case
#                    keep only this commit's message; -c is same as -C but
#                    opens the editor
# x, exec <command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop <commit> = remove commit
# l, label <label> = label current HEAD with a name
# t, reset <label> = reset HEAD to a label
# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified); use -c <commit> to reword the commit message
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
```

3. 依照需求把內容作修改，然後儲存，關閉。

例如改這兩行：

```txt
pick 17b70a8 add 1.md
squash 2d09439 add 2.md
squash 3bbfe6b add 3.md
```

儲存，關閉後，系統後跳出標籤名為 COMMIT_EDITMSG 的檔案，要你決定合併後的 commit message：
（**注意**：編排方式是時序 前 -> 後，與 `git log` 的編排方式 後 -> 前，正好相反）

```txt
# This is a combination of 3 commits.
# This is the 1st commit message:

add 1.md

# This is the commit message #2:

add 2.md

# This is the commit message #3:

add 3.md

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Date:      Fri Oct 8 13:13:16 2021 +0800
#
# interactive rebase in progress; onto de322ea
# Last commands done (3 commands done):
#    squash 2d09439 add 2.md
#    squash 3bbfe6b add 3.md
# No commands remaining.
# You are currently rebasing branch 'test' on 'de322ea'.
#
# Changes to be committed:
#	new file:   1.md
#	new file:   2.md
#	new file:   3.md
```

4. 由於開頭為 `#` 的字串都會被忽略，所以你可以挑一個舊的 commit message，其他開頭都打 `#` 或是全部開頭都打 `#` 自己輸入新的 commit message。

像是改成這樣（節錄）：

```txt
add 3 files

# This is a combination of 3 commits.
# This is the 1st commit message:

#add 1.md

# This is the commit message #2:

#add 2.md

# This is the commit message #3:

#add 3.md
```

儲存，關閉檔案。

5. `git log` ：確認是否合併成功。

---

### 方法二： `git reset --soft HEAD~3`

1. `git log` ：看看本地端 Head 與 遠端版本 在哪個節點，看完 按 `q` 退出。

1. `git reset --soft HEAD~3` ：回到包括 HEAD 的三個 commit 之前的狀態，這三個改變將顯示於 暫存區。

1. `git commit -a -m "add 3 files"` ：給這三個改變，一個新的 commit message。


#### 參考資料

* What is difference between 'git reset --hard HEAD~1' and 'git reset --soft HEAD~1'?
  * https://stackoverflow.com/questions/24568936/what-is-difference-between-git-reset-hard-head1-and-git-reset-soft-head

* 【狀況題】剛才的 Commit 後悔了，想要拆掉重做…
  * https://gitbook.tw/chapters/using-git/reset-commit.html

---

### 附註

* `git help 指令` ：查閱更多關於 指令 的資訊。例如：
  * `git help rebase`
  * `git help reset`
