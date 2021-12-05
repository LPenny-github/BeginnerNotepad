# Selection sort / 選擇排序

跟 Bubble sort 很像，但 Selection sort 是只跟目標對象交換

```csharp
public int[] SelectionSortFuction(int[] numbers)
{
    for (int i = 0; i <= numbers.Length - 1; ++i)
    {
        for (int j = numbers.Length - 1; j > i; --j)
        {
            // 只要找到比 numbers[i] 更小的數字就立即對換
            if (numbers[j] < numbers[i])
            {
                int temp = numbers[j];
                numbers[j] = numbers[i];
                numbers[i] = temp;
            }
        }
    }
    return numbers;
}
```

或是

```csharp
public int[] SelectionSortFuction2(int[] numbers)
{
    for (int i = 0; i <= numbers.Length - 1; ++i)
    {
        // 用一個變數儲存最小值的 index，然後再視需要對換
        int minIndex = i;
        for (int j = numbers.Length - 1; j > i; --j)
        {
            if (numbers[j] < numbers[minIndex])
            {
                minIndex = j;
            }
        }
        if (minIndex != i)
        {
            int temp = numbers[i];
            numbers[i] = numbers[minIndex];
            numbers[minIndex] = temp;
        }
    }
    return numbers;
}
```

或 更直觀：

```csharp

// runtime = n(n-1)
public int[] SelectionSortFuction3(int[] numbers)
{
    for (int firstPointer = 0; firstPointer < numbers.Length -1; ++firstPointer)
    {
        int minIndex = firstPointer;
                
        for (int secondPointer = firstPointer + 1; secondPointer < numbers.Length; ++secondPointer)
        {
            if (numbers[secondPointer] < numbers[minIndex])
            {
                minIndex = secondPointer;
            }
        }

        if (minIndex != firstPointer)
        {
            (numbers[firstPointer], numbers[minIndex]) = (numbers[minIndex], numbers[firstPointer]);
        }
    }
    return numbers;
}
```

* runtime = O( N<sup>2</sup> ) <-- 概算


## 參考資料

* 選擇排序
  ```c
  void selection_sort(int a[], int len) 
  {
    int i,j,temp;

	for (i = 0 ; i < len - 1 ; i++) 
    {
		int min = i;
		for (j = i + 1; j < len; j++)     //走訪未排序的元素
		{
			if (a[j] < a[min])    //找到目前最小值
			{
				min = j;    //紀錄最小值的 index
			}
		}
		if(min != i)
		{
		  temp=a[min];  //交換兩個變數
		  a[min]=a[i];
		  a[i]=temp;
		}
	   	/* swap(&a[min], &a[i]);  */   //做交換
	}
  }

  /*
  void swap(int *a,int *b) //交換兩個變數
  {
    int temp = *a;
    *a = *b;
    *b = temp;
  }
  */
  ```
  * https://zh.wikipedia.org/wiki/选择排序