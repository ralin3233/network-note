# 實體層 Physical Layer 全景導覽

實體層（Physical Layer）是 OSI 七層模型的最底層（Layer 1）。它的核心任務只有一個：**將上層的邏輯資料（0 與 1 位元串），轉換為可在真實物理媒介（銅線、光纖、空氣電磁波）中傳遞的實體訊號（電壓、光脈衝、無線電波），並在接收端還原。**

---

## 為什麼需要從「正弦波」開始學網路？

很多初學者在剛翻開網路通訊教科書時常感到困惑：

> *「我明明是來學電腦網路和軟體協定的，為什麼第一堂課老師在黑板上畫三角函數、正弦波、頻率和傅立葉轉換？」*

這個疑惑非常正常。要理解網路通訊的底層邏輯，必須掌握以下**環環相扣的知識脈絡**：

```mermaid
graph TD
    A["1. 正弦波 (Sine Wave)<br>物理界最純粹的連續訊號通式"] --> B["2. 方波的構成 (Square Wave)<br>電腦的 0 與 1 方波由無數正弦波疊加而成"]
    B --> C["3. 傅立葉分析 (Fourier Analysis)<br>時域跳變 ⟷ 頻域頻譜與高頻諧波"]
    C --> D["4. 頻寬與通道極限 (Bandwidth & Limits)<br>物理介質會濾除高頻 ⟷ Nyquist & Shannon 極限"]
    D --> E["5. 無線傳輸與調變 (Modulation)<br>天線尺寸與共享介質限制 ⟷ 將資料載入高頻正弦波 (ASK/FSK/PSK/QAM)"]
    
    style A fill:#e0f2fe,stroke:#0288d1,stroke-width:2px,color:#0f172a;
    style B fill:#dcfce7,stroke:#16a34a,stroke-width:2px,color:#0f172a;
    style C fill:#ffedd5,stroke:#ea580c,stroke-width:2px,color:#0f172a;
    style D fill:#fce7f3,stroke:#db2777,stroke-width:2px,color:#0f172a;
    style E fill:#f3e8ff,stroke:#9333ea,stroke-width:2px,color:#0f172a;
```

---

## 本章循序漸進閱讀指南

本章節按照通訊原理的演進邏輯，由淺入深拆解實體層技術：

| 章節 | 核心課題 | 一句話總結 |
|---|---|---|
| [1. 正弦波特性與通式](sine-wave.md) | 什麼是正弦波？三個基本參數是什麼？ | 任何週期訊號的基礎「積木」，用數學精確描述波形。 |
| [2. 方波構成與傅立葉分析](fourier-and-square-wave.md) | 數位方波是怎麼生出來的？ | 透過傅立葉級數，方波其實是「基頻 + 奇數次諧波」的疊加。 |
| [3. 頻寬與傳輸極限](bandwidth-and-capacity.md) | 為什麼網路線不能跑無限快？ | 媒介具有頻寬限制，Nyquist 與 Shannon 定理劃定了速度天花板。 |
| [4. 基頻編碼與傳輸模式](signal-encoding.md) | 有線網路如何用電壓傳 0/1？ | NRZ、曼徹斯特編碼解決時脈同步與直流漂移問題。 |
| [5. 無線傳輸與調變技術](modulation.md) | 無線訊號如何把 0/1 射向空中？ | 透過 ASK、FSK、PSK 與高階 QAM 把資料載入高頻載波。 |
| [6. 傳輸媒介與標準規格](media.md) | 雙絞線、光纖、天線的物理差異 | 導向式與非導向式媒介特性及常見乙太網標準（Cat6、光纖）。 |

---

## 實體層在通訊系統中的位置

```mermaid
sequenceDiagram
    participant App as 上層協定 (Data Link 以上)
    participant PHY_Tx as 傳送端實體層 (PHY Tx)
    participant Media as 實體傳輸媒介 (有線/無線)
    participant PHY_Rx as 接收端實體層 (PHY Rx)
    participant App_Rx as 接收端上層協定

    App->>PHY_Tx: 邏輯位元流 (e.g. 1 0 1 1 0 0 1)
    Note over PHY_Tx: 編碼 (Line Coding) 或<br/>調變 (Modulation)
    PHY_Tx->>Media: 連續物理訊號 (電壓 / 光波 / 電磁波)
    Note over Media: 媒介造成衰減 (Attenuation)<br/>雜訊干擾 (Noise) 與失真
    Media->>PHY_Rx: 受損但保有可辨特徵的訊號
    Note over PHY_Rx: 採樣判決 (Sampling)<br/>解調 (Demodulation) / 解碼
    PHY_Rx->>App_Rx: 還原的位元流 (1 0 1 1 0 0 1)
```

準備好探索實體層的底層奧秘了嗎？請點擊進入第一節：[1. 正弦波特性與通式](sine-wave.md)。
