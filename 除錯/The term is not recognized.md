##  The term '>' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.

### 情境

我打開 Windows PowerShell，輸入：

```
PS C:\Users\coldb\myHome\HelloCsharp9.0> echo `System.Console.WriteLine("Hello C# 9.0");`  > Program.cs

System.Console.WriteLine
Hello C# 9.0

> : The term '>' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if
a path was included, verify that the path is correct and try again.
At line:1 char:51
+ echo `System.Console.WriteLine("Hello C# 9.0");`  > Program.cs
+                                                   ~
    + CategoryInfo          : ObjectNotFound: (>:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

### 發生什麼事

**我把 ` 和 ' 搞混了**

` 這是 tab 上面那顆鍵。
' 這是單引號。

` 在 CLI 中是換行指令，所以輸出換行了，變成：

```
System.Console.WriteLine
Hello C# 9.0
```

應該使用 單引號 去包整個字串，正確輸入應該是：

`echo 'System.Console.WriteLine("Hello C# 9.0");'  > Program.cs`