# `Could not execute because the specified command or file was not found.`

## 情境

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

## 修正

```
PS C:\Users\coldb\myHome\Notepad> dotnet branch -a -vv
```

`dotnet` 改成 `git`，即：

```
PS C:\Users\coldb\myHome\Notepad> git branch -a -vv
```

---

## 解釋

## TERMINAL 收到人類的手動輸入後都做些什麼

（因為程度不足的關係，以下的敘述充滿擬人化譬喻）

1. TERMINAL 會把輸入字串裡，將 **空白** 作為切分點。
   * 例如：把大字串 `git branch -a -vv` 切成小字串 `git`、`branch`、`a`、`-vv`。

2. 把 **第一個指令**，即 `git` 當作搜尋條件，找到儲存區中同名的可執行檔。

3. 將 第一個指令 **之外** 的字串，即 `branch`、`a`、`-vv`，丟給那個執行檔。

3. 那個執行檔 將處理字串後的結果，傳給 TERMINAL。

4. TERMINAL 顯示結果。

## 錯誤訊息傳遞什麼樣的資訊

```
Could not execute because the specified command or file was not found.
```

無法執行，因為找不到特定指令或是檔案。

可以猜想，TERMINAL 找到了 .Net SDK（因為我有下載），把字串丟給 .Net SDK，.Net SDK 認不得這是啥（.Net SDK 沒有設定 `branch` 指令）。

例如：對狗 喵喵叫。狗回覆：「我聽不懂，我的汪生中從沒學過這些（指令）。」

**所以，可能是找錯對象，或是表達錯誤。**

## 使用 `Get-Command` 指令來了解 `dotnet` 和 `git`

* `dotnet` 和 `git` 都是裝在電腦上的應用程式

```
PS C:\OnlyForTest> Get-Command dotnet

CommandType     Name                                               Version
-----------     ----                                               -------
Application     dotnet.exe                                         5.0.4...
```

```
PS C:\OnlyForTest> Get-Command git

CommandType     Name                                               Version
-----------     ----                                               -------
Application     git.exe
```