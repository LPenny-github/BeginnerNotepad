# this modifier in extension methods

> The this keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.


## Why

1. 方便。
   > Extension methods enable you to "add" methods to existing types without creating a new derived type, recompiling, or otherwise modifying the original type. Extension methods are static methods, but they're called as if they were instance methods on the extended type. For client code written in C#, F# and Visual Basic, there's no apparent difference between calling an extension method and the methods defined in a type.

1. 貼近（物件導向的）直觀思考。

## How

* 使用方式：

  > Their first parameter specifies which type the method operates on. 

  * 把 `this` 加在方法的第一個參數。第一個參數也代表被擴充的對象。例如：

    ```cs
    static void Main(string[] args)
    {
      int[] numbers = new []{1,2,3};
      numbers.Swap(0,2);
      foreach (var item in numbers)
      {
        Console.Write(item + " ");
      }
            
      // Output: 3 2 1 
    }
  
    static void Swap(this int[] input, int index1, int index2)
    {
      input[index1], input[index2]) = (input[index2], input[index1]);
    }
    ```

* 注意：

  1. Extension methods 屬於靜態方法，須標示 `static` 。

## 參考資料

* this (C# Reference)
  * https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/this

* Extension Methods (C# Programming Guide)
  * https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/extension-methods