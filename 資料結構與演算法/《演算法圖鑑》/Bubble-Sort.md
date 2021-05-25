# Bubble Sort / 氣泡排序 / 泡沫排序

```csharp
// 我自己寫的，例如 即時顯示遊戲排行榜
public int[] BubbleSortFuction(int[] numbers)
{
    for (int i = 0; i <= numbers.Length - 1; ++i)
    {
        // 由後往前推送，小的往前
        for (int j = numbers.Length - 1; j > i; --j)
        {
            if (numbers[j] < numbers[j-1])
            {
                int temp = numbers[j];
                numbers[j] = numbers[j-1];
                numbers[j-1] = temp;
            }
        }
    }
return numbers;
}
```

* runtime = O( N<sup>2</sup> ) <-- 概算

## 參考資料

* 泡沫排序
  ```csharp
  private int[] BubbleSort(int[] array)
  {
    var temp = 0;

    for (int i = 0; i < array.Length; i++)
    {
        for (int j = 0; j < array.Length - 1 - i; j++)
        {
            if (array[j] > array[j + 1])
            {
                temp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = temp;
            }
        }
    }

    return array;
  }
  ```
  * https://zh.wikipedia.org/wiki/冒泡排序#C#