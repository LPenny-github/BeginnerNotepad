## 時間複雜度 VS 空間複雜度

### 時間複雜度（Time complexity）

* 執行一個程式所需要的時間，使用 big O 表達
  * 例如：List<T>.Remove(T) runtime 為 O(n)

### 空間複雜度（Space Complexity）

* 執行一個程式所需要的空間，使用 big O 表達
  * 例如：以下的函式 空間複雜度 為 O(1)

```csharp
function(int n)
{
    for(int i=0;i<n;i++)
    {
        print(i);
    }
}
```

### 時間複雜度 VS 空間複雜度

* 都用 big O 表達，會不會搞混？
  * 不會。
    * 不特別指定的話， big O 通常指的是 時間複雜度，例如：.NET 文件
    * 要指名空間複雜度時，會特地說出 **空間複雜度** 或 **Space Complexity**

### 資料來源

* 資料結構筆記(一)：演算法、時間複雜度、空間複雜度
  * https://noob.tw/data-structure/