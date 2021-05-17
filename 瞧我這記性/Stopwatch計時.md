# Stopwatch 計時

計算執行某個程式耗費多少時間


## 常用方法

* `Start()` 、 `Stop()`

* `Restart()` 關掉原有的計時、歸零，並且重新啟動計時


## 常用參數

* `Elapsed` 執行時間

* `ElapsedMilliseconds` 以毫秒為單位的執行時間


## 範例

```csharp
var stopwatch1 = new Stopwatch();
stopwatch1.Start();
new Lesson1().FindNumber(); // 執行你想計時的程式
stopwatch1.Stop();
Console.WriteLine("方法一花費時間：" + stopwatch1.Elapsed); // 方法一花費時間：00:00:00.0012229
Console.WriteLine("方法一花費時間：" + stopwatch1.ElapsedMilliseconds); // 方法一花費時間：1

```


## 參考資料

* Stopwatch Class
  > Namespace: System.Diagnostics
  * https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.stopwatch?view=net-5.0