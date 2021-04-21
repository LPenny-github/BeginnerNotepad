# Method chaining

* 物件導向的程式語言中，在同一行（statement）中使用多個方法（method）。
* 每個方法執行後丟出 結果/物件（object），不需要建造新變數儲存，便能隨即被鍊在後面的方法使用。

## 範例

像是一個方法接連著用：

```csharp  
String s = "aaa";
Console.WriteLine("The initial string: '{0}'", s);
s = s.Replace("a", "b").Replace("b", "c").Replace("c", "d");
Console.WriteLine("The final string: '{0}'", s);

// The example displays the following output:
//       The initial string: 'aaa'
//       The final string: 'ddd'
```

或是 LINQ 寫法：

```csharp
int[] newArray = new int[]{1,2,3,4,5,6};
int output = newArray.Where(a => a > 4).Count();
Console.WriteLine(output);

// output: 2
```

## 資料來源

* Method chaining
  https://en.wikipedia.org/wiki/Method_chaining