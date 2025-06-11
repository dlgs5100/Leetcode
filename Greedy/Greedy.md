# Greedy

核心概念: 貪婪演算法不進行回溯或考慮可能的後果，只關注當前的最佳結果，因此能找到局部最佳解。

## 適用情境
- 活動選擇問題（Activity Selection Problem）: 選最多場不重疊的活動，貪婪地選結束時間最早的活動。
- 最小生成樹（Minimum Spanning Tree）
- Kruskal’s Algorithm（選權重最小邊）
- Prim’s Algorithm（擴展最便宜的連接）
- 單源最短路徑（Dijkstra’s Algorithm）: 每次選離起點最近的點擴展。
- Huffman 編碼: 合併頻率最小的兩個節點以構建最優前綴碼樹。
- 分錢問題 / 換硬幣問題（有條件時才行）: 比如：用最少硬幣湊金額，如果硬幣面額是「貪婪友善的」，就能用 Greedy。
- 區間覆蓋問題 / 貪心切割問題: 常見在排程、資源分配等領域。