# Assert.AreEqual() VS. Assert.AreSame()


* 除了 String 外，不同點：
  * Assert.AreEqual() ： 驗證兩者的型別與值
  * Assert.AreSame()  ： 驗證兩者是否為同一物件（object）
    * 若是同一物件，則記憶體儲存位置相同


```csharp
[TestFixture]
public class LearnHowToTest
{
     [Test]
    public void BothParseString1_AreEqual_True() // 兩者值與型別相同
    {
        Assert.AreEqual(int.Parse("1"), int.Parse("1"));
    }
     [Test]
    public void BothParseString1_AreNotSame_True() // 兩者記憶體位置不同
    {
        Assert.AreNotSame(int.Parse("1"), int.Parse("1"));
    }
     [Test]
    public void CompareInt_AreNotSame_True() // 兩者記憶體位置不同
    {
        int i = 5;
        Assert.AreNotSame(i, 5);
    }
     [Test]
    public void CompareString_AreSame_True()
    {
        string o = "O";
        string oo = "O";
        Assert.AreSame(o, oo);
    }
     [Test]
    public void CompareString_AreEqual_True()
    {
        string o = "O";
        string oo = "O";
        Assert.AreEqual(o, oo);
    }
}

// Output:
//
// Total tests: 5. Passed: 5. Failed: 0. Skipped: 0
```


## 參考資料

* Diff between Assert.AreEqual and Assert.AreSame?（必看）
  * https://stackoverflow.com/questions/24172782/diff-between-assert-areequal-and-assert-aresame/24172799

* Assert Class
  * https://docs.microsoft.com/en-us/dotnet/api/nunit.framework.assert?view=xamarin-ios-sdk-12

* Assert.AreEqual Method
  * https://docs.microsoft.com/en-us/dotnet/api/nunit.framework.assert.areequal?view=xamarin-ios-sdk-12#NUnit_Framework_Assert_AreEqual_System_Int32_System_Int32_

* Assert.AreSame Method
  * https://docs.microsoft.com/en-us/dotnet/api/nunit.framework.assert.aresame?view=xamarin-ios-sdk-12#NUnit_Framework_Assert_AreSame_System_Object_System_Object_