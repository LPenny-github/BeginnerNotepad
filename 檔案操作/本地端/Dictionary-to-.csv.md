# Dictionary to .csv

```csharp
string houseworkDetailText = String.Join(
    Environment.NewLine, houseworkDetail.Select(
        d => $"{d.serialNumber},{d.frequency},{d.lastDate:yyyy-MM-dd},{d.nextDate:yyyy-MM-dd}")); 
        
        // `d.lastDate:yyyy-MM-dd` 、 `d.nextDate:yyyy-MM-dd` 用 Excel 打開跑版，但用 Notepad 打開格式正確，原來是 Excel 貼心過頭 XD

string houseworkDetailPath = @"C:\myHome\housework-manager\housework-detail.csv";
System.IO.File.WriteAllText(houseworkDetailPath, houseworkDetailText);
```

## 參考資料

* “how to save a dictionary as a csv file in c#” Code Answer
  * https://www.codegrepper.com/code-examples/csharp/how+to+save+a+dictionary+as+a+csv+file+in+c%23