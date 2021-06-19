# Heap sort / 堆積排序

* runtime = O(N logN)

```csharp
using System.Collections.Generic;

public class HeapSort
{
    public int[] Sort(int[] input)
    {
        if (input.Length <= 1)
        {
            return input;
        }

        BottomUpHeapify(); // O(N)

        Queue<int> output = new Queue<int>(input.Length);
        for (int i = input.Length - 1; 0 <= i; --i)
        {
            output.Enqueue(input[0]);
            input[0] = input[i];
            var index = 0;
            while (0 <= index)
            {
                index = TopDownHeapify(index, i); // O(N logN)
            }
        }

        return output.ToArray();

        int GetParentIndex(int index) => (index - 1) / 2;

        void Swap(int index1, int index2)
        {
            var t = input[index1];
            input[index1] = input[index2];
            input[index2] = t;
        }

        void BottomUpHeapify()
        {
            for (int i = input.Length - 1; 0 <= i; --i)
            {
                var parentIndex = GetParentIndex(i);
                if (input[parentIndex] < input[i])
                {
                    Swap(i, parentIndex);
                }
            }
        }

        int GetLeftChildIndex(int index) => index * 2 + 1;

        int TopDownHeapify(int index, int heapSize)
        {
            var leftChildIndex = GetLeftChildIndex(index);
            if (leftChildIndex < heapSize)
            {
                var childIndex = leftChildIndex;
                var childValue = input[childIndex];
                var rightChildIndex = leftChildIndex + 1;
                if (rightChildIndex < heapSize)
                {
                    var rightChildValue = input[rightChildIndex];
                    if (childValue < rightChildValue)
                    {
                        childIndex = rightChildIndex;
                        childValue = rightChildValue;
                    }
                }
                var myValue = input[index];
                if (myValue <= childValue)
                {
                    Swap(index, childIndex);
                    return childIndex;
                }
            }
            return -1;
        }
    }
}
```

## 參考資料

* 堆積排序
  * https://zh.wikipedia.org/wiki/堆排序