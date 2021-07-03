# static modifier（修飾詞）


## Example

```cs
public static class Math
```

## Why: 避免被加料

>  The advantage of using a static class is that the compiler can check to make sure that no instance members are accidentally added. The compiler will guarantee that instances of this class cannot be created.

## How

* 特性：

> The following list provides the main features of a static class:
>
> * Contains only static members.
>
> * Cannot be instantiated.
>
> * Is sealed.
>
> * Cannot contain Instance Constructors.

* 注意：

1. 第一次叫用靜態 成員/建構函式 時，（可考慮）先初始化。 <-- 你不做，編輯器最後也會幫你做

1. 靜態類別在叫用後，會保留在記憶體。

## 參考資料

* Static Classes and Static Class Members (C# Programming Guide)
  * https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members

* static (C# Reference)
  * https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/static

* Math Class
  * https://docs.microsoft.com/en-us/dotnet/api/system.math?view=net-5.0