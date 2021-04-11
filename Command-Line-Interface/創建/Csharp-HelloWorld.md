## C# HelloWorld

應用範例的先決條件：

1. 電腦已安裝 Visual Studio Code
2. Visual Studio Code 已安裝 C# Extension
3. 電腦已安裝 .Net 5.0 SDK 或更新版本

### 在 Windows PowerShell 上的輸入

```txt
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

Try the new cross-platform PowerShell https://aka.ms/pscore6

PS C:\Users\coldb> cd .\myHome\
PS C:\Users\coldb\myHome> md HelloWorld


    Directory: C:\Users\coldb\myHome


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         3/15/2021   9:54 AM                HelloWorld


PS C:\Users\coldb\myHome> cd .\HelloWorld\
PS C:\Users\coldb\myHome\HelloWorld> dotnet new console
Getting ready...
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\coldb\myHome\HelloWorld\HelloWorld.csproj...
  Determining projects to restore...
  Restored C:\Users\coldb\myHome\HelloWorld\HelloWorld.csproj (in 69 ms).
Restore succeeded.

PS C:\Users\coldb\myHome\HelloWorld> dotnet run
Hello World!
PS C:\Users\coldb\myHome\HelloWorld>
```

---

### 解釋

預設為 Home Directory，即 C:\Users\使用者名稱。

但我想把專案建在資料夾 myHome 的新資料夾裡面。

```
PS C:\Users\coldb> cd .\myHome\
```

`cd` 代表 change directory

`cd` + 你想抵達的目錄名稱

* 自動完成目錄名稱的小技巧可參考：**讓 CLI 自動完成已建立的目錄或檔案名稱.md** 

```
PS C:\Users\coldb\myHome> md HelloWorld
```

`md` 代表 make directory，即 建立目錄 / 資料夾

`md` + 你想創建的資料夾名稱

```
PS C:\Users\coldb\myHome> cd .\HelloWorld\
```

前往 HelloWorld 資料夾

```
PS C:\Users\coldb\myHome\HelloWorld> dotnet new console
```

`dotnet` 是用來指示 CLI（Command-Line Interface 命令列介面） 執行 .NET 程式或相關指令的 指令

`dotnet new` 表示 creates a new project, configuration file, or solution based on the specified template.

`console` 代表 console application（主控台應用程式，一種專案的預設模板）

`dotnet new console` 表示 create a new .NET console application

```
PS C:\Users\coldb\myHome\HelloWorld> dotnet run
```

`dotnet run` 表示 runs source code without any explicit compile or launch commands，即執行原始碼。但這是基於 `dotnet build` 編譯出的 bytecode

---

### 資料來源

* Tutorial: Create a .NET console application using Visual Studio Code
  * https://docs.microsoft.com/zh-tw/dotnet/core/tutorials/with-visual-studio-code

* .NET CLI 總覽
  * https://docs.microsoft.com/zh-tw/dotnet/core/tools/

* dotnet new
  * https://docs.microsoft.com/zh-tw/dotnet/core/tools/dotnet-new#console

* dotnet run
  * https://docs.microsoft.com/zh-tw/dotnet/core/tools/dotnet-run

* Compiled language
  * https://en.wikipedia.org/wiki/Compiled_language

* 命令列介面
  * https://zh.wikipedia.org/wiki/%E5%91%BD%E4%BB%A4%E8%A1%8C%E7%95%8C%E9%9D%A2
