# A value of type '<null>' cannot be used as a default parameter because there are no standard conversions to type 'DateTime' [housework-manager]csharp(CS1750)

```csharp
public class Data
{
    public int frequency;
    DateTime? lastDate;
    DateTime? nextDate;
    public Data(int frequency = 0, DateTime? lastDate = null, DateTime nextDate = null) 
    // Error: `DateTime nextDate = null`
    {
        this.frequency = frequency;
        this.lastDate = lastDate;
        this.nextDate = nextDate;
    }
}
```

## 那 DateTime 的 default 值 是什麼咧

是 `1/1/0001 12:00:00 AM`

```csharp
using System;

public class Program
{
	public static void Main()
	{
		DateTime dt1 = new DateTime(); 
		Console.WriteLine(dt1); // 1/1/0001 12:00:00 AM

		DateTime dt2 = new DateTime(2015, 12, 31);
		Console.WriteLine(dt2); // 12/31/2015 12:00:00 AM

		DateTime dt3 = new DateTime(2015, 12, 31, 5, 10, 20);
		Console.WriteLine(dt3); // 12/31/2015 5:10:20 AM

		DateTime dt4 = new DateTime(2015, 12, 31, 5, 10, 20, DateTimeKind.Utc);
		Console.WriteLine(dt4); // 12/31/2015 5:10:20 AM
	}
}
```


## 那 `DateTime? lastDate = null` 為什麼不會壞掉咧

因為 `?` 表示這個變數是 nullable。


## 那我可以把 `DateTime? lastDate = null` 改成 `DateTime? lastDate` 嗎

如果你直接改成下面這樣，會出現另一個錯誤訊息：Optional parameters must appear after all required parameters

```csharp
public Data(int frequency = 0, DateTime? lastDate, DateTime? nextDate) 
// Error: `int frequency = 0, DateTime? lastDate, DateTime? nextDate`
{
    // ...
}
```

如果使用者沒有給 `frequency` 參數的話，就可以使用 `0` 所以是 `Optional parameters`；而，使用者必須給個交代的 `lastDate` 和 `nextDate` 就是 `required parameters` 。 

C# 語法規定 `required parameters` 要擺在 `Optional parameters` 的前面，所以（為了消弭錯誤）會寫成：

```csharp
public Data(DateTime? lastDate, DateTime? nextDate, int frequency = 0)
{
    // ...
}
```


## 資料來源

* Working with Date and Time in C#
  * https://www.tutorialsteacher.com/csharp/csharp-datetime

* Nullable value types (C# reference)
  * https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/nullable-value-types