# 讓 CLI 自動完成已建立的目錄或檔案名稱

假如你想對 Windows PowerShell 下這段指令：

```
`cd` + 你想抵達的目錄名稱
```

但是你的目錄名稱很長，懶得打。以下是小技巧：

* 在 Windows PowerShell 介面上，輸入 一個字元（英文字母有區分大小寫），按 `tab` 讓電腦替你自動完成目錄 / 檔案 的名稱

  * 如果你的目錄 / 檔案 的名稱中有許多都使用同一個字元，那你可以多打幾個字元，再按 `tab`
  * 如果你輸入了幾個字元，按 `tab`，電腦卻不理你，那你可以使用指令 `ls`，列出目前路徑下所有目錄 / 檔案 的名稱   

    * 但如果你是在 Linux 中的 Bash，若你鍵入的字元無法對應到任何已存在的檔案，可以 按 2 次  `tab`，列出所有可能符合的目錄 / 檔案。