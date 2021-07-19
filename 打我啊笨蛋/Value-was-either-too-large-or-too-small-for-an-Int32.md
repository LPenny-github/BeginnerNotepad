# System.OverflowException: Value was either too large or too small for an Int32.


## 情境

編譯錯誤：

```cs
// 把一個日期以 yyyyMMdd 轉成十進位，再轉成二進位，再反轉，再轉回十進位。
// 如果還是相同的十進位，就回傳 true，否則回傳 false

public bool IsValidDay(DateTime day)
{
    var formatedDay = day.ToString("yyyyMMdd");
    int dayToInt;
    bool result = Int32.TryParse(formatedDay, out dayToInt);
    if (!result)
    {
        return false;
    }
    var dayToBinary = Convert.ToString(dayToInt, 2);
    var reversedDay = dayToBinary.Reverse().ToArray();
    var reversedDayToString = new string(reversedDay);
    var reversedDayToInt = Convert.ToInt32(reversedDayToString); // System.OverflowException
    if (reversedDayToInt != dayToInt)
    {
        return false;
    }
    return true;
}
```


## 解釋

因為 `Convert.ToInt32()` 如果不丟第二個參數（int fromBase），那麼程式就會以十進位的方式轉換成 `int` 。

日期格式 `yyyyMMdd` 轉成二進位共有 25 位阿拉伯數字，所以就炸掉了。

```cs
Console.WriteLine(Convert.ToInt32("100"));
Console.WriteLine(Int32.MaxValue);
Console.WriteLine(Int32.MinValue);
Console.WriteLine(Convert.ToInt32("100", 2));
            
// Output:
// 100
// 2147483647
// -2147483648
// 4
```


## 參考資料

* Convert.ToInt32 Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.convert.toint32?view=net-5.0#System_Convert_ToInt32_System_String_System_Int32_