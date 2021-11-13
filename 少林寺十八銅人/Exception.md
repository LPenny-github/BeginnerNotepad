# Exception / 例外狀況 / 在 .NET 中處理和擲回例外狀況


## What

> An exception is any error condition or unexpected behavior that is encountered by an executing program. Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that can't be verified), and so on. 

> 例外狀況是執行程式所遇到的錯誤狀況或未預期的行為。 在發生程式碼或您呼叫的程式碼 (例如共用程式庫) 中有錯誤、無法使用作業系統資源、執行階段遇到非預期的狀況 (例如無法驗證的程式碼) 等情況時，就可能會擲回例外狀況。


## Why

> 傳統上，一種語言的錯誤處理模型不是依賴語言唯一偵測錯誤的方式與尋找處理常式，就是依賴作業系統所提供的錯誤處理機制。 .NET 實作例外狀況處理的方式具有下列優點：
>
> * .NET 程式語言擲回和處理例外狀況的方式都相同。
>
> * 不需要任何特定語言語法以處理例外狀況，但可讓每一種語言定義屬於自己的語法。
>
> * 例外狀況可跨處理序，甚至是跨電腦界限擲回。
>
> * 可將例外狀況處理程式碼加入應用程式，以增加程式可靠性。
 

## Why not

頻繁地擲回例外狀況會影響程式效能，對於可預期的錯誤不妨改以擲回 Null 。


## Which

請見： 在 .NET 中處理和擲回例外狀況 > 常見例外狀況

https://docs.microsoft.com/zh-tw/dotnet/standard/exceptions/#common-exceptions


## How

待消化的資源：

* What Every Dev needs to Know About Exceptions in the Runtime
  * https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/botr/exceptions.md

* 例外狀況的最佳做法
  * https://docs.microsoft.com/zh-tw/dotnet/standard/exceptions/best-practices-for-exceptions

* 如何使用當地語系化的例外狀況訊息來建立使用者定義的例外狀況
  * https://docs.microsoft.com/zh-tw/dotnet/standard/exceptions/how-to-create-localized-exception-messages


## 參考資料

* Exception 類別和屬性
  * https://docs.microsoft.com/zh-tw/dotnet/standard/exceptions/exception-class-and-properties

* 在 .NET 中處理和擲回例外狀況
  * https://docs.microsoft.com/zh-tw/dotnet/standard/exceptions/
