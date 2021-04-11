## Get-Command VS Get-Help

### 同

都可以查詢命令。

### 異

`Get-Help` 是從手冊中查詢，會提供完整的內容。如果你想要查詢的命令是本地端裝設的應用程式，請用 `Get-Command `，`Get-Help` 會認不出來。

以下是兩個命令查詢 `ls` 的區別：

* `Get-Command ls`

```
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           ls -> Get-ChildItem
```

* `Get-Help  ls`

```
NAME
    Get-ChildItem

SYNTAX
    Get-ChildItem [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint32>] [-Force]
    [-Name] [-UseTransaction] [-Attributes {ReadOnly | Hidden | System | Directory | Archive | Device | Normal | Temporary | SparseFile |
    ReparsePoint | Compressed | Offline | NotContentIndexed | Encrypted | IntegrityStream | NoScrubData}] [-Directory] [-File] [-Hidden]
    [-ReadOnly] [-System]  [<CommonParameters>]

    Get-ChildItem [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint32>]
    [-Force] [-Name] [-UseTransaction] [-Attributes {ReadOnly | Hidden | System | Directory | Archive | Device | Normal | Temporary |
    SparseFile | ReparsePoint | Compressed | Offline | NotContentIndexed | Encrypted | IntegrityStream | NoScrubData}] [-Directory] [-File]
    [-Hidden] [-ReadOnly] [-System]  [<CommonParameters>]                                                                  

ALIASES
    gci
    ls
    dir

REMARKS
    Get-Help cannot find the Help files for this cmdlet on this computer. It is displaying only partial help.
        -- To download and install Help files for the module that includes this cmdlet, use Update-Help.
        -- To view the Help topic for this cmdlet online, type: "Get-Help Get-ChildItem -Online" or
           go to https://go.microsoft.com/fwlink/?LinkID=113308.
```

以下是兩個命令查詢 `git` 的區別：

* `Get-Command git`

```
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Application     git.exe                                            2.30.2.1   C:\Program Files\Git\cmd\git.exe
```

* `Get-Help git`

```
Get-Help : Get-Help could not find git in a help file in this session. To download updated help topics type: "Update-Help". To get help
online, search for the help topic in the TechNet library at https:/go.microsoft.com/fwlink/?LinkID=107116.
At line:1 char:1
+ Get-Help git
+ ~~~~~~~~~~~~
    + CategoryInfo          : ResourceUnavailable: (:) [Get-Help], HelpNotFoundException
    + FullyQualifiedErrorId : HelpNotFound,Microsoft.PowerShell.Commands.GetHelpCommand
```

### 參考資料

* Get-Command
  * https://docs.microsoft.com/zh-tw/powershell/module/microsoft.powershell.core/get-command?view=powershell-7.1

* Get-Command
  > "Get-Command *" 會取得所有 Windows PowerShell 元素以及 Path 環境變數 ($env:path) 中的所有非 Windows PowerShell 檔案。它會將這些檔案歸類為「應用程式」命令類型群組。
  * https://forsenergy.com/zh-tw/windowspowershellhelp/html/8b2b995e-792a-4114-a4e4-f59f29ca1ceb.htm