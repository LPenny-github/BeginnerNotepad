# [TestFixture] Attribute Description


> This is the attribute that marks a class that contains tests and, optionally, setup or teardown methods.


*  `[TestFixture]` 為 NUnit 測試 class 的標記，可以做到（目前我還用不到，先列出官方文件上的分類）：
  * Inheritance
  * Parameterized Test Fixtures
  * Generic Test Fixtures
  * Generic Test Fixtures with Parameters


## 為什麼不加上 [TestFixture] 標記，測試仍然可以運作？

> Beginning with NUnit 2.5, the TestFixture attribute is optional for non-parameterized, non-generic fixtures. So long as the class contains at least one method marked with the Test, TestCase or TestCaseSource attribute, it will be treated as a test fixture.


* 關於我自己安裝的 NUnit 版本：

  ```html
  <ItemGroup>
    <PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.11.0" />
    <PackageReference Include="NUnit" Version="3.13.2" />
    <PackageReference Include="NUnit3TestAdapter" Version="4.0.0" />
    <PackageReference Include="coverlet.collector" Version="3.1.0" />
  </ItemGroup>
  ```


## 參考資料

* TestFixture
  * https://docs.nunit.org/articles/nunit/writing-tests/attributes/testfixture.html