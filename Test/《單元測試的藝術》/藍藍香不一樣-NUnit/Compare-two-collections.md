#  Compare two collections

* CollectionAssert 提供兩個 IEnumerable 物件比對，其中
  *  AreEqual ：比對內容，包含次序
  *  AreEquivalent ：比對內容， **不** 包含次序
  

```csharp
using System;
using NUnit.Framework;

namespace UnitTests;

[TestFixture]
public class SelectionSortTests
{
    [Test]
    public void Sort1_Array_containAllElements()
    {
        int[] numbers = new []{25,48,10,0,-4,1,88,99,22,4};

        // 選擇排序法（由小排到大）
        SelectionSort selectionSort = new();
        int[] result = selectionSort.Sort1(new []{25,48,10,0,-4,1,88,99,22,4});
        // result = { -4, 0 , 1, 4, 10, 22, 25, 48 ,88, 99 } 

        CollectionAssert.AreEquivalent(numbers, result);
    }

    [Test]
    public void Sort1_Array_sorted()
    {
        int[] numbers = new []{25,48,10,0,-4,1,88,99,22,4};
        Array.Sort(numbers);

        SelectionSort selectionSort = new();
        int[] result = selectionSort.Sort1(new []{25,48,10,0,-4,1,88,99,22,4});

        CollectionAssert.AreEqual(numbers, result);
    }
}
// Output:
//
// Total tests: 2. Passed: 2. Failed: 0. Skipped: 0
```

## 參考資料

* CollectionAssert
  * https://docs.nunit.org/articles/nunit/writing-tests/assertions/classic-assertions/Collection-Assert.html