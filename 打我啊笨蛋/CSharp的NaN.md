# CSharp 的 NaN


## What

* NaN，Not a Number。
  * 表示未定義（ undefined）或無法代表（unrepresentable）
  * 數值型別
  * 制定於浮點數規格中

* 範例
  * Double 型別的 NaN 使用：
    * 確認是否為 NaN 可用 Double.IsNaN()
    * 比較 NaN 可用 Equals() 或 CompareTo()

  ```cs
  var a = 3.0;
  var b = a / 0;
  var c = b * 10;
  var d = Double.NaN;
  var e = d / 0;
  var f = 0.00;
  var g = f / 0;

  Console.WriteLine("b is " + b);
  Console.WriteLine("c is " + c);
  Console.WriteLine("d is " + d);
  Console.WriteLine("e is " + e);
  Console.WriteLine("g is " + g);
  Console.WriteLine("Double.IsNaN(b) " + Double.IsNaN(b));
  Console.WriteLine("Double.IsNaN(c) " + Double.IsNaN(c));
  Console.WriteLine("Double.IsNaN(d) " + Double.IsNaN(d));
  Console.WriteLine("Double.IsNaN(e) " + Double.IsNaN(e));
  Console.WriteLine("Double.IsNaN(g) " + Double.IsNaN(g));
  Console.WriteLine("b.Equals(c): " + b.Equals(c));
  Console.WriteLine("b.Equals(d): " + b.Equals(d));
  Console.WriteLine("d.Equals(e): " + d.Equals(e));
  Console.WriteLine("e.Equals(g): " + e.Equals(g));
  Console.WriteLine("b.CompareTo(c): " + b.CompareTo(c));
  Console.WriteLine("b.CompareTo(d): " + b.CompareTo(d));
  Console.WriteLine("b.CompareTo(e): " + b.CompareTo(e));
  Console.WriteLine("e.CompareTo(g): " + e.CompareTo(g));

  // b is ∞
  // c is ∞
  // d is NaN
  // e is NaN
  // g is NaN
  // Double.IsNaN(b) False
  // Double.IsNaN(c) False
  // Double.IsNaN(d) True
  // Double.IsNaN(e) True
  // Double.IsNaN(g) True
  // b.Equals(c): True
  // b.Equals(d): False
  // d.Equals(e): True
  // e.Equals(g): True
  // b.CompareTo(c): 0
  // b.CompareTo(d): 1
  // b.CompareTo(e): 1
  // e.CompareTo(g): 0
  ```


## 為什麼 int 的值除以 0 時會拋出錯誤，而不是 NaN？

最簡單的回答：因為 CSharp 的 int 型別沒有如此定義這樣的行為。

* 可以用很多角度來檢視：
  * 數學的世界 VS. 程式語言的世界
    * 數學的世界：只要資源足夠，沒有無法表示的數值
    * 程式語言的世界：權衡
  * 整數 VS. 浮點數
    * 當你使用整數型別，多數時候，那些數字是可以明確地數出來的
  * 程式語言的工程設計
    * **標準** ，即意謂有 歷史包袱、程式語言有別 與 效能/代價 取捨


## 參考資料

* NaN
  * http://en.wikipedia.org/wiki/NaN

* Double.NaN Field
  * http://docs.microsoft.com/en-us/dotnet/api/system.double.nan?view=net-5.0