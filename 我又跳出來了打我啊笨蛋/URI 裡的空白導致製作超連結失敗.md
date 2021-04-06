## URI 裡的空白導致製作超連結失敗

因為從以前開始，空白格就作為切分命令的字元，所以無論是 URI 或 URL 都預設沒有空白格。

有的話？

有的話，就用跳脫字元與編碼，讓解讀 URI 或 URL 的電腦知道：包含這些空白格在內是一整個字串。

### 目前可行的方法

假如 shortName = @"./軟工術語/一般/URI VS URL.md"

以下三種皆可行：

1. `20` 是空白格的 16 進位 表示
```
path = shortName.Replace(" ","%20"); 

// path = @"./軟工術語/一般/URI%20VS%20URL.md
```

2. 使用 `+` 號
```
path = shortName.Replace(" ","+");

// path = @"./軟工術語/一般/URI+VS+URL.md
```

3. `40` 是空白格的 8 進位 表示
```
path = shortName.Replace(" ","%40");

// path = @"./軟工術語/一般/URI%40VS%40URL.md
```

### 搞得我好亂

從以前平民老百姓很難上網，到撥接上網，到目前人人都可上網、幾乎處處都可上網。

技術日新月異，總有歷史包袱。解析器並不知道你用的是西元幾年的標準，所以很 NICE 都可以！


### 參考資料

* 跳脫字元
  * https://zh.wikipedia.org/wiki/转义字符

* 百分號編碼
  * https://zh.wikipedia.org/wiki/百分号编码

* ASCII CODE 對照表
  * https://mcusoft.files.wordpress.com/2015/07/ascii_code_table-1.pdf
