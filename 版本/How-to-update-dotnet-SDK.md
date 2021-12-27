# How to update dotnet SDK


## 前置作業


### 如何知道自己該下載 x64 或 x86 版本？

1. 第一次安裝：
   * 查詢自己裝置的系統，例如 Windows ：
     * (1) Settings
     * (2) System
     * (3) About
     * (4) System type  

2. 第二次以上安裝：
   * 去找上一次安裝檔，並查看檔名


## 安裝


1. 反安裝目前 .Net SDK 版本：原安裝檔點選 `Uninstall` 。

1. 安裝目標 .Net SDK 版本：
   * 前往 Download .NET
     * https://dotnet.microsoft.com/en-us/download/dotnet
       * (1) 選擇目標版本 
       * (2) 選擇目標產品（假若是 SDK）
       * (3) 按照裝置、配備和檔案形式 做選擇
       * (4) 儲存檔案

1. 執行安裝檔：
   * (1) 點擊安裝檔（因為我選擇下載安裝檔） 
   * (2) 點選 `Install` 
   * (3) 允許此 App 改變裝置
   * (4) 讓程式跑完  


## 驗證


1. 開啟 PowerShell 或 CLI

1. `dotnet --version` ：查詢版本


## 等等，為什麼我的 .net 5.0 的專案無法自動升級為 .net 6.0 ？


因為目前仍然需要手動。


### 步驟

1. 打開專案中所有檔名為 `launch.json` ，把 `configurations` 裡的 `program` 中的字串由 net5.0 改為 net6.0 。

1. 打開專案中所有副檔名為 `.csproj` ， 
   
   把 `<TargetFramework>net5.0</TargetFramework>` 

   改成 `<TargetFramework>net6.0</TargetFramework>`

1. `dotnet build` ：編譯

1. 自選項目：關掉編輯器重開

### 驗證

* 打開專案資料夾 bin > Debug ，看是否有出現 `.net6.0` 這個資料夾。

* 若有寫測試的話，跑看看是否能如期執行。