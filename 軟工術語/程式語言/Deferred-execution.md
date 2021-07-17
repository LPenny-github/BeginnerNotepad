# Deferred Execution / 延遲執行


## Why 

* 等到（程式覺得）真正需要時才執行查詢，避免不需要的浪費。

> Deferred execution means that the evaluation of an expression is delayed until its realized value is actually required. It greatly improves performance by avoiding unnecessary execution.

* （程式覺得）真正需要時：呼叫 `GetEnumerator`、 使用 `foreach` ......

> This method is implemented by using deferred execution. The immediate return value is an object that stores all the information that is required to perform the action. The query represented by this method is not executed until the object is enumerated either by calling its `GetEnumerator` method directly or by using `foreach` in Visual C# or `For Each` in Visual Basic.


## 範例

```cs
using System;
using System.Collections.Generic;
using System.Linq;

namespace HelloWorld
{
    class Program
    {
        public class MathTestResult
        {
            public string Name;
            public int Score;
        }
        static void Main(string[] args)
        {
            var results = new List<MathTestResult>{
                            new MathTestResult{Name = "Nancy", Score = 55},
                            new MathTestResult{Name = "Ambor", Score = 80},
                            new MathTestResult{Name = "Rubby", Score = 73}
                            };

            var passMathTestStudents = results.Where(studentItem => studentItem.Score > 60);

            results.Add(new MathTestResult { Name = "Tony", Score = 92 });

            foreach (var item in passMathTestStudents) // 由於此時才開始執行 LINQ，所以 Output 有 `Tony`
            {
                Console.WriteLine(item.Name);
            }

            // Output:
            // Ambor
            // Rubby
            // Tony
        }
    }
}
```


## 等等，我個性很急，要立馬查詢（immediate query）

把這行：

```cs
var passMathTestStudents = results.Where(studentItem => studentItem.Score > 60);
```
加上 `ToList()` 或是 `ToArray()` ，這樣一來 Output 就不會有 `Tony` 了。

（當然 passMathTestStudents 的型別會因此改變，但在範例這樣單純的情境中不必顧慮）

```cs
var passMathTestStudents = results.Where(studentItem => studentItem.Score > 60).ToList();
```

因為 `ToList()` 和 `ToArray()` 都會強制立即查詢：

> The `ToArray<TSource>(IEnumerable<TSource>)` method forces immediate query evaluation and returns an array that contains the query results. 

> The `ToList<TSource>(IEnumerable<TSource>)` method forces immediate query evaluation and returns a `List<T>` that contains the query results. You can append this method to your query in order to obtain a cached copy of the query results.
>
> `ToArray` has similar behavior but returns an array instead of a `List<T>`.


## 參考資料

* Deferred Execution of LINQ Query
  * https://www.tutorialsteacher.com/linq/linq-deferred-execution

* Enumerable.ToArray<TSource>(IEnumerable<TSource>) Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.linq.enumerable.toarray?view=net-5.0

* Enumerable.ToList<TSource>(IEnumerable<TSource>) Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.linq.enumerable.tolist?view=net-5.0