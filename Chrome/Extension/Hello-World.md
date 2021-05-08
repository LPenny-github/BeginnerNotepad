# Hello World 專案

目標：當 Chrome 一載入 `Hello-World` 這個 Extension 時，會開啟一個新分頁。新分頁的標題是 `Hello, World!`，內容為 `Hello, World!`。

## 基本結構

* `Hello-World` 這個資料夾裡有三個檔案： `manifest.json` 、 `background.js` 和 `hello.html`
  * 你也可以從官方例子開始，但那不是 Hello World
    * https://developer.chrome.com/docs/extensions/mv3/getstarted/

## `manifest.json`

`background` 指的是背景程式會執行的動作。

```json
{
  "name": "Hello, World!",
  "version": "1.0",
  "manifest_version": 3,
  "background": {
    "service_worker": "background.js"
  }
}
```

## `background.js`

原始檔案裡的解說就已經非常清楚。

```javascript
// Extension event listeners are a little different from the patterns you may have seen in DOM or
// Node.js APIs. The below event listener registration can be broken in to 4 distinct parts:
//
// * chrome      - the global namespace for Chrome's extension APIs
// * runtime     – the namespace of the specific API we want to use
// * onInstalled - the event we want to subscribe to
// * addListener - what we want to do with this event
//
// See https://developer.chrome.com/docs/extensions/reference/events/ for additional details.
chrome.runtime.onInstalled.addListener(async () => {

  // While we could have used `let url = "hello.html"`, using runtime.getURL is a bit more robust as
  // it returns a full URL rather than just a path that Chrome needs to be resolved contextually at
  // runtime.
  let url = chrome.runtime.getURL("hello.html");

  // Open a new tab pointing at our page's URL using JavaScript's object initializer shorthand.
  // https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer#new_notations_in_ecmascript_2015
  //
  // Many of the extension platform's APIs are asynchronous and can either take a callback argument
  // or return a promise. Since we're inside an async function, we can await the resolution of the
  // promise returned by the tabs.create call. See the following link for more info on async/await.
  // https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Async_await
  let tab = await chrome.tabs.create({ url });

  // Finally, let's log the ID of the newly created tab using a template literal.
  // https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals
  //
  // To view this log message, open chrome://extensions, find "Hello, World!", and click the
  // "service worker" link in th card to open DevTools.
  console.log(`Created tab ${tab.id}`);
});
```

## `hello.html`

內容很單純，沒有需要特別說明的部分。

```html
<!DOCTYPE html>
<html>
<head>
  <title>Hello, World!</title>
</head>
<body>
  <p>Hello, World!</p>
</body>
</html>
```

## 資料來源

* GoogleChrome/chrome-extensions-samples
  * https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/examples/hello-world