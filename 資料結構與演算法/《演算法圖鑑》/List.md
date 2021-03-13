## List

### 特性

* List 內成員可為 null，且 List 可接受重複元素

* linear search 線性搜尋  （/ˈlɪn.i.ɚ/）

* 底層為 Array
  * 當 Count < Capasity 時，想加入新物件於最末，電腦用運算的方式找出新物件應該被放在哪裡：
    * newObjectPosition = firstObjectPosition + newObjectIndex * perObjectPosition
    * 此時的 runtime 為 Ω(1)
    
* 注意：一旦當 Count = Capasity，程式會自動複製 List 的內容到 新的位址，此時的 runtime 將為 O(n) 

### 範例方法
* List<T>.Contains(T)：線性搜尋， runtime 為 O(n)

* List<T>.Add(T)
  * 一旦 Count = Capasity， runtime 將為 O(n)
  * 當 Count < Capasity 時，想加入新物件於最末， runtime 為 Ω(1)
  * 也可以這樣說：List<T>.Add(T) 最佳表現是 Ω(1)，最差表現是 O(n)

* List<T>.Remove(T)：線性搜尋， runtime 為 O(n)

### 引用資料
* List 底層為 Array 
  * https://github.com/dotnet/runtime/blob/v5.0.3/src/libraries/System.Private.CoreLib/src/System/Collections/Generic/List.cs

* List<T> Class 
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1?view=net-5.0

* List<T>.Contains(T) Method 
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.contains?view=net-5.0#System_Collections_Generic_List_1_Contains__0_

* List<T>.Add(T) Method 
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.add?view=net-5.0#System_Collections_Generic_List_1_Add__0_

* List<T>.Remove(T) Method 
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.remove?view=net-5.0#System_Collections_Generic_List_1_Remove__0_
  
      
