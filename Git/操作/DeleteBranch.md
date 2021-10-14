# Delete Branch

1. `git branch -a -v` ：確認既有分支。

```txt
  csv-to-json         715f632 Could show the operation result
  main                715f632 Could show the operation result
* test                2e10928 add 5 files
  remotes/origin/main 715f632 Could show the operation result
```

2. `git checkout csv-to-json` ：將主場轉移至 欲刪除 的其他分支，這裡挑的是 csv-to-json。

```txt
Switched to branch 'csv-to-json'
```

3. `git branch -a -v` ：確認跳到分支 csv-to-json 是否成功。

（純屬個人習慣。其實你無法刪除自己目前所在的分支）

```txt
* csv-to-json         715f632 Could show the operation result
  main                715f632 Could show the operation result
  test                2e10928 add 5 files
  remotes/origin/main 715f632 Could show the operation result
```

4. `git branch -d test` ：刪除分支 test。

出現防呆機制：

```txt
error: The branch 'test' is not fully merged.
If you are sure you want to delete it, run 'git branch -D test'.
```

5. `git branch -a -v` ：確認分支還沒有被刪除。

（純屬個人習慣。）

```txt
* csv-to-json         715f632 Could show the operation result
  main                715f632 Could show the operation result
  test                2e10928 add 5 files
  remotes/origin/main 715f632 Could show the operation result
```

6. `git branch -D test` ：確定刪除分支 test。

```txt
Deleted branch test (was 2e10928).
```

7. `git branch -a -v` ：確認分支刪除成功。

```txt
* csv-to-json         715f632 Could show the operation result
  main                715f632 Could show the operation result
  remotes/origin/main 715f632 Could show the operation result
```
