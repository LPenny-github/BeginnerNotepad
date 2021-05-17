# 用 Windows 工作排程執行 git push

## 目標

解決每天都要手動 git push 自己的 筆記repo（管理和維護僅我一人）

## 步驟

簡單來說就是：
1. 寫好 .cmd 檔案
2. 設定工作排程

## 說明

1. 寫好 .cmd 檔案
   * (1). 進入 cmd ，或是 進入 Windows PowerShell 鍵入 `cmd`
        
        `PS` 指的就是 PowerShell
        ```
        PS C:\Users\coldb> cmd
        Microsoft Windows [Version 10.0.19042.928]
        (c) Microsoft Corporation. All rights reserved.

        C:\Users\coldb>
        ```
   * (2). 把預期的 script 先寫在這裡試試看

        %userProfile% 中 userProfile 是 cmd 內建的環境變數（不分大小寫），你可以用指令 `set` 列出所有環境變數

        ```
        C:\Users\coldb> cd %userProfile%\myHome\Notepad
        C:\Users\coldb> git push
        ```

        你也可以善用 `echo + %變數名稱%` 觀察變數的內容
        ```
        C:\OnlyForTest\notepad-directory-manager\ConsoleApp>echo %USERPROFILE%
        C:\Users\coldb
        ```

        既然是路徑，你也可以寫出絕對路徑。也就是說以下兩者是相等的：

        cd %userProfile%\myHome\Notepad
        cd C:\Users\coldb\myHome\Notepad

    * (3). 建立 .cmd 檔案，內容是：

        ```
        cd %userProfile%\myHome\Notepad
        git push

        ```

2. 設定工作排程

   * (1). 開啟 `工作排程`（Task Scheduler）
   * (2). 點右邊 `建立基本工作`（Create Basic Task）
   * (3). 按照流程填表
        * 不需要把權限調到最高
        * `條件`（Conditions）：預設是當電腦插上插頭時執行，如果你不想要這樣，記得建立時調整設定；或者建立之後，在該工作排程上右鍵，選 Properties，更改設定
   * (4). 全部設定好之後，你可以在該工作排程上右鍵，選 Run 或是 自然地等你排程的時間到，讓電腦跑跑看；畫面應該會閃一下 cmd，但是跑完程式後便會自動關閉
   * (5).  如果你不想讓程式跑完後便會自動關閉，可以在最後一行加上 `pause` 讓畫面留在螢幕上，直到你按下任何鍵。你試完之後可以加上註解，註解的關鍵字是 `rem`。如下列所示：

        ```
        cd %userProfile%\myHome\Notepad
        git push
        rem pause
        ```


## 錯過執行時間要怎麼辦呢

設定錯過執行時間時，自動再執行一次。

在該工作排程上右鍵，選 Properties，點 Settings，勾選 `Run task as soon as possible after a scheduled start is missing` （我不知道中文翻成什麼 XD） 


## 資料來源

* 使用工作排程器執行批次檔
  * https://snoopy30485.github.io/2019/01/23/使用工作排程器執行批次檔/