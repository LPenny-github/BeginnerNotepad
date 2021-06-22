# Quick sort / 快速排序

```csharp
using System;

public class QuickSort
{
    public int[] QuickSort(int[] input, int startIndex, int endIndex)
    {
        if (startIndex < endIndex)
        {
            int pivotIndex = Partition(startIndex, endIndex);

            if (pivotIndex > 1)
            {
                QuickSort(input, startIndex, pivotIndex - 1);
            }
            if (pivotIndex + 1 < endIndex)
            {
                QuickSort(input, pivotIndex + 1, endIndex;                    
            }
        }
        return input;

        int Partition(int startIndex, int endIndex)
        {
            int pivotValue = input[startIndex];

            while (true)
            {
                while (input[startIndex] < pivotValue)
                {
                    ++startIndex;
                }
                while (pivotValue < input[endIndex])
                {
                    --endIndex;
                }

                if (startIndex < endIndex)
                {
                    int temp = input[startIndex];
                    input[startIndex] = input[endIndex];
                    input[endIndex] = temp;
                }
                else
                {
                    return startIndex;
                }
            }
        }
    }
}
```

## 參考資料

* Quicksort
  > Mathematical analysis of quicksort shows that, on average, the algorithm takes O(n log n) comparisons to sort n items. In the worst case, it makes O(n<sup>2</sup>) comparisons, though this behavior is rare.
  * https://en.wikipedia.org/wiki/Quicksort

* C# program to perform Quick sort using Recursion
  * https://www.tutorialspoint.com/chash-program-to-perform-quick-sort-using-recursion