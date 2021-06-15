# Heap sort / 堆積排序

* runtime = O(N logN)

```csharp
public class HeapSort1
{
    // int[] input = new int[] { 2, 4, 9, 3, 5 }
    public int[] HeapSortFuction(int[] input)
    {
        BottomUp(input);
        TopDown(input);
        return input;
    }

    // output: 9  5  2  3  4  
    int[] BottomUp(int[] input)
    {
        if (input.Length <= 1) { return input; }
        for (int i = input.Length - 1; i >= 1; --i)
        {
            int parentIndex = GetParentIndex(i);
            if (input[parentIndex] < input[i])
            {
                Swap(parentIndex, i, input);
            }
        }
        return input;

        int GetParentIndex(int index) => (index - 1) / 2;
    }

    void Swap(int index1, int index2, int[] input)
    {
        int temp = input[index1];
        input[index1] = input[index2];
        input[index2] = temp;
    }

    // output: 2  3  4  5  9  
    int[] TopDown(int[] input)
    {
        if (input.Length <= 1) { return input; }
        for (int i = input.Length - 1; i >= 1; --i)
        {
            int index = 0;
            Swap(index, i, input);
            while (index >= 0)
            {
                index = TopDownHeapify(index, i);
            }
        }
        return input;

        int GetLeftChildIndex(int parentIndex) => (parentIndex * 2) + 1;

        int TopDownHeapify(int parentIndex, int heapSize)
        {
            int leftChildIndex = GetLeftChildIndex(parentIndex);
            if (leftChildIndex < heapSize)
            {
                int childIndex = leftChildIndex;
                int childValue = input[leftChildIndex];
                int rightChildIndex = leftChildIndex + 1;
                if (rightChildIndex < heapSize)
                {
                    int rightChildValue = input[rightChildIndex];
                    if (childValue < rightChildValue)
                    {
                        childIndex = rightChildIndex;
                        childValue = rightChildValue;
                    }
                }
                if (input[parentIndex] < childValue)
                {
                    Swap(parentIndex, childIndex, input);
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