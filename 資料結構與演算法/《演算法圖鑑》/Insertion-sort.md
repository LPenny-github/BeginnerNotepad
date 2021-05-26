# Insertion sort / 插入排序

把前方當作已排好的陣列，每個 i 位置對應的數值，都跟 j 位置應對的數值 比較。

```csharp
public int[] InsertionSortFuction(int[] numbers)
{
    for (int i = 1; i < numbers.Length; ++i)
    {
        int j = i - 1;
        int temp = numbers[i];
        while (j >= 0 && temp < numbers[j])
        {                    
            numbers[j+1] = numbers[j];
            --j;
        }
        numbers[j+1] = temp;
    }
    return numbers;
}
```

* runtime = O( N<sup>2</sup> ) <-- 概算


## 參考資料

* 插入排序
  ```c
    void insertion_sort(int arr[], int len){
        int i,j,key;
        for (i=1;i!=len;++i){
                key = arr[i];
                j=i-1;
                while((j>=0) && (arr[j]>key)) {
                        arr[j+1] = arr[j];
                        j--;
                }
                arr[j+1] = key;
        }
    }
  ```
  * https://zh.wikipedia.org/wiki/插入排序