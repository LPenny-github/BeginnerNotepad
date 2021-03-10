## Array

### 特性

* 若知道搜尋標的 Index，那最佳搜尋時間可以降至 O(1)，否則為線性搜尋 O(n)

* 新增元素或刪除元素牽涉到對資料的複製，最差執行時間為 O(n)

* 支援 BinarySearch


### 範例方法

* Array.GetValue(Index)：找出該 Array 此 Index 的值，最佳執行時間為 O(1)

* Array.IndexOf(Array, Object)：回傳 Array 中第一個符合 Object 的 Index，最差執行時間為 O(n)

* Array.BinarySearch(Array, Object)
  * 使用前提： Array 必須由小到大排序好
  * 接受 Array 有重複元素，回傳 Array 中 **第一次** 遇到符合 Object 的 Index
  * 若回傳的數值為負數，表示沒有找到相符的 Object
  * 最差執行時間為 O(log n)

* Array.Resize<T>(T[],NewSize)：修改 Array 的長度
  * 如果NewSize > 舊 Array 的長度(OldLength)，則另開空間，並複製所有 Array 的元素
  * 如果NewSize < OldLength，則則另開空間，複製 Array 的元素，直到新空間裝不下為止
  * 如果NewSize = OldLength，則這個方法不會做事
  * 最差執行時間為 O(n)，n 指的是 NewSize


### 參考資料

* Array Class
  * https://docs.microsoft.com/en-us/dotnet/api/system.array?view=net-5.0

* Array.GetValue Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.array.getvalue?view=net-5.0#System_Array_GetValue_System_Int32_

* Array.IndexOf Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.array.indexof?view=net-5.0#System_Array_IndexOf_System_Array_System_Object_

* Array.BinarySearch Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.array.binarysearch?view=net-5.0#System_Array_BinarySearch_System_Array_System_Object_

* Array.Resize<T>(T[], Int32) Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.array.resize?view=net-5.0#System_Array_Resize__1___0____System_Int32_