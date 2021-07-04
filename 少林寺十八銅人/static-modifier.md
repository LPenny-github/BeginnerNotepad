# static modifier（修飾詞）


## Why: 


1. 避免被加料

   > The advantage of using a static class is that the compiler can check to make sure that no instance members are accidentally added. The compiler will guarantee that instances of this class cannot be created.


1. （以物件導向的角度）當函式只跟自己有關聯時，加上 `static` 讓它屬於它自己。例如 Math:

   ```cs
   public static class Math
   ```


1. （以物件導向的角度）當函式相較於物件，與類別有更多互動時。反例：

   * Substring 屬於 String 物件的方法。

     ```cs
     public string Substring (int startIndex);
     ```

      * 當我們按照 String 這個藍圖創造出 String 物件後，可以用 Substring 這個方法擷取這個 String 物件中某幾個字元，製作出新的 String 物件。
      * 反觀，在 String 這個類別（藍圖）有 Substring 方法是不合理的，就像是 問車子設計圖有沒有加裝雪鏈。 


### 等等，為什麼 IsNullOrEmpty 屬於 String 類別的方法？

  ```cs
  public static bool IsNullOrEmpty (string? value);
  ```

  基於歷史包袱。以前程式語言設計，要一個 null 物件去查看自己是否為 null 會炸裂，就像，在程式語言中，任何自然數除以 0 會炸裂一樣。

  由於程式語言的演化，現在 C# 可以用 extension method 的模式，讓 null 物件去做事而可能不至於炸裂。


## How

* 特性：

  > The following list provides the main features of a static class:
  >
  > * Contains only static members.
  >
  > * Cannot be instantiated.
  >
  > * Is sealed.
  >
  > * Cannot contain Instance Constructors.

* 注意：

  1. 第一次叫用靜態 成員/建構函式 時，（可考慮）先初始化。 <-- 你不做，編輯器最後也會幫你做

  1. 靜態類別在叫用後，會保留在記憶體。


## 參考資料

* Static Classes and Static Class Members (C# Programming Guide)
  * https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members

* static (C# Reference)
  * https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/static

* Math Class
  * https://docs.microsoft.com/en-us/dotnet/api/system.math?view=net-5.0

* String.Substring Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.string.substring?view=net-5.0

* Extension Methods (C# Programming Guide)
  * https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/extension-methods