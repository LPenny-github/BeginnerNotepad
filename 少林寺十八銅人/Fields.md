# Fields / 欄位

> variables inside a class are called fields, and that you can access them by creating an object of the class, and by using the dot syntax (`.`). 

但，也可以用以下的做法賦值例如：

```csharp
using System;

namespace BlackBox
{
    class Program
    {
        public class FieldHouseholdChoreInformation
        {
            public string HouseholdChoreName;
            public int IdealFrequency;
        }

        static void Main(string[] args)
        {
            string name = "倒垃圾";
            int frequency = 7;

            FieldHouseholdChoreInformation fhouseholdChoreData = new FieldHouseholdChoreInformation
            {
                HouseholdChoreName = name,
                IdealFrequency = frequency
            };
            Console.WriteLine(fhouseholdChoreData.HouseholdChoreName);
            Console.WriteLine(fhouseholdChoreData.IdealFrequency);

            // Output:
            //
            // 倒垃圾
            // 7
        }
    }
}
```

* public 的 field 變數，是任何人 new 出新實體時都可以給予 field 變數 值
  * > 一般而言，您應該只針對具有 private 或 protected 存取範圍的變數使用欄位。 您的型別公開給用戶端程式代碼的資料應該透過 方法、 屬性和 索引子提供。 藉由使用這些建構來間接存取內部欄位，即可防範無效的輸入值。


## 參考資料

* C# Class Members
  * https://www.w3schools.com/cs/cs_class_members.php

* Fields (C# Programming Guide)
  * https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/fields