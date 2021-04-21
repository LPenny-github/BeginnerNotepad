# Queue

## 特性

* 像排隊一樣。加入新元素在 Queue 的結尾，取出元素則從 Queue 的起頭開始，也就是 先進先出（First In First Out / FIFO）

* Queue 接受元素為 null，或者 重複的元素

* 底層為 Array

## 範例方法

* Queue<T>.Enqueue(T)：加入新元素在 Queue 的結尾
  * 當 Count < Capacity，runtime 為 O(1)
  * 一旦 Count = Capacity，程式會自動複製全部內容到新的儲存地點，所以 runtime 會成 O(n)

* Queue<T>.Peek：檢視 Queue 結尾的那個元素 **<--這和 Stack 所提供的方法很像**
  * runtime 為 O(1)

* Queue<T>.Dequeue：取出 Queue 結尾的那個元素，並且隨後從 Quequ 中刪除
  * runtime 為 O(1)

* Queue<T>.ToArray：複製 Queue 中的內容到新的 Array 中
  * 新 Array 中的元素順序和 Queue 相同 **<--這和 Stack 所提供的方法相反**
  * runtime 為 O(n)

## 資料來源

* Queue<T> Class
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.queue-1?view=net-5.0

* runtime/src/libraries/System.Collections/src/System/Collections/Generic/Queue.cs
  * https://github.com/dotnet/runtime/blob/v5.0.3/src/libraries/System.Collections/src/System/Collections/Generic/Queue.cs

* Queue<T>.Enqueue(T) Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.queue-1.enqueue?view=net-5.0#System_Collections_Generic_Queue_1_Enqueue__0_

* Queue<T>.Peek Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.queue-1.peek?view=net-5.0#System_Collections_Generic_Queue_1_Peek

* Queue<T>.Dequeue Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.queue-1.dequeue?view=net-5.0#System_Collections_Generic_Queue_1_Dequeue

* Queue<T>.ToArray Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.queue-1.toarray?view=net-5.0#System_Collections_Generic_Queue_1_ToArray