## 預覽 markdown 檔案

### 圖形介面

點 VS Code 右上角 `兩個長方形兼有一個放大鏡` 的圖示。

當你把游標停在那個圖示上，會顯示 `Open Preview to the Side (Ctrl+K V)`。


### 快捷鍵

`Ctrl+K V`

精緻步驟：

0. 滑鼠游標在 Markdown 文件區域
1. 按 `Ctrl`鍵 不放
2. 按 `K`（不分大小寫） 不放
3. 放掉 `K`
4. 放掉 `Ctrl`鍵
5. 按 `V`（不分大小寫） 不放
6. 放掉 `V`

### 注意事項

* 雖然說是預覽，但仍然可能會跟輸出結果稍微有一點點落差
  * 例如：預覽畫面中，`### ` 所產生的標題效果 與 一般陳述 的區別不明顯
  * 因為
    * 每個平台（VSCode、GitHub、GitLab…）轉 Markdown 文件 為 HTML 的工具不同
    * Markdown 格式定義並不是很嚴謹，於是有人發起 "CommonMark" 行動，目標是 協商出多數人認可且嚴謹的語法規格書。目前業界也朝著 CommonMark 的方向發展
  
* 如果你的輸入法切在中文輸入，那麼，電腦可能不會理你

### 資料來源

* CommonMark Spec
  * https://spec.commonmark.org/

* Markdown (wiki)
  * https://zh.wikipedia.org/wiki/Markdown