## Stack

### 特性

* 適合短期儲存、看完即扔的資料，由你想拿到資料的順序
  * in the same order: Queue
  * in the reverse order: Stack

* 先儲存的元素會在 Stack 的底部，後儲存的元素會在 Stack 的頂部（top），所以是 **先進後出**（Last In First Out / LIFO）

* 底層為 Array

### 範例方法

* Stack<T>.Push(T)：在 Stack 的上方（top）加入一個元素
  * 當 Count < Capacity，runtime 為 O(1)
  * 一旦 Count = Capacity，程式會自動複製全部元素到新的儲存地點，所以 runtime 會成 O(n)

* Stack<T>.Peek：取出 Stack 最上方（/ top）的元素，但不移除
  * runtime 為 O(1)

* Stack<T>.Pop：取出 Stack 最上方（/ top）的元素，且隨後從 Stack 中移除
  * runtime 為 O(1)

* Stack<T>.ToArray：複製 Stack 中的內容到新的 Array 中
  * 複製的順序是由 Stack 的 top 開始，一路往下
  * 如果 Stack 的儲存順序為 A B C D，那 Array 自 Index = 0 的排序會是 D C B A 
  * runtime 為 O(n)

### 參考資料

* Stack<T> Class
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.stack-1?view=net-5.0

* dotnet/runtime/src/libraries/System.Collections/src/System/Collections/Generic/Stack.cs 
  * https://github.com/dotnet/runtime/blob/v5.0.3/src/libraries/System.Collections/src/System/Collections/Generic/Stack.cs

* Stack<T>.Push(T) Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.stack-1.push?view=net-5.0#System_Collections_Generic_Stack_1_Push__0_

* Stack<T>.Peek Method
  https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.stack-1.peek?view=net-5.0#System_Collections_Generic_Stack_1_Peek

* Stack<T>.Pop Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.stack-1.pop?view=net-5.0#System_Collections_Generic_Stack_1_Pop

* Stack<T>.ToArray Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.stack-1.toarray?view=net-5.0#System_Collections_Generic_Stack_1_ToArray

