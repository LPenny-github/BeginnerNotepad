## URI 裡的空白導致製作超連結失敗

因為從以前開始，空白格就作為切分命令的字元，所以無論是 URI 或 URL 都預設沒有空白格。

有的話？

有的話，就用跳脫字元與編碼，讓解讀 URI 或 URL 的電腦知道：包含這些空白格在內是一整個字串。

### 目前可行的方法

假如 shortName = @"./軟工術語/一般/URI VS URL.md"

1. `20` 是空白格的 16 進位 表示
```
path = shortName.Replace(" ","%20"); 

// path = @"./軟工術語/一般/URI%20VS%20URL.md
```


### 為什麼 VS Code 預覽是超連結，上傳 GitHub，點連結卻顯示網頁不存在

因為 VS Code 解析 Markdown 文件時，只是簡單對格式判讀，並沒有測試連結是否可用。例如：

1. [創建](./Command-Line%20Interface/創建) 
    * `* [創建](./Command-Line%20Interface/創建)`
2. [創建](./Command-Line+Interface/創建)   
    * `* [創建](./Command-Line+Interface/創建)`
3. [創建](./Command-Line Interface/創建)   
    * `* [創建](./Command-Line Interface/創建)`

其中 1 和 2 因為 `()` 中為連續字串，被 VS Code 解析 為超連結；而 3 因為含有空白所以被認為不是超連結。其實在 GitHub 上點擊 2 是找不到頁面的。


### 一堆資料說可行，最後卻不行，搞得我好亂

從以前平民老百姓很難上網，到撥接上網，到目前人人都可上網、幾乎處處都可上網。

技術日新月異，總有歷史包袱。解析器並不知道你用的是西元幾年的標準，你也不知道解析器是用哪個標準，所以有些可以有些不可以！


### 參考資料

* 跳脫字元
  > Quoted-printable，把8位元資料編碼為7位元有限行長的資料，使用=作為跳脫字元。
  * https://zh.wikipedia.org/wiki/转义字符

* 百分號編碼
  > 當HTML表單中的資料被提交時，表單的域名與值被編碼並通過HTTP的GET或者POST方法甚至更古遠的email[2]把請求傳送給伺服器。這裡的編碼方法採用了一個非常早期的通用的URI百分號編碼方法，並且有很多小的修改如換行規格化以及把空格符的編碼"%20"替換為"+" 。按這套方法編碼的資料的MIME類型是application/x-www-form-urlencoded，當前仍用於（雖然非常過時了）HTML與XForms規範中。
  * https://zh.wikipedia.org/wiki/百分号编码

* ASCII CODE 對照表
  * https://mcusoft.files.wordpress.com/2015/07/ascii_code_table-1.pdf


