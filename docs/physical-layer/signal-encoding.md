# 訊號與編碼

## 類比訊號 vs 數位訊號

<!-- TODO: 連續 vs 離散、各自的優缺點 -->

## 為什麼需要編碼

如果單純用「高電壓 = 1，低電壓 = 0」，會遇到同步問題（連續一串 1 或 0 時，接收端不容易知道現在是第幾個位元）。編碼方式就是為了解決這類問題設計的。

## 常見編碼方式

### NRZ (Non-Return-to-Zero)
<!-- TODO: 原理、缺點（長串相同位元時同步困難） -->

### Manchester Encoding
<!-- TODO: 原理（每個位元中間都有轉態）、優點（自帶時脈訊號）、實際用在哪（早期乙太網路） -->

### Differential Manchester
<!-- TODO: 跟 Manchester 的差異 -->

!!! example "圖解建議"
    這裡強烈建議畫出每種編碼方式對同一組位元序列（例如 `1 0 1 1 0 0 1`）的波形圖，用看的比用讀的清楚很多

## 編碼方式比較

| 編碼 | 自帶時脈 | 頻寬效率 | 常見應用 |
|---|---|---|---|
| NRZ | 否 | 高 | - |
| Manchester | 是 | 低（頻寬需求加倍）| Classic Ethernet |
| Differential Manchester | 是 | 低 | Token Ring |
