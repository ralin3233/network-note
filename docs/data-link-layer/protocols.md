# 常見協定

## Ethernet Frame 格式

<!-- TODO: 畫出 Ethernet frame 的欄位圖：Preamble | Destination MAC | Source MAC | Type | Data | CRC -->

| 欄位 | 長度 | 用途 |
|---|---|---|
| Preamble | 7 bytes | 讓接收端同步時脈 |
| Destination MAC | 6 bytes | 目的裝置位址 |
| Source MAC | 6 bytes | 來源裝置位址 |
| Type/Length | 2 bytes | 上層協定類型 |
| Data | 46-1500 bytes | 實際資料 |
| CRC | 4 bytes | 錯誤偵測碼 |

## MAC 位址

- 48 位元（6 bytes），通常寫成 12 位十六進位數字，如 `00:1A:2B:3C:4D:5E`
- 前 3 bytes 是廠商代碼 (OUI)，後 3 bytes 由廠商自行分配
- 理論上全球唯一，燒錄在網路卡上

<!-- TODO: 補充課堂提到的其他協定，例如 PPP、HDLC -->
