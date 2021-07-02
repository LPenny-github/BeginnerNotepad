# TimeSpan.Days VS. TimeSpan.TotalDays

* `TimeSpan.Days` 回傳結果為整數，因為該方法只是把 TimeSpan 變數中的 `天` 取出來；相對 `TimeSpan.TotalDays` 就是把時間以 `天` 為單位做換算的結果。

```cs
DateTime a = DateTime.Now;
DateTime b = DateTime.Now.AddDays(5);

var result1 = b.Subtract(a).Days;
var result2 = b.Subtract(a).TotalDays;

Console.WriteLine($"b = {b}");
Console.WriteLine($"result1's type = {result1.GetType().Name};  result1's value = {result1}");
Console.WriteLine($"result2's type = {result2.GetType().Name}; result2's value = {result2}");

// b = 7/7/2021 10:49:23 AM
// result1's type = Int32;  result1's value = 5
// result2's type = Double; result2's value = 5.000000016092593
```

## 參考資料

* TimeSpan.Days Property
  > A TimeSpan value can be represented as [-]d.hh:mm:ss.ff, where the optional minus sign indicates a negative time interval, the d component is days, hh is hours as measured on a 24-hour clock, mm is minutes, ss is seconds, and ff is fractions of a second. The value of the Days property is the day component, d.
  * https://docs.microsoft.com/en-us/dotnet/api/system.timespan.days?view=net-5.0

* TimeSpan.TotalDays
  * https://docs.microsoft.com/en-us/dotnet/api/system.timespan.totaldays?view=net-5.0

* C# 如何取得兩個 DateTime 日期之間的天數
  * https://blog.miniasp.com/post/2008/01/22/Find-the-difference-between-two-DateTime