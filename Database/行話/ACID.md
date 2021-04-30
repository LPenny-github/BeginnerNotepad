# ACID

* DBMS 的四個特性，簡稱 ACID
  * 1. Atomicity / 原子性 / 基元性 / 不可分割性
    * 執行一個事務（transaction） 全部完成 或 全部沒完成，不會停在中間環節 或 僅處理某一部分。

  * 2. Consistency / 一致性
    * 執行一個事務（transaction）後，資料庫性沒有被破壞。也就是說：
      * > 資料都必須永遠符合 schema 的規範，保持資料與資料庫的一致性

  * 3. Isolation / 獨立性 / 隔離性
    * 確保多個事務（transaction）併行、進行讀寫修改。例如：
      * > 資料庫允許多筆交易同時進行，交易進行時未完成的交易資料並不會被其他交易使用，直到此筆交易完成。

  * 4. Durability / 持久性 / 持續性
    * 事務（transaction）處理後，對數據修改就是永久的，數據不會因系統故障、重啟而丟失。


## 參考資料

* ACID
  * https://zh.wikipedia.org/wiki/ACID

* 資料庫
  * https://zh.wikipedia.org/wiki/数据库

* MySQL 基本運作介紹，從資料庫交易與 ACID 特性開始
  * https://tw.alphacamp.co/blog/mysql-intro-acid-in-databases

* SQL 大小事
  * https://totoroliu.medium.com/資料庫-acid-bb87324035a8