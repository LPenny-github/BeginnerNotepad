## foreach VS ListT.ForEach()

### 同

1. 兩個都可以把 List 中的物件，逐一取出。

2. 都不允許 更改物件 或 變動 List 長度。

### 異

主要是寫法上有差異 XD

* List<T>.ForEach() 的範例程式碼：

```
List<String> names = new List<String>();
names.Add("Bruce");
names.Add("Alfred");
names.Add("Tim");
names.Add("Richard");

// 第一種寫法
names.ForEach(Print);

void Print(string s)
{
    Console.WriteLine(s);
}

// 第二種寫法
names.ForEach(delegate(String name)
{
    Console.WriteLine(name);
});
```

### 為什麼電腦知道我改了 List 裡面的內容

因為底層的 _version 變數會記錄 List 的版本。

* List<T>.ForEach() 底層：

```
public void ForEach(Action<T> action)
{
    if (action == null)
    {
        ThrowHelper.ThrowArgumentNullException(ExceptionArgument.action);
    }

    // 當你對 List 進行 CRUD 時，底層會記錄 version 改變。因此你會被抓包。
    int version = _version;

    for (int i = 0; i < _size; i++)
    {
        if (version != _version)
        {
            break;
        }
        action(_items[i]);
    }

    if (version != _version)
       ThrowHelper.ThrowInvalidOperationException_InvalidOperation_EnumFailedVersion();
}
```

* List<T>.Add 底層：

```
[MethodImpl(MethodImplOptions.AggressiveInlining)]
public void Add(T item)
{
    _version++; // YO~就是這行
    T[] array = _items;
    int size = _size;
    if ((uint)size < (uint)array.Length)
    {
        _size = size + 1;
        array[size] = item;
    }
    else
    {
        AddWithResize(item);
    }
}
```

### 資料來源：

* foreach, in (C# reference)
  * https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/foreach-in

* List<T>.ForEach(Action<T>) Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.foreach?view=net-5.0

* runtime/src/libraries/System.Private.CoreLib/src/System/Collections/Generic/List.cs /
  * https://github.com/dotnet/runtime/blob/v5.0.3/src/libraries/System.Private.CoreLib/src/System/Collections/Generic/List.cs