# Interface / 介面


> An interface defines a contract. Any class or struct that implements that contract must provide an implementation of the members defined in the interface.


## 為什麼需要介面

1. 介面就像是一種 模組/雛形/藍圖 ，提供實作事物的概廓。

   * 像是提到「褲子」，很容易就可以聯想到兩條長長的褲管，以及臀部、腹部的包覆。
     * 運動褲、牛仔褲、褲裙。

1. 使用介面與實作，在測試時可以更單純、更容易偵測錯誤。

1. 更好收斂，或是擴充功能。


## 特性

* 命名習慣以大寫 `I` 為首。

C# 8.0 以前，介面可宣告但沒有實作：

* Methods
* Properties
* Indexers
* Events

C# 8.0 以後，介面可以包含實作，以及：

* Constants
* Operators
* Static constructor
* Nested types
* Static fields, methods, properties, indexers, and events
* Member declarations using the explicit interface implementation syntax.
* Explicit access modifiers (the default access is public).


# 參考資料

* interface (C# Reference)
  * https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/interface

* 介面-定義多個類型的行為
  * https://docs.microsoft.com/zh-tw/dotnet/csharp/fundamentals/types/interfaces