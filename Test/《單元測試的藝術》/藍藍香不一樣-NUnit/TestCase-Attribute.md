# [TestCase] Attribute Description


* 可以在同一個測試方法中，投遞一個至多個測試參數。


```csharp
using NUnit.Framework;

namespace UnitTests;

[TestFixture]
public class LogAnalyzerTests
{
    // 寫法一
    [TestCase("FileWithBadExtension.pdf")]
    public void IsValidLogFileName_BadExtension_ReturnFalse(string filename)
    {
        LogAnalyzer analyzer = new();
        bool result = analyzer.IsValidLogFileName(filename);
        Assert.False(result);
    }

    // 寫法二
    [TestCase("FileWithBadExtension.PDF", false)]
    public void IsValidLogFileName_BadExtension_ReturnTrue(string filename, bool expectedResult)
    {
        LogAnalyzer analyzer = new();
        Assert.AreEqual(expectedResult, analyzer.IsValidLogFileName(filename));
    }

    // 寫法三
    [TestCase("FileWithGoodExtension.SLF", ExpectedResult = true)]
    [TestCase("FileWithGoodExtension.slf", ExpectedResult = true)]
    public bool IsValidLogFileName_GoodExtension_ReturnTrue(string filename)
    {
        LogAnalyzer analyzer = new();
        bool result = analyzer.IsValidLogFileName(filename);
        return result;
    }
}

// Output:
//
// Total tests: 4. Passed: 4. Failed: 0. Skipped: 0
```

## 參考資料

* TestCase
  * https://docs.nunit.org/articles/nunit/writing-tests/attributes/testcase.html