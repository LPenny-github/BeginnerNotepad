# `params` keyword for parameter

* 不確定個數的一維陣列參數
* 用 `,` 分隔每個值

* 注意：
  * 每個方法只能有一個 `params`
  * `params` 參數之後不能有其他參數
  * `params` 參數必須是一維陣列，否則會出現編譯錯誤 CS0225 （params 參數必須是單一維度陣列）
  * 若沒有傳入任何引數， `params` 陣列長度為 0
  

## 範例

```cs
static void Main(string[] args)
{
    Console.WriteLine(TotalAmount(275, 322, 50));  
    Console.WriteLine(TotalAmount(399, 278, 15, 20));

    // Output:
    // 707
    // 712
}

public static int TotalAmount(params int[] cart)
{
    int totalAmount = 0;
    const int shippingFee = 60;
    const int freeShippingThreshold = 699;
    
    foreach (var item in cart)
    {
        totalAmount += item;
    }

    if (totalAmount < freeShippingThreshold)
    {
        totalAmount += shippingFee;
    }

    return totalAmount;
}
```

## 參考資料

* params (C# 參考)
  * https://docs.microsoft.com/zh-tw/dotnet/csharp/language-reference/keywords/params

* 編譯器錯誤 CS0225
  * https://docs.microsoft.com/zh-tw/dotnet/csharp/misc/cs0225