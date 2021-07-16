# Enumerable.Reverse VS. Enumerable.OrderByDescending

* 有許多容器，像是 Array、List、Queue......都有實作 `IEnumerable` 這個介面。

* `Enumerable.Reverse` 是直接把內容物的順序直接倒過來，而 `Enumerable.OrderByDescending` 會有排序的動作。

## 範例

* 簡單版

```cs
int[] a = new int[] { 1, 4, 3 };
IEnumerable b = a.Reverse();
IEnumerable c = a.OrderByDescending(item => item);

Print("original Array", a);
Print("b", b);
Print("c", c);

void Print(string title, IEnumerable output)
{
    Console.WriteLine($"This's {title}:");

    foreach (var item in output)
    {
        Console.WriteLine(item);
    }
    Console.WriteLine("----");
}

    // This's original Array:
    // 1
    // 4
    // 3
    // ----
    // This's b:
    // 3
    // 4
    // 1
    // ----
    // This's c:
    // 4
    // 3
    // 1
    // ----
```

* 自訂類別
```cs
using System;
using System.Linq;

namespace HelloHousework
{
    public class HouseworkToDoList
    {
        public DateTime date;
        public string Item;
    }
    static class Program
    {
        static void Main(string[] args)
        {
            HouseworkToDoList[] weeklyToDo =
                            {new HouseworkToDoList
                                {date = Convert.ToDateTime("2021/7/10"), Item = "洗衣服"},
                             new HouseworkToDoList
                                {date = Convert.ToDateTime("2021/7/12"), Item = "整理"},
                             new HouseworkToDoList
                                {date = Convert.ToDateTime("2021/7/11"), Item = "收衣服"},
                             new HouseworkToDoList
                                {date = Convert.ToDateTime("2021/7/14"), Item = "倒垃圾"}
                            };

            weeklyToDo.Print("Nothing. It's original Array.");

            HouseworkToDoList[] result1 = weeklyToDo.Reverse().ToArray();
            result1.Print("Enumerable.Reverse");

            HouseworkToDoList[] result2 = weeklyToDo.OrderByDescending(subject => subject.date).ToArray();
            result2.Print("Enumerable.OrderByDescending");

            /*
            Output:
            
            使用 Nothing. It's original Array.：
            07-10, 洗衣服
            07-12, 整理
            07-11, 收衣服
            07-14, 倒垃圾
            ------
            使用 Enumerable.Reverse：
            07-14, 倒垃圾
            07-11, 收衣服
            07-12, 整理
            07-10, 洗衣服
            ------
            使用 Enumerable.OrderByDescending：
            07-14, 倒垃圾
            07-12, 整理
            07-11, 收衣服
            07-10, 洗衣服
            ------
            */

        }
        static void Print(this HouseworkToDoList[] output, string explination)
        {
            Console.WriteLine($"使用 {explination}：");
            foreach (var item in output)
            {
                Console.WriteLine(item.date.ToString("MM-dd") + ", " + item.Item);
            }
            Console.WriteLine("------");
        }
    }
}
```

## 參考資料

* Enumerable.Reverse<TSource>(IEnumerable<TSource>) Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.linq.enumerable.reverse?view=net-5.0

* Enumerable.OrderByDescending
  * https://docs.microsoft.com/en-us/dotnet/api/system.linq.enumerable.orderbydescending?view=net-5.0

* IEnumerable Interface
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.ienumerable?view=net-5.0