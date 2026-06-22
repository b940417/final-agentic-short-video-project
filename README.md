# 國立臺南大學資訊工程學系 60秒形象宣傳影片 

### 加分項目標示：`NUTN CSIE 60-second promotional video`

本專案為 **Multimedia Systems - AI Agentic Labs** 的自主學習作業成果。我們使用 **Hermes Agent** 平台設計並實作了一個受控式的多代理人（Multi-Agent）影片企劃與製作工作流，並產出一支符合 60 秒規格之南大資工形象宣傳短片。

---

## 專案成員

*   **成員介紹**：
    *   資工三 S11259036 傅蜂貴

---

## 開發平台與實作形式

*   **使用平台**：**Hermes Agent (桌面版 App)**
*   **實作形式**：
    *   本專案採用 **Hermes Desktop GUI** 建立 5 個功能專一的代理人角色（Planner, Script, Visual, Reviewer, Finalizer）。
    *   工作流透過非同步的結構化 **JSON Handoff** 進行資料交接與局部反饋修正。
    *   執行過程完全採用桌面版可視化介面操作，並已將執行軌跡進行圖文記錄。

---

## 檔案目錄導覽

您可以在本倉庫的以下路徑中閱讀對應的作業成果：

```
Final_Project_Repo/
├── README.md                     <-- 本導覽說明文件
├── report/
│   └── Final_Report.pdf  <-- 專案報告 PDF (包含系統設計、執行 trace、對照組評估)
├── agents/                       <-- 5 個 Agent 的 Markdown 角色與 Prompt 設定檔
│   ├── planner_agent.md
│   ├── script_agent.md
│   ├── visual_agent.md
│   ├── reviewer_agent.md
│   └── finalizer_agent.md
├── handoff/                      <-- 工作流執行中各節點交接之中間 JSON 檔案
│   ├── project_brief.json
│   ├── script_output.json
│   ├── visual_output.json
│   └── reviewer_feedback.json
├── traces/                       <-- Hermes Desktop UI 執行軌跡、GUI 截圖與日誌說明
│   ├── execution_trace.md
│   └── gui_run_screenshot.png
├── outputs/                      <-- 最終多媒體成果與製作輸出
│   ├── final_video.mp4           <-- 🎬 60秒短影片檔案 (唯一多媒體成果)
│   └── final_shooting_list.json  <-- Finalizer 輸出的最優化腳本與拍攝檢核表
└── baseline/                     <-- 用於評估對比之單一 Prompt 對照組
    └── single_agent_baseline.md
```

---

## 60秒短影片檔案資訊

*   **檔案位置**：`outputs/final_video.mp4`
*   **影片長度**：整整 60 秒（00:00 - 01:00）
*   **解析度與格式**：720p (720x1280), MP4
*   **內容特徵**：包含繁體中文字幕與全程中文旁白語音。

---

## 零付費 Token 完成性聲明 (Zero-Paid-Token Declaration)

本專案之工作流設計與執行完全基於「**零付費 Token（Zero-Paid-Token）路徑**」完成。
1.  我們並未要求、亦無使用任何個人付費 API Key、商業 LLM 額度、或訂閱任何付費 AI 影音生成服務。
2.  工作流中的對話、修正與交接紀錄，皆在 Hermes 桌面版 App 中，配合本地端免費資源及預設 Mock 機制受控執行。
3.  本專案已在報告第七章及 `traces/execution_trace.md` 中詳細說明如何以無成本方案重現此主要工作流程。

---

## 素材來源與授權說明 (Sourcing & Licensing)

影片中使用的所有畫面與聲音素材均符合非侵權與合規性要求，來源清單如下：

| 素材名稱/類型 | 來源說明 | 授權/版權狀態 |
| :--- | :--- | :--- |
| **校園與系館空景、電腦教室、成果發表海報** | 團隊成員於國立臺南大學榮譽校區實地拍攝。 | 本人自主版權，允許公開發布。 |
| **出鏡教師、學生、專題簡報人物** | 國立臺南大學資工系真實師生。 | 拍攝前均已取得本人之肖像權使用同意。 |
| **螢幕展示內容 (代碼、AI 圖表、海報)** | 團隊預先製作之無個資學術示意畫面，或取得作品權利人授權。 | 無洩漏個資與機密，允許公開展示。 |
| **背景配樂 (BGM)** | 來源於Capcut免版權素材 | 可公開宣傳授權。 |
| **影片中文字體** | 系統與開源字型（如思源黑體）。 | 免費商用/開源授權。 |
