# Char[] to String


```cs
using System;

namespace Hello007
{
    class Program
    {
        static void Main(string[] args)
        {
            char[] a = { '其', '實', '我', '是', '一', '個', '演', '員' };
            string b = new string(a);
            string c = string.Join("", a); // 若想加入分隔符號
            string d = string.Concat(a);   // 若想搭配 LINQ 

            Console.WriteLine($"This is {nameof(b)}: {b}");
            Console.WriteLine($"This is {nameof(c)}: {c}");
            Console.WriteLine($"This is {nameof(d)}: {d}");

            // Output:
            // This is b: 其實我是一個演員
            // This is c: 其實我是一個演員
            // This is d: 其實我是一個演員
        }
    }
}
```


## 參考資料

* .NET / C# - Convert char[] to string
  * https://stackoverflow.com/questions/1324009/net-c-sharp-convert-char-to-string

* String.Join Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.string.join?view=net-5.0#code-try-20

* String.Concat Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.string.concat?view=net-5.0#System_String_Concat__1_System_Collections_Generic_IEnumerable___0__