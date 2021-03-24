## README.md 上傳 GitHub 換行跑版

我做了一個字串寫入本地端的 `README.md` 檔案，上傳 GitHub 後發現有換行跑版的現象（意思就是 *沒有換行*）。

### 行得通的寫法：

1. 使用 markdown 語法：字串前面加上 `* ` 或 `- `，後面加上換行指令 `\r\n` 或 `Environment.NewLine`
2. 在字串結尾加上兩個空白（像是 `  `），後面加上換行指令 `\r\n` 或 `Environment.NewLine`


### 範例：

```csharp
content += fileName.Replace(@"C:\Users\coldb\myHome\Notepad\", "* ")+ Environment.NewLine ;

content += fileName.Replace(@"C:\Users\coldb\myHome\Notepad\", "* ")+ "\r\n" ;

content += fileName.Replace(@"C:\Users\coldb\myHome\Notepad\", "- ")+ Environment.NewLine ;

content += fileName.Replace(@"C:\Users\coldb\myHome\Notepad\", "- ")+ "\r\n" ;

content += fileName.Replace(@"C:\Users\coldb\myHome\Notepad\", "  ")+"  "+ Environment.NewLine ;

content += fileName.Replace(@"C:\Users\coldb\myHome\Notepad\", "  ")+"  "+ "\r\n" ;
```

### 目標結果

```
 * 創建\用 CLI 建立 C# HelloWorld.md
 * 檔案操作\本地端\取得檔案路徑與檔名.md
```

### 換行跑版

```
* 創建\用 CLI 建立 C# HelloWorld.md * 檔案操作\本地端\取得檔案路徑與檔名.md 
```

### 資料來源

* 為什麼我的 Markdown 會跑版？
  > 最簡單的例子就是換行，就標準的 Markdown 語法，當你在 .md 檔內換行，並不會真的換行。如果你要做到換行，必須在行尾加入兩個空白，或是手動插入 `<br>`。
  * https://dwy6626.github.io/post/markdown-intro-history/#:~:text=%E6%9C%80%E7%B0%A1%E5%96%AE%E7%9A%84%E4%BE%8B%E5%AD%90%E5%B0%B1%E6%98%AF,%E9%83%BD%E8%AE%8A%E6%88%90%E7%9C%9F%E6%AD%A3%E7%9A%84%E6%8F%9B%E8%A1%8C%E3%80%82

* https://commonmark.org/help/