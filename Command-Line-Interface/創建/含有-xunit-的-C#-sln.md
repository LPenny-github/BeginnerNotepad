## 創建含有 xunit 的 C# sln

### 步驟

以下是用 Windows PowerShell 的操作步驟：

1. `md notepad-directory-manager`
2. `cd notepad-directory-manager`
3. `dotnet new sln`
4. `dotnet new console -o ConsoleApp`
5. `dotnet new xunit -o Tests`
6. `dotnet sln add Tests\Tests.csproj`
7. `dotnet sln add ConsoleApp\ConsoleApp.csproj`
8. `dotnet add Tests\Tests.csproj reference ConsoleApp\ConsoleApp.csproj`

### 解釋

* 步驟三：電腦會自動用目錄名稱當作 sln（solution） 的名稱
  * 若想自訂 sln 名稱，請用 `dotnet new sln -o 你想要的sln名稱`

* 步驟六~八：電腦不會因為你在 sln 創建 project，就知道他們彼此的關聯，所以你需要手動建立

### 怎麼確認上述步驟

* 確認步驟六、七成功：在 Windows PowerShell 中，至 notepad-directory-manager 目錄下，執行 `dotnet build`，`build` 這個命令會找尋目錄底下 `.sln` 或 `.csproj` 檔案，並且執行它。
  * 但這僅止表示 ConsoleApp 或 Tests 其中一個和 sln 建立關聯成功

```
Microsoft (R) Build Engine version 16.9.0+57a23d249 for .NET
Copyright (C) Microsoft Corporation. All rights reserved.

  Determining projects to restore...
  All projects are up-to-date for restore.
  ConsoleApp -> C:\Users\coldb\myHome\notepad-directory-manager\ConsoleApp\bin\Debug\net5.0\ConsoleApp.dll
  Tests -> C:\Users\coldb\myHome\notepad-directory-manager\Tests\bin\Debug\net5.0\Tests.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:02.80
```

* 確認步驟八成功：打開 Tests.csproj，看能否找到這行：

```
  <ItemGroup>
    <ProjectReference Include="..\ConsoleApp\ConsoleApp.csproj" />
  </ItemGroup>
```