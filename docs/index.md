# 網路課程筆記：實體層與資料連接層

這份筆記整理自課堂內容，目標是讓**沒有上過這堂課的人**，光看這份筆記也能理解實體層 (Physical Layer) 與資料連接層 (Data Link Layer) 的核心概念與底層運作原理。

---

## 怎麼讀這份筆記

- **循序漸進的推導脈絡**：每個章節先說明「為什麼需要這個技術」，再以嚴謹的物理與數學邏輯推導核心原理。
- **初學者問答 (Q&A)**：每節文末皆整理「初學者常見盲點與誤區」，直擊思考死角。
- **圖解與算式兼備**：波形圖、頻譜圖、Mermaid 流程圖搭配 MathJax 公式與經典範例詳解。

---

## 章節導覽

### [實體層 Physical Layer](physical-layer/index.md)
負責將電腦中的邏輯位元轉換為能在實體媒介中傳播的物理訊號。
- **知識推進路徑**：
  1. [正弦波特性與通式](physical-layer/sine-wave.md)：物理界最純粹的連續訊號與三大核心參數。
  2. [方波構成與傅立葉分析](physical-layer/fourier-and-square-wave.md)：數位方波如何由基頻與奇數次諧波疊加而成？
  3. [頻寬與傳輸極限](physical-layer/bandwidth-and-capacity.md)：有效頻寬與 Nyquist / Shannon 通道容量極限。
  4. [基頻編碼與傳輸模式](physical-layer/signal-encoding.md)：有線網路的 NRZ、曼徹斯特編碼與時脈同步。
  5. [無線傳輸與調變技術](physical-layer/modulation.md)：從正弦載波到 ASK、FSK、PSK 及高階 QAM 星狀圖。
  6. [傳輸媒介與標準規格](physical-layer/media.md)：雙絞線、光纖與無線電磁波頻段。

### [資料連接層 Data Link Layer](data-link-layer/index.md)
負責在相鄰節點之間提供可靠的點對點傳輸，包含成框（Framing）、錯誤偵測與更正（CRC / 漢明碼）、流量控制（滑動視窗）與 MAC 子層協定。

### [AI 協作與對話紀錄](ai-collaboration.md)
記錄本網站製作期間使用 AI 輔助規劃、觀念釐清、計算驗證與排版之 Prompt 與對話歷程（供課程評分查驗）。
