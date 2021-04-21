# File.Move()　VS　Directory.Move()

## 同

File.Move()
```csharp
public static void Move (string sourceFileName, string destFileName);
```

Directory.Move()
```csharp
public static void Move (string sourceDirName, string destDirName);
```

* 兩個方法都是在底層幫你完成 Copy 來源內容至新位置 和 Delete 來源檔案。

* 可以利用這個運作機制來改檔名。

## 異

* File.Move() 只能處理檔案；Directory.Move() 可以處理 檔案 或 資料夾。

* Directory Class VS DirectoryInfo Class
  * Directory Class：適合處理 **一次性**、**大量** 檔案/資料夾
  * DirectoryInfo Class：適合 **多次**、**單一** 檔案/資料夾

## 其他好玩的事情

如果你用 File.Move() 來讀資料夾，那 TERMINAL 就會告訴你（只列第一行）：
```
Unhandled exception. System.IO.FileNotFoundException: Could not find file 'C:\OnlyForTest\Folder7'.
```

不過，若你使用 File.Move() 來讀不存在的檔案，那 TERMINAL 也會告訴你（只列第一行）：
```
Unhandled exception. System.IO.FileNotFoundException: Could not find file 'C:\OnlyForTest\Folder1\Ahahahahahah.txt'.
```

因為 `FileNotFoundException` 的定義單純只是 "sourceFileName was not found." 

而究竟是 檔案不存在/檔名錯誤 或是 根本就不是個檔案，客倌自行判斷 XD

換作是 Directory.Move() 也有類似的狀況。

## 參考資料

* File.Move Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.io.file.move?view=net-5.0#System_IO_File_Move_System_String_System_String_

* Directory.Move(String, String) Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.io.directory.move?view=net-5.0

* NET Directory.Move() vs File.Move()
  * https://stackoverflow.com/questions/33105182/net-directory-move-vs-file-move

* Directory Class
  * https://docs.microsoft.com/en-us/dotnet/api/system.io.directory?view=net-5.0

