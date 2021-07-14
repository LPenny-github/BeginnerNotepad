# Enumerable.SequenceEqual()

```cs
public static bool SequenceEqual<TSource> (
    this System.Collections.Generic.IEnumerable<TSource> first, 
    System.Collections.Generic.IEnumerable<TSource> second);
```

```cs
public static bool SequenceEqual<TSource> (
    this System.Collections.Generic.IEnumerable<TSource> first, 
    System.Collections.Generic.IEnumerable<TSource> second, 
    System.Collections.Generic.IEqualityComparer<TSource>? comparer);
```

* 用在可以一個一個拿出來比較的情景。

* IEqualityComparer 裡面有兩個方法： GetHashCode 和 Equals。可藉由改寫這兩個方法，讓程式照你的意思比對物件。

* 如果沒有給予第三個參數（comparer），那就會根據當個物件的型別已經默認的規格做比對，例如：
  * 如果 first 和 second 都是 int[]，默認的規格 int（數值型別） 會比較 **值**
  * 如果 first 和 second 都是 int[]，默認的規格 int（數值型別） 會比較 **值**
  * 如果 first 和 second 都是 List<object>，默認的規格 object（參考型別） 會比較 **參考**


```cs
using System;
using System.Collections.Generic;
using System.Linq;

namespace HelloWorld
{
    class Program
    {
        public class CustomerData
        {
            public string Name { get; set; }
            public int Age { get; set; }
        }
        static void Main(string[] args)
        {
            int[] a = new int[] { 1, 3, 5 };
            int[] b = new int[] { 1, 3, 5 };

            Console.WriteLine("a, b {0} equal.", Enumerable.SequenceEqual(a, b) ? "are" : "are not");

            b[1] = 10;
            Console.WriteLine("a, b {0} equal.", Enumerable.SequenceEqual(a, b) ? "are" : "are not");

            CustomerData c = new CustomerData() { Name = "Penny", Age = 88 };
            CustomerData d = new CustomerData() { Name = "Fenny", Age = 99 };

            List<CustomerData> e = new List<CustomerData> { c, d };
            List<CustomerData> f = new List<CustomerData> { c, d };
            List<CustomerData> g = new List<CustomerData> { c, new CustomerData { Name = "Fenny", Age = 99 } };

            Console.WriteLine("e, f {0} equal.", Enumerable.SequenceEqual(e, f) ? "are" : "are not");
            Console.WriteLine("e, g {0} equal.", Enumerable.SequenceEqual(e, g) ? "are" : "are not");

            // Output:
            // a, b are equal.
            // a, b are not equal.
            // e, f are equal.
            // e, g are not equal.
        }
    }
}
```

## 參考資料

* Enumerable.SequenceEqual Method
  ```cs
  public class ProductA: IEquatable<ProductA>
  {
    public string Name { get; set; }
    public int Code { get; set; }

    public bool Equals(ProductA other)
    {
        if (other is null)
            return false;

        return this.Name == other.Name && this.Code == other.Code;
    }

    public override bool Equals(object obj) => Equals(obj as ProductA);
    public override int GetHashCode() => (Name, Code).GetHashCode();
  }
  ```
  ```cs
  ProductA[] storeA = { new ProductA { Name = "apple", Code = 9 },
                       new ProductA { Name = "orange", Code = 4 } };

  ProductA[] storeB = { new ProductA { Name = "apple", Code = 9 },
                       new ProductA { Name = "orange", Code = 4 } };

  bool equalAB = storeA.SequenceEqual(storeB);

  Console.WriteLine("Equal? " + equalAB);

  /*
    This code produces the following output:

    Equal? True
  */
  ```

  * https://docs.microsoft.com/en-us/dotnet/api/system.linq.enumerable.sequenceequal?view=net-5.0#System_Linq_Enumerable_SequenceEqual__1_System_Collections_Generic_IEnumerable___0__System_Collections_Generic_IEnumerable___0__System_Collections_Generic_IEqualityComparer___0__

