# 指令 `dotnet add [ProjectA] reference [ProjectB]`


## What

[ProjectA] 參考 [ProjectB]，意味 [ProjectA] 執行時，使用/應用/採用 [ProjectB] 裡面的內容，所以在編譯 [ProjectA] 時，系統會先編譯 [ProjectB]。

**注意** ： 誰參考誰，方向是重要的；如果相互參考會出現編譯錯誤。
  * 若 [ProjectA] 、 [ProjectB] 互相參考，那編譯 [ProjectA] 時看到有註明 "[ProjectA] 參考 [ProjectB]" ，就會轉而先去編譯 [ProjectB]，在編譯 [ProjectB] 時看到有註明 "[ProjectB] 參考 [ProjectA]" ，就會轉而去編譯  [ProjectA] ……，所以會出現編譯錯誤。


## How

假如你在 CLI 下指令 `dotnet add Tests\Tests.csproj reference ConsoleApp\ConsoleApp.csproj`

接著，你可以到 Tests.csproj 裡尋找參考是否成功：

```
<ItemGroup>
    <ProjectReference Include="..\ConsoleApp\ConsoleApp.csproj" />
</ItemGroup>
```


## 參考資料

* dotnet add reference
  * https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-add-reference