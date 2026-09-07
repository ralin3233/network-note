# MAC 子層 Medium Access Control

## 為什麼需要 MAC 子層

當多台裝置共用同一個傳輸媒介（例如同一條乙太網路線、同一個無線頻道）時，必須要有規則決定「誰現在可以傳送資料」，否則訊號會互相干擾（碰撞）。

## CSMA/CD (Carrier Sense Multiple Access with Collision Detection)

用在有線乙太網路（傳統匯流排架構）。

1. 傳送前先「聽」媒介是否有其他裝置在傳（Carrier Sense）
2. 如果沒有，就開始傳送，同時持續監聽是否發生碰撞
3. 如果偵測到碰撞，雙方都停止傳送，各自等待一段隨機時間後重試（避免同時再次碰撞）

<!-- TODO: 補充 exponential backoff 的概念與公式 -->

## CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance)

用在無線網路（因為無線環境下碰撞不容易「偵測」，只能盡量「避免」）。

<!-- TODO: 補充為什麼無線環境偵測碰撞比較困難、RTS/CTS 機制 -->

## 兩者比較

| | CSMA/CD | CSMA/CA |
|---|---|---|
| 應用場景 | 有線乙太網路 | 無線網路 (Wi-Fi) |
| 核心策略 | 偵測碰撞後重傳 | 事先避免碰撞發生 |
