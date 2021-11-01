# field 變數序列化成 json 失敗

## 情境

我做了一個 field 架構，也有賦予值，用 Console.WriteLine() 也印得出（值）來，但轉換成 json格式後卻啥都沒有。

例如：

```csharp
using System.IO;
using System.Text.Encodings.Web;
using System.Text.Json;
using System.Text.Unicode;

namespace BlackBox
{
    class Program
    {
        public class FieldHouseholdChoreInformation
        {
            public string HouseholdChoreName; 
            public int IdealFrequency;
        }
        public class PropertyHouseholdChoreInformation
        {
            public string HouseholdChoreName { get; set; }
            public int IdealFrequency { get; set; }
        }

        static void Main(string[] args)
        {
            string name = "倒垃圾";
            int frequency = 7;

            // ---
            // Property 變數架構操作

            PropertyHouseholdChoreInformation phouseholdChoreData = new PropertyHouseholdChoreInformation
            {
                HouseholdChoreName = name,
                IdealFrequency = frequency
            };

            var options = new JsonSerializerOptions
            {
                WriteIndented = true,
                Encoder = JavaScriptEncoder.Create(UnicodeRanges.All)
            };
            string pSerializedString = JsonSerializer.Serialize<PropertyHouseholdChoreInformation>(phouseholdChoreData, options);
            
            const string fileName = "HouseholdChoreInformation.json";

            File.AppendAllText(fileName, pSerializedString.ToString());

            // ---
            // Field 變數的操作

            FieldHouseholdChoreInformation fhouseholdChoreData = new FieldHouseholdChoreInformation
            {
                HouseholdChoreName = name,
                IdealFrequency = frequency
            };
            
            string fSerializedString = JsonSerializer.Serialize<FieldHouseholdChoreInformation>(fhouseholdChoreData, options);
            File.AppendAllText(fileName, fSerializedString.ToString());
        }
    }
}

// HouseholdChoreInformation.json 內容:
//
// {
//   "HouseholdChoreName": "倒垃圾",
//   "IdealFrequency": 7
// }{}

```

## 解法

### 一：更改全域設定。

* 在 JsonSerializerOptions 裡，將 IncludeFields 改為 true （預設為 false）。

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
    Encoder = JavaScriptEncoder.Create(UnicodeRanges.All),
    IncludeFields = true // 就是這個光
};
```

### 二：為欄位設定屬性。

```csharp
using System.Text.Json.Serialization;

public class FieldHouseholdChoreInformation
{
    [JsonInclude]
    public string HouseholdChoreName; 
    [JsonInclude]
    public int IdealFrequency;
}
```


## 參考資料

* JsonSerializerOptions.IncludeFields Property
  * https://docs.microsoft.com/en-us/dotnet/api/system.text.json.jsonserializeroptions.includefields?view=net-5.0

* 如何在 .NET 中序列化和還原序列化 (封送處理和 unmarshal) JSON
  * https://docs.microsoft.com/zh-tw/dotnet/standard/serialization/system-text-json-how-to?pivots=dotnet-5-0