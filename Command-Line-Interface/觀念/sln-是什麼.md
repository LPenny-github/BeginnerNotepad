# sln 是什麼

以下全是譬喻，可能有不精準之處：

想像一個工具箱（.sln）裝滿解決單一問題的工具（.csproj/. vbproj/.dbproj...），以及 "測量這些解決問題的工具是否真正解決問題" 的工具（.csproj/. vbproj...）。

一個解決螺絲釘有沒有好好拴緊的工具箱，裡面既有電動鑽洞器、各種形狀的螺絲起子和各式形狀的螺絲釘，同時有捲尺、墨線等輔助工具來協助工人精準解決問題。

但，光是把工具放入工具箱，忠心且耿直的工人無法了解你的深意，你必須指明工具箱必須放入的工具和測量工具（例如：`dotnet sln add 十字形螺絲起子.csproj`、`dotnet sln add 捲尺.csproj`），以及工具與測量工具之間依賴的關係（`dotnet add 捲尺.csproj reference 十字形螺絲起子.csproj`），好讓耿直的工人出發工作前照順序清點必要零件（沒有帶 `十字形螺絲起子` 的話，那 `捲尺` 要輔助誰咧），順利操作任務，達成完成拴緊螺絲釘的任務。


## 參考資料

* Visual Studio 中的方案和專案
  * https://docs.microsoft.com/zh-tw/visualstudio/ide/solutions-and-projects-in-visual-studio?view=vs-2019

* 方案 ( .sln) 檔
  * https://docs.microsoft.com/zh-tw/visualstudio/extensibility/internals/solution-dot-sln-file?view=vs-2019