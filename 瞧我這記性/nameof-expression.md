# nameof expression（運算式）

* `nameof(變數名稱)` 會丟出該變數名稱，而非該變數的值。 

```cs
string command = GetArgument(0, nameof(command)).ToLowerInvariant();

string GetArgument(int index, string name)
{
    if (arguments.Length < 1)
    {
        throw new ArgumentNullException(nameof(name), $"Argument `{name}` is empty.");
    }
    return arguments[index];
}
            
// Unhandled exception. System.ArgumentNullException: Argument `command` is empty. (Parameter 'name')
```

* 也可以用 nameof 取得方法名稱或型別名稱

```cs
Console.WriteLine(nameof(System.Collections.Generic));  // output: Generic
Console.WriteLine(nameof(List<int>));  // output: List
Console.WriteLine(nameof(List<int>.Count));  // output: Count
Console.WriteLine(nameof(List<int>.Add));  // output: Add

var numbers = new List<int> { 1, 2, 3 };
Console.WriteLine(nameof(numbers));  // output: numbers
Console.WriteLine(nameof(numbers.Count));  // output: Count
Console.WriteLine(nameof(numbers.Add));  // output: Add
```

## 參考資料

* nameof expression (C# reference)
  * https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/nameof