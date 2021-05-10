# Unable Javascript

目標：在晚上八點與凌晨四點之間，關閉 javascript。


## 基本結構

資料夾 `unable-javascript` 裡面有兩個檔案： `manifest.json` 和 `javascriptDecision.js`


## `manifest.json`

因為這次要變動 javascript 設定，所以需要給予 Extension 權限（加入 `permissions`）。

至於給予權限的內容寫法，可以在 Chrome API 文件上查的到，請見參考資料的第一筆。

```json
{
    "name": "Unable Javascript",
    "description": "Unable Javascript At Night!",
    "version": "1.1",
    "manifest_version": 3,
    "background": {
      "service_worker": "javascriptDecision.js"
    },
    "permissions": [
        "contentSettings"
      ]
  }
```

## `javascriptDecision.js`

自己在推斷 `chrome.contentSettings.javascript.set()` 這個句法，花了超級久的時間（因為不會 javascript，也看不懂 javascript 文件，滿頭霧水花了不少時間 XD）

後來是直接找網路上的例子來理解。

```javascript
let nowTime = new Date().getHours();

if (nowTime > 20 || nowTime < 4) {
    chrome.contentSettings.javascript.set({
        primaryPattern: '*://*/*', // 意指所有網址
        setting: 'block'
    });
} else {
    chrome.contentSettings.javascript.set({
        primaryPattern: '*://*/*',
        setting: 'allow'
    });
}
```

## 缺陷

每次都得重新載入才能執行此 Extension（的判斷功能），所以之後我又做了一個改良版 XD

## 參考資料

* Documentation > Extensions > API Reference > chrome.contentSettings
  * https://developer.chrome.com/docs/extensions/reference/contentSettings/

* How to replace code from my chrome-extension?
  * https://stackoverflow.com/questions/55766755/how-to-replace-code-from-my-chrome-extension