# 如何用URI移駕到其他目錄

依據不同的作業系統，有不同的路徑表示法。

以 Windows 10 系統來說：

* `.` 代表當前的目錄
* `..` 代表上一層目錄
* `\` Windows 本機端目錄分隔符號
* `/` URI 目錄分隔符號

## 範例

一則網址：

https://github.com/LPenny-github/Notepad/blob/main/打我啊笨蛋/URI-裡的空白導致製作超連結失敗.md

如果我們想從 `URI-裡的空白導致製作超連結失敗.md` 做一個 URI 跳轉至：

https://github.com/LPenny-github/Notepad/tree/main/Command-Line-Interface/創建

可行的方法：

1. 回到 `main`
   * [創建](https://github.com/LPenny-github/Notepad/blob/main/打我啊笨蛋/URI-裡的空白導致製作超連結失敗.md/../../Command-Line-Interface/創建)
     * `[創建](https://github.com/LPenny-github/Notepad/blob/main/打我啊笨蛋/URI-裡的空白導致製作超連結失敗.md/../../Command-Line-Interface/創建)`

2. 回到 `Notepad`
   * [創建](https://github.com/LPenny-github/Notepad/blob/main/打我啊笨蛋/URI-裡的空白導致製作超連結失敗.md/../../../../tree/main/Command-Line-Interface/創建)
      * `[創建](https://github.com/LPenny-github/Notepad/blob/main/打我啊笨蛋/URI-裡的空白導致製作超連結失敗.md/../../../../tree/main/Command-Line-Interface/創建)`
      * https://github.com/LPenny-github/Notepad/blob/main/打我啊笨蛋/URI-裡的空白導致製作超連結失敗.md/ 最後這個斜線會讓 `URI-裡的空白導致製作超連結失敗.md` 被認為是個 **目錄**

3. 回到 `Notepad`
   * [創建](https://github.com/LPenny-github/Notepad/blob/main/打我啊笨蛋/URI-裡的空白導致製作超連結失敗.md../../../Command-Line-Interface/創建)
     * `[創建](https://github.com/LPenny-github/Notepad/blob/main/打我啊笨蛋/URI-裡的空白導致製作超連結失敗.md../../../Command-Line-Interface/創建)`


## 等等，為何回到 `main` 可行？

因為 GitHub 網站會自動判斷應該要 blob（丟出一坨資料） 或 tree（查看結構）。

若你將 `https://github.com/LPenny-github/Notepad/blob/main/打我啊笨蛋/URI-裡的空白導致製作超連結失敗.md`

誤置為 `https://github.com/LPenny-github/Notepad/tree/main/打我啊笨蛋/URI-裡的空白導致製作超連結失敗.md`

按下 `enter` 網址機自動轉變為

`https://github.com/LPenny-github/Notepad/blob/main/打我啊笨蛋/URI-裡的空白導致製作超連結失敗.md`

所以，在可行方法 1 中雖然你給出去網址是 
`https://github.com/LPenny-github/Notepad/blob/main/Command-Line-Interface/創建`

但經由 GitHub 的自動修正機制，網址會自動由 `blob` 改成 `tree`，於是轉向成功！

**檔案全名後 或是 目錄名後 一定要先加上 URI 分隔符號。**


## 參考資料

* 路徑 (電腦科學)
  * https://zh.wikipedia.org/wiki/路径_(计算机科学)
