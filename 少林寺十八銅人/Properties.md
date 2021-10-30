# Properties / 屬性

> Before we start to explain properties, you should have a basic understanding of "Encapsulation"（封裝）.
>
> The meaning of Encapsulation, is to make sure that "sensitive" data is hidden from users. To achieve this, you must:
>
>  * declare fields/variables as private
>  * provide public get and set methods, through properties, to access and update the value of a private field


> 屬性有許多用途：它們可以先驗證資料，再允許變更；它們會以透明方式公開類別上的資料，而該資料實際是從某個其他來源 (例如資料庫) 所擷取；資料變更時 (例如，引發事件，或變更其他欄位的值)，它們可以採取動作。


## 範例

```csharp
using System;

namespace BlackBox
{
    class Program
    {
        public class PropertyHouseholdChoreInformation
        {
            public string HouseholdChoreName { get; set; } // Automatic Properties (Short Hand)
            private int idealFrequency; // Field
            public int IdealFrequency   // Property
            {
                get => idealFrequency;
                set 
                {
                    if (value < 1 || value > 60)
                    {
                        idealFrequency = 30;
                    }
                }
            }            
        }

        static void Main(string[] args)
        {
            string name = "倒垃圾";
            int frequency = 90;

            PropertyHouseholdChoreInformation phouseholdChoreData = new PropertyHouseholdChoreInformation
            {
                HouseholdChoreName = name,
                IdealFrequency = frequency
            };
            
            Console.WriteLine(phouseholdChoreData.HouseholdChoreName);
            Console.WriteLine(phouseholdChoreData.IdealFrequency);

            // Output:
            //
            // 倒垃圾
            // 30
        }
    }
}
```


## 參考資料

* C# Properties (Get and Set)
  * https://www.w3schools.com/cs/cs_properties.php

* 使用屬性 (C# 程式設計手冊)
  * https://docs.microsoft.com/zh-tw/dotnet/csharp/programming-guide/classes-and-structs/using-properties