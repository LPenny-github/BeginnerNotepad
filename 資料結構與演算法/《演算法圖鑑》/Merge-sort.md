# Merge sort / 合併排序

拆成兩兩一組，小的在前、大的在後，不足二則直接晉級上一層。接著是四個一組、八個一組……直到全部排列完成。

* runtime = O( N log N ) <-- 概算
  * 每層有 N 個要排 * 共有 log<sub>2</sub>N 層

```csharp
using System;
using System.Collections.Generic;
using static System.Math;

namespace ConsoleApp
{
    public class MergeSort
    {
        public int[] MergeSortFuction(int[] input)
        {
            if (input.Length <= 1) { return input; }
            int batchSize = 2;
            List<int> output = new List<int>(input.Length);
            while (true)
            {
                for (int startIndex = 0; startIndex < input.Length; startIndex += batchSize)
                {
                    Sort(startIndex, batchSize);
                }
                Array.Copy(output.ToArray(), input, input.Length);
                output.Clear();
                if (batchSize > input.Length)
                {
                    break;
                }
                batchSize *= 2;
            }
            return input;

            void Sort(int startIndex, int batchSize)
            {
                int startIndex1 = startIndex;
                int startIndex2 = startIndex + batchSize / 2;
                int midIndex = Min(startIndex2, input.Length);
                int endIndex = Min(startIndex + batchSize, input.Length);

                while (startIndex1 < midIndex && startIndex2 < endIndex)
                {
                    if (input[startIndex1] <= input[startIndex2])
                    {
                        output.Add(input[startIndex1]);
                        ++startIndex1;
                    }
                    else
                    {
                        output.Add(input[startIndex2]);
                        ++startIndex2;
                    }
                }

                while (startIndex1 < midIndex)
                {
                    output.Add(input[startIndex1]);
                    ++startIndex1;
                }

                while (startIndex2 < endIndex)
                {
                    output.Add(input[startIndex2]);
                    ++startIndex2;
                }
            }
        }
    }
}
```


## 參考資料

* 合併排序
  * https://zh.wikipedia.org/wiki/归并排序#C#