## md VS mkdir

### 同

在 **Windows 操作系統** 中，`md` 和 `mkdir` 都可以建立 單一或多個 資料夾/目錄。

* 例如：使用 `md a\b\c`
```
PS C:\OnlyForTest\Folder2> md a\b\c


    Directory: C:\OnlyForTest\Folder2\a\b


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         3/30/2021  11:53 AM                c
```

* 例如：使用 `mkdir a\b\c\d`
```
PS C:\OnlyForTest\Folder2> mkdir a\b\c\d


    Directory: C:\OnlyForTest\Folder2\a\b\c


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         3/30/2021  11:56 AM                d
```

### 異

> In DOS, OS/2, Windows and ReactOS, the command is often abbreviated to md.
  * 在 DOS、OS/2、Windows 和 ReactOS，`mkdir` 可縮寫為 `md`
  * 也就是說，有些操作系統只認得 `mkdir`

### 資料來源

* mkdir
  * https://en.wikipedia.org/wiki/Mkdir

* What is the difference between MD and MKDIR batch command?
  * https://stackoverflow.com/questions/32370254/what-is-the-difference-between-md-and-mkdir-batch-command/32372438#:~:text=MKDIR%20%5Bdrive%3A%5Dpath%20MD%20%5Bdrive%3A%5Dpath%20If%20Command,in%20the%20path%2C%20if%20needed.&text=On%20Linux%2FUnix%2FMacOS%2C,platform%2C%20you%20should%20use%20mkdir%20.