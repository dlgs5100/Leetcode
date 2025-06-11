# Dynamic Programming

核心概念: 將一個複雜的問題切割成小的子問題，運算小的子問題後儲存解果避免重複運算，此概念稱為最優子結構。(白話文: 當前的結果和前面一步或兩步的結果有關)
- Optimal Substructure（最優子結構）問題的最優解可以由其子問題的最優解組合而成。
- Overlapping Subproblems（重疊子問題） 在求解過程中，會遇到很多重複的子問題。
- Memoization（記憶化）或 Tabulation（表格法）
    - Top-down（自上而下）: 使用遞迴 + 記憶化（Memoization）
        - Top-Down 是從整體的大問題開始往下切割成小問題，直到碰到最小的基本情況為止。
        - 例如: Leetcode 62. 從(0,0)走到(m-1,n-1)，往下切割，會得到(m-2,n-1)走到(m-1,n-1)，及(m-1,n-2)走到(m-1,n-1)的子問題，接著在跳出stack回去。
    - Bottom-up（自下而上）: 使用迴圈 + 表格儲存（Tabulation）
        - Bottom-Up 是從最小、最簡單的 base case 開始累積，往更大的子問題推進。
        - 例如: Leetcode 62. 從(0,0)走到(0,1)有幾種可能，一直推進到從(0,0)走到(m-1,n-1)有幾種可能。

## 適用情境
| 類型         | 題目關鍵詞/描述                                             |
|--------------|-------------------------------------------------------------|
| 子序列、子字串問題 | "longest", "common", "subsequence", "substring"            |
| 換錢問題     | "how many ways", "minimum number of coins"                 |
| 最短路徑     | "minimum cost", "shortest path"                            |
| 走格子問題   | "number of ways to reach", "robot path"                    |
| 背包問題     | "choose items with weight and value", "maximum value"      |
| 遊戲策略     | "pick from both ends", "who wins"                          |
| 可行性判斷   | "can you reach?", "is it possible?"                        |

問自己這三個問題：

1. 這層有多少種選擇要嘗試？
多種 ➜ 要 for 迴圈

2. 是否每次都只根據參數唯一遞推？
是 ➜ 不要迴圈

3. 這題本質像是在列出「所有可能組合」嗎？
是 ➜ 需要迴圈（通常在 backtracking 類題目）

| 型別 |	是否使用遞迴	|遞推方向	|dp[i] 意義| 問題拆解方向|
|------|-------------------|-----------|------------|---------|
|由未來推現在|	✅（遞迴）|	f(i) → f(i+1)|	從 i 開始（"從" 型）| 問題是「今天做什麼 → 接下來要怎麼辦？」|
|由過去推現在|	✅ or ❌|	f(i) ← f(i-1)	|到 i 為止（"到" 型）| 問題是「我做到今天為止怎樣？」|

|情況|	是否需要迴圈？|
|---|---|
|要對多種選擇嘗試|	✅ 要放迴圈|
|每次呼叫只有單一路徑|	❌ 不需要迴圈|
