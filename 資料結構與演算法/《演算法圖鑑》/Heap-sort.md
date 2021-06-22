# Heap sort / 堆積排序

* runtime = O(N logN)

```csharp
public class HeapSort
{
    public int[] Sort(int[] input)
    {
        BottomUpHeapify();
        for (int limit = input.Length - 1; limit >= 1; --limit)
        {
            Swap(limit, 0);
            TopDownHeapify(limit, 0);
        }
        return input;

        void BottomUpHeapify()
        {
            for (int parentIndex = input.Length / 2 - 1; parentIndex >= 0; --parentIndex)
            {
                TopDownHeapify(input.Length, parentIndex);
            }
        }

        void Swap(int index1, int index2)
        {
            int temp = input[index1];
            input[index1] = input[index2];
            input[index2] = temp;
        }

        void TopDownHeapify(int length, int parentIndex)
        {
            int largestIndex = parentIndex;
            int leftChildIndex = parentIndex * 2 + 1;
            int rightChildIndex = parentIndex * 2 + 2;

            if (leftChildIndex < length && input[leftChildIndex] > input[largestIndex])
            {
                largestIndex = leftChildIndex;
            }

            if (rightChildIndex < length && input[rightChildIndex] > input[largestIndex])
            {
                largestIndex = rightChildIndex;
            }

            if (largestIndex != parentIndex)
            {
                Swap(largestIndex, parentIndex);
                TopDownHeapify(length, largestIndex);
            }
        }
    }
}
```

## 參考資料

* 堆積排序
  * https://zh.wikipedia.org/wiki/堆排
  
* Heap Sort - The Sorting Algorithm Family Reunion
  * https://exceptionnotfound.net/heap-sort-csharp-the-sorting-algorithm-family-reunion/