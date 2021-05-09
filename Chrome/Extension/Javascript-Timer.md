# Javascript Timer

目標：改良 Unable-Javascript （在晚上八點與凌晨四點之間，關閉 javascript），讓使用者可以不必手動反覆載入。


## 基本結構

資料夾 `javascript-timer` 有兩個檔案： `manifest.json` 和 `javascriptDecision.js` 。
 

## `manifest.json`

藉由定時器，自動執行查驗當地時間的任務。所以給予 `alarms` 這個權限。

```json
{
    "name": "Javascript Timer",
    "description": "Check Every Minute!",
    "version": "1.0",
    "manifest_version": 3,
    "background": {
      "service_worker": "javascriptDecision.js"
    },
    "permissions": [
        "alarms",
        "contentSettings"
      ]
  }
```

## `javascriptDecision.js`

基本上是由網路查到的範例做更改，內容很簡單。

```javascript
var alarmInfo = {
    delayInMinutes: 1, // 載入程式一分鐘後執行（Chrome Extension 不允許小於一分鐘）
    periodInMinutes: 1 // 執行後，於一分鐘後再度執行
};

chrome.alarms.clearAll();

chrome.alarms.onAlarm.addListener(function (alarm) { // 註冊事件。當鬧鐘響起時執行

    if (alarm.name === 'testAlarm') {

        let nowTime = new Date().getHours(); // 判斷方式跟之前完全一樣

        if (nowTime > 20 || nowTime < 4) {
            chrome.contentSettings.javascript.set({
                primaryPattern: '*://*/*',
                setting: 'block'
            });
        } else {
            chrome.contentSettings.javascript.set({
                primaryPattern: '*://*/*',
                setting: 'allow'
            });
        }
    }
});

chrome.alarms.create('testAlarm', alarmInfo);
```

## 參考資料

* Chrome Extension 開發與實作 17-chrome.alarms 定時器API
  * https://ithelp.ithome.com.tw/articles/10188167