# 含有 NUnit 的 Csharp sln


0. `dotnet new --install NUnit3.DotNetNew.Template` ：安裝 nunit 樣板專案


以下是抄 `含有-xunit-的-Csharp-sln.md` 只改 `5`，因為之前是裝 xunit，這次裝 nunit：


```txt
## 步驟

以下是用 Windows PowerShell 的操作步驟：

1. `md TheArtOfUnitTesting1`
2. `cd TheArtOfUnitTesting1`
3. `dotnet new sln`
4. `dotnet new console -o LogAn`
5. `dotnet new nunit -o UnitTests`   
6. `dotnet sln add UnitTests\UnitTests.csproj`
7. `dotnet sln add LogAn\LogAn.csproj`
8. `dotnet add UnitTests\UnitTests.csproj reference LogAn\LogAn.csproj`
```


## 參考資料

* [Day25] ASP.NET Core 2 系列 - 單元測試 (NUnit)
  * https://ithelp.ithome.com.tw/articles/10196862