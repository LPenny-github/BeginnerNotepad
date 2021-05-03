# Binary tree（二元樹）

* 二元樹 是 樹 的一種。一個 father node 最多可連接兩個 child node。

* 二元樹的小分類：
  * 1. full tree：每個 father node 都連接兩個 child node，也就是掛滿滿的意思。
  * 2. complete tree：不是上面那種，也就是沒掛滿。

## 注意：perfect binary Tree 與 full binary tree 分類上的無限之戰

如果遇到 perfect binary Tree，記得把 `每個 father node 都連接兩個 child node，也就是掛滿滿的意思` 給它。

## 計算 節點（node）總數 和 樹高

1. full tree
   * 節點總數：k = 2<sup>h</sup> -1
   * 樹高：h = log<sub>2</sub> (k+1)

2. complete tree
   * 節點總數：2<sup>h-1</sup> <= k <= 2<sup>h</sup> -1
   * 樹高：	h = log<sub>2</sub> k+1

## 製作二元樹

兩個分法：

1. 用一個 Array 裝，child node 的 index 用計算得出
   * 左邊 child node 的 index：2 * `father node index` + 1
   * 右邊 child node 的 index：2 * `father node index` + 2

2. 使用自訂結構 class

## List<T>.BinarySearch Method

* BinarySearch(T)：在 List 中找出元素 T 的 index
  * List 必須已排序（sorted）
  * runtime 為 O(logN)，N 是節點總數
  * 如果找不到該元素，則傳回負值
  * 如果該元素有多個，則隨機傳回其中一個的 index

## 等等， runtime 是 O(logN)？ log 底數一下子是 2、一下子是 10？

精確來說，runtime 是 O(log<sub>2</sub> N)。

所以有可能是……

1. 一種習慣
   * 大家心裡都知道 O(logN) 是 簡寫/化 O(log<sub>2</sub> N)，因為懶。

2. 這種懶並不會影響大多數的判斷
   * 無論是 O(logN) 或 O(log<sub>2</sub> N) 都比 O(N) 和 O(N<sup>2</sub>) 明顯來得小。

## 參考資料

* 樹 (資料結構)
  * > 在計算機科學中，樹（英語：tree）是一種抽象資料類型（ADT）或是實作這種抽象資料類型的資料結構，用來類比具有樹狀結構性質的資料集合。它是由n（n>0）個有限節點組成一個具有層次關係的集合。把它叫做「樹」是因為它看起來像一棵倒掛的樹，也就是說它是根朝上，而葉朝下的。
  * https://zh.wikipedia.org/zh-tw/树_%28数据结构%29

* 二元樹
  * https://zh.wikipedia.org/wiki/二叉树

* 樹狀結構(Python)
  * https://sites.google.com/site/zsgititit/home/python-cheng-shi-she-ji/shu-zhuang-jie-gou-python

* List<T>.BinarySearch Method
  * https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.binarysearch?view=net-5.0
