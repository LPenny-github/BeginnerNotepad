# 用 tuple 做 swap

* 舊方法：

```csharp
int temp = input[index1];
input[index1] = input[index2];
input[index2] = temp;
```

* 新支援（其實已經不 **新** 了 😅）：

```csharp
int x = 56;
int y = 77;
Console.WriteLine($"original: x = {x}, y = {y}");
(x, y) = (y, x);
Console.WriteLine($" swapped: x = {x}, y = {y}");

// Output:
// original: x = 56, y = 77
//  swapped: x = 77, y = 56
```

## 參考資料

* C # 7.0 到 c # 7.3 的新功能
  * https://docs.microsoft.com/zh-tw/dotnet/csharp/whats-new/csharp-7#tuples-and-discards