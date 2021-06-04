# ?? and ??= operators 

從 C# 8.0 起， Null 聯合運算子 左邊的操作項不可為

* 可以用於數值變數判斷：

```csharp
int? a = 28;
int b = a ?? -1;
Console.WriteLine($"a is {a}");
Console.WriteLine($"b is {b}");  

int? c = null;
int d = c ?? -1;
Console.WriteLine($"c is {c}");
Console.WriteLine($"d is {d}"); 

// output:
// a is 28
// b is 28
// c is 
// d is -1
```

* 參考型別變數判斷：

```csharp
List<int> numbers = null;
int? a = null;

(numbers ??= new List<int>()).Add(5);
Console.WriteLine(string.Join(" ", numbers));  // output: 5

numbers.Add(a ??= 0);
Console.WriteLine(string.Join(" ", numbers));  // output: 5 0
Console.WriteLine(a);  // output: 0
```

* 也可以用在泛型：

```csharp
private static void Display<T>(T a, T backup)
{
    Console.WriteLine(a ?? backup);
}
```


## 資料來源

* ?? and ??= operators (C# reference)
  > 在 c # 7.3 及更早版本中，運算子左邊運算元的類型 ?? 必須是 參考型別 或 可為 null 的實值型別。 從 c # 8.0 開始，該需求會以下列內容取代：和運算子的左運算元型別 ?? ??= 不能是不可為 null 的實值型別。
  * https://docs.microsoft.com/zh-tw/dotnet/csharp/language-reference/operators/null-coalescing-operator