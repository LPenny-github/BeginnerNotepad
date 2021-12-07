# 用 tuple 於方法中傳遞參數

之前使用過 tuple 做 swap，這次學習把 tuple 應用於方法中：

```csharp
using System;

namespace HelloTuple
{
    class Program
    {
        static void Main(string[] args)
        {
            // 可用 `var` 自動推斷型別
            // 沒有特別命名的話， tuple 裡第一個位置叫做 Item1，第二個位置叫做 Item2，以此類推......
            var householdChore1 = ("擦地板", 7); 
            var householdChore2 = ("倒垃圾", 7);

            var result = AreEqualName(householdChore1.Item1, householdChore2.Item1);

            Console.WriteLine(result.message);

            if (!result.valid)
            {
                Console.WriteLine("是否建立新家事？");
            }
            
            
            // 方法回傳值與傳入參數都可以使用 tuple
            (string message, bool valid) AreEqualName(string name1, string name2)
            {
                if (name1.Equals(name2))
                {
                    return ($"家事名稱 ( {name1} & {name2} ) 相同", true);
                }
                return ($"家事名稱 ( {name1} & {name2} ) 不同", false);
            }
        }
    }
}
// Output:
//
// 家事名稱 ( 擦地板 & 倒垃圾 ) 不同
// 是否建立新家事？
```

## 參考資料
  
* Intro to Tuples in C# In 10 Minutes or Less
  * https://youtu.be/QC6hpl2iU0c

* C # 7.0 到 c # 7.3 的新功能
  * https://docs.microsoft.com/zh-tw/dotnet/csharp/whats-new/csharp-7#tuples-and-discards