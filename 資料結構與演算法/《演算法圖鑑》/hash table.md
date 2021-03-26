## hash table

### 特性

1. 彈性儲存資料、快速存取

2. 常用於關聯陣列（associate array）

3. 實作，如：Dictionary

### hash table 的誕生

1. 每個資料由 key 和 value 一對組成，key 不能為 null，也不能重複。

2. key 經過 雜湊函數（hash function） 生成 雜湊碼（hash code），並依據雜湊碼給定儲存位置。

3. 每個 input 經過 雜湊函數 運算後，生成 雜湊碼，接著用 雜湊碼 去取得 value。

### 稍微細節的部份

* 雜湊函數（hash function）
  * 諸如：MD5、SHA-1、SHA-2
  * MD5 和 SHA-1 目前並不安全

* 雜湊碼（hash code）
  * 雜湊碼 由 16進位 組成，但電腦儲存是 2進位
  * 無論 key/輸入 的值大或小，經過 雜湊函數 運算後的 雜湊碼，長度不變
  * 相同的 key/輸入，用相同的 雜湊函數運算，雜湊碼會相同
  * 相似的 key/輸入，用相同的 雜湊函數運算，雜湊碼會截然不同
  * 由於 雜湊碰撞（hash collision），即便 雜湊碼 和 雜湊函數 相同，也可能來自不同的 key/輸入
  * 針對密碼或安全性設計的雜湊函數，其 雜湊碼 很難推導出 key/輸入

* 雜湊碰撞（hash collision）
  * 出現機率很小，但仍然可能發生
  * 出現 雜湊碰撞 時常見的做法：
    * 鍊結法（chaining）：用 list 結構，把資料接在已存入的資料後面
    * 開放定址法（open addressing）：利用 多個雜湊函數 或 線性探測法（linear probing） 等方法，把資料放在候補位置

* hash table 容量的藝術
  * 儲存空間開太大，浪費
  * 儲存空間開太小，提高 雜湊碰撞 的機率

### 資料來源

* Dictionary<TKey,TValue> Class
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2?view=net-5.0