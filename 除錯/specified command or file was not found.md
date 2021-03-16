## `Could not execute because the specified command or file was not found.`

### 情境

在 VS Code 裡的 TERMINAL 輸入指令，想要查詢 Git 本地端版本情形。

```
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

Try the new cross-platform PowerShell https://aka.ms/pscore6

PS C:\Users\coldb\myHome\Notepad> dotnet branch -a -vv
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET program, but dotnet-branch does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
PS C:\Users\coldb\myHome\Notepad>
```

### 修正

```
PS C:\Users\coldb\myHome\Notepad> dotnet branch -a -vv
```

`dotnet` 改成 `git`，即：

```
PS C:\Users\coldb\myHome\Notepad> git branch -a -vv
```

---

## 解釋

### TERMINAL 收到人類的手動輸入後都做些什麼

（因為程度不足的關係，以下的敘述充滿擬人化譬喻）

1. TERMINAL 會把輸入字串裡，遇到的 **第一個空白** 作為切分點，將第一個空白 **之前** 的字串作為 **第一個指令**。

2. 把 **第一個指令** 當作搜尋條件，找到儲存區中那個程式。

3. TERMINAL 將第一個空白 **之後** 的字串丟給那個程式。

3. 那個程式 將處理字串後的結果，傳給 TERMINAL。

4. TERMINAL 顯示結果。

### 錯誤訊息傳遞什麼樣的資訊

```
Could not execute because the specified command or file was not found.
```

無法執行，因為找不到特定指令或是檔案。

可以猜想，TERMINAL 找到了 .Net SDK（因為我有下載），把字串丟給 .Net SDK，.Net SDK 認不得這是啥（.Net SDK 沒有設定 `branch` 指令）。

例如：對狗 喵喵叫。狗回覆：「我聽不懂，我的汪生中從沒學過這些（指令）。」

**所以，可能是找錯對象，或是表達錯誤。**