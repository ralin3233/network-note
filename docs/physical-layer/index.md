# 實體層 Physical Layer 全景導覽

實體層（Physical Layer）是 OSI 七層模型的最底層（Layer 1）。它的核心任務只有一個：**將上層的邏輯資料（0 與 1 位元串），轉換為可在真實物理媒介（空氣電磁波、電纜）中傳遞的實體訊號（高頻載波電壓、電磁波），並在接收端還原。**

---

## 為什麼需要從「正弦波」開始學網路？

很多初學者在剛翻開網路通訊教科書時常感到困惑：

> *「我明明是來學電腦網路和軟體協定的，為什麼第一堂課老師在黑板上畫三角函數、正弦波、頻率和傅立葉轉換？」*

要理解網路通訊的底層邏輯，必須掌握課堂簡報中**環環相扣的四大推導脈絡**：

```mermaid
graph TD
    A["1. 正弦波 (Sine Wave)<br>物理界最純粹的連續訊號通式：A cos(2πft + θ)"] --> B["2. 方波的構成與傅立葉分析 (Fourier Analysis)<br>電腦的 0 與 1 方波由基頻與奇數次諧波疊加而成"]
    B --> C["3. 頻寬與傅立葉五大性質 (Bandwidth & Properties)<br>有效頻寬 (90%能量) ↔ 時移/縮放/相加/餘弦相乘性質"]
    C --> D["4. 數位調變、解調與適應性機制 (Modulation & AMC)<br>ASK/PSK/QAM 星座圖 ↔ I/Q 正交分解 ↔ 最近鄰判決與 AMC 策略"]
    
    style A fill:#e0f2fe,stroke:#0288d1,stroke-width:2px,color:#0f172a;
    style B fill:#dcfce7,stroke:#16a34a,stroke-width:2px,color:#0f172a;
    style C fill:#ffedd5,stroke:#ea580c,stroke-width:2px,color:#0f172a;
    style D fill:#fce7f3,stroke:#db2777,stroke-width:2px,color:#0f172a;
```

---

## 本章循序漸進閱讀指南

本章節完全依照課堂簡報之推導進程，由淺入深拆解實體層技術：

| 章節 | 核心課題 | 一句話總結 |
|---|---|---|
| [1. 正弦波特性與通式](sine-wave.md) | 什麼是正弦波？三個基本參數是什麼？ | 任何週期訊號的基礎「積木」，用振幅、頻率與相位數學精確描述波形。 |
| [2. 方波構成與傅立葉分析](fourier-and-square-wave.md) | 數位方波是怎麼生出來的？ | 透過傅立葉級數，方波其實是「基頻 + 奇數次諧波」的疊加。 |
| [3. 頻寬與傅立葉轉換性質](bandwidth-and-capacity.md) | 什麼是頻寬？壓縮時間為何會展寬頻率？ | 頻寬以 Hz 為單位，矩形脈衝主瓣集中 90% 能量，掌握傅立葉五大物理性質。 |
| [4. 數位調變、解調與適應性傳輸機制](modulation.md) | 如何利用正弦波傳送 0/1 並在雜訊中精準還原？ | ASK/PSK/QAM 星座圖映射、I/Q 正交雙載波解調，以及依 SNR 動態調整的 AMC 策略。 |

---

## 實體層在通訊系統中的位置

```mermaid
sequenceDiagram
    participant App as "上層通訊協定 (Upper Layers)"
    participant PHY_Tx as "傳送端實體層 (PHY Tx)"
    participant Media as "實體傳輸媒介 (無線電磁波)"
    participant PHY_Rx as "接收端實體層 (PHY Rx)"
    participant App_Rx as "接收端上層協定"

    App->>PHY_Tx: 邏輯位元流 (e.g. 1 0 1 1 0 0 1)
    Note over PHY_Tx: 產生基頻脈衝 s(t) 並<br/>乘上高頻載波調變 s(t) cos(2πfc t)
    PHY_Tx->>Media: 高頻帶通電磁波訊號
    Note over Media: 大氣媒介傳播
    Media->>PHY_Rx: 接收訊號 r(t)
    Note over PHY_Rx: 乘載波 → 低通濾波 (LPF) → 放大還原 s(t)
    PHY_Rx->>App_Rx: 還原的位元流 (1 0 1 1 0 0 1)
```

準備好探索實體層的底層奧秘了嗎？請點擊進入第一節：[1. 正弦波特性與通式](sine-wave.md)。
