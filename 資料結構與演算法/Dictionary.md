# Dictionary

## 特性

請參考 hash-table.md

## 範例方法

* Dictionary<TKey,TValue>.Add(TKey, TValue)
  * 一旦 Count = capacity，會自動複製現有內容至更大記憶區塊，runtime 為 O(n)，n 為 Count
  * 當 Count < capacity 時，runtime 為 O(1)

* Dictionary<TKey,TValue>.Remove
  * runtime 為 O(1)

* Dictionary<TKey,TValue>.ContainsKey(TKey)
  * runtime 為 O(1)

* Dictionary<TKey,TValue>.ContainsValue(TValue)
  * 線性搜尋，runtime 為 O(n)，n 為 Count

* Dictionary<TKey,TValue>.Clear
  * 線性搜尋，runtime 為 O(n)，n 為 **capacity**

## 一些好玩的事情

1. Dictionary<TKey,TValue>.Clear 方法的內部有兩個 Array.Clear

```csharp
public void Clear()
{
    int count = _count;
    if (count > 0)
    {
        Debug.Assert(_buckets != null, "_buckets should be non-null");
        Debug.Assert(_entries != null, "_entries should be non-null");

        Array.Clear(_buckets, 0, _buckets.Length);

        _count = 0;
        _freeList = -1;
        _freeCount = 0;
        Array.Clear(_entries, 0, count);
    }
}
```

2. Array.Clear(Array, Int32StartIndex, Int32Length) runtime 為 O(n)，n 為 length

3. Dictionary 內部方法 Initialize，使用建構方法之一的參數 capacity 去找最小 大於capacity 的質數

```csharp
private int Initialize(int capacity)
{
    int size = HashHelpers.GetPrime(capacity);
    int[] buckets = new int[size];
    Entry[] entries = new Entry[size];

    // Assign member variables after both arrays allocated to guard against corruption from OOM if second fails
    _freeList = -1;
#if TARGET_64BIT
    _fastModMultiplier = HashHelpers.GetFastModMultiplier((uint)size);
#endif
    _buckets = buckets;
    _entries = entries;

    return size;
}
```

來自 HashHelpers 的質數好朋友：

```csharp
private static readonly int[] s_primes =
{
    3, 7, 11, 17, 23, 29, 37, 47, 59, 71, 89, 107, 131, 163, 197, 239, 293, 353, 431, 521, 631, 761, 919,
    1103, 1327, 1597, 1931, 2333, 2801, 3371, 4049, 4861, 5839, 7013, 8419, 10103, 12143, 14591,
    17519, 21023, 25229, 30293, 36353, 43627, 52361, 62851, 75431, 90523, 108631, 130363, 156437,
    187751, 225307, 270371, 324449, 389357, 467237, 560689, 672827, 807403, 968897, 1162687, 1395263,
    1674319, 2009191, 2411033, 2893249, 3471899, 4166287, 4999559, 5999471, 7199369
};
```

## 等等，我要怎麼知道 capacity

我不知道啊啊啊啊啊 XD

## 參考資料

* runtime/src/libraries/System.Private.CoreLib/src/System/Collections/Generic/Dictionary.cs
  * https://github.com/dotnet/runtime/blob/v5.0.3/src/libraries/System.Private.CoreLib/src/System/Collections/Generic/Dictionary.cs

* Dictionary<TKey,TValue>.Add(TKey, TValue) Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2.add?view=net-5.0

* Dictionary<TKey,TValue>.Remove Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2.remove?view=net-5.0

* Dictionary<TKey,TValue>.ContainsKey(TKey) Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2.containskey?view=net-5.0

* Dictionary<TKey,TValue>.ContainsValue(TValue) Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2.containsvalue?view=net-5.0

* Dictionary<TKey,TValue>.Clear Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2.clear?view=net-5.0

* Array.Clear(Array, Int32, Int32) Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.array.clear?view=net-5.0

* HashHelpers.GetPrime 
  * https://github.com/dotnet/runtime/blob/v5.0.3/src/libraries/System.Private.CoreLib/src/System/Collections/HashHelpers.cs?fbclid=IwAR3fZ0ZW_o1THM4Uz22K8_2Sxc0GiVGE7cOs839wQYgL5YKFiBibNdBpYeI#L55