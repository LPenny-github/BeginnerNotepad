# Dictionary to .csv

```csharp
string houseworkDetailText = String.Join(
    Environment.NewLine, houseworkDetail.Select(
        d => $"{d.serialNumber},{d.frequency},{d.lastDate:yyyy-MM-dd},{d.nextDate:yyyy-MM-dd}")); 
        
        // `d.lastDate:yyyy-MM-dd` 在.csv 上跑版，正在查資料......

string houseworkDetailPath = @"C:\myHome\housework-manager\housework-detail.csv";
System.IO.File.WriteAllText(houseworkDetailPath, houseworkDetailText);
```

## 參考資料

* “how to save a dictionary as a csv file in c#” Code Answer
  * https://www.codegrepper.com/code-examples/csharp/how+to+save+a+dictionary+as+a+csv+file+in+c%23