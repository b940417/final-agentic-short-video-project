# Hermes Agent 系統執行軌跡 (Execution Trace)

本文件記錄了「國立臺南大學資訊工程學系 60秒形象宣傳影片」在 **Hermes Agent 桌面版應用程式 (GUI)** 中的實際執行軌跡。

---

## 1. 執行路徑與環境聲明
*   **執行工具**：Hermes Agent Desktop App
*   **實作形式**：**零付費 Token 之 Mock/Stub 執行路徑**。
*   **執行原理**：透過在 Hermes GUI 中建立 5 個功能專一的 Agent 節點，並手動/半自動加載預設之提示詞與輸出規則。Agents 之間不透過雲端 paid API，而是藉由本地 Mock 腳本將結果寫入 `/handoff` 資料夾，完全達成公平性與零成本規範。

---

## 2. GUI 工作流執行軌跡 (GUI Workflow Steps)

### 步驟一：啟動與企劃大綱生成 (Planner Agent)
1.  **操作**：在 Hermes GUI 中載入 `planner_agent.md`，輸入原始需求：*「製作南大資工系 60 秒宣傳片腳本，受眾為高中生。」*
2.  **執行狀態**：Planner 節點成功觸發。
3.  **資料輸出**：在 Hermes 介面中確認產出 6 個場景結構，並由系統自動寫入本地檔案：
    *   `./handoff/project_brief.json`

### 步驟二：腳本文字撰寫 (Script Agent)
1.  **操作**：在 GUI 中將工作流指派（Delegate）給 Script Agent。
2.  **執行狀態**：Script Agent 讀取大綱 JSON，針對各場景進行文字創作與語速檢查（1秒不超過4字）。
3.  **資料輸出**：寫入本地檔案：
    *   `./handoff/script_output.json`

### 步驟三：分鏡視覺規劃 (Visual Agent)
1.  **操作**：GUI 自動將 Script 的輸出傳遞給 Visual Agent 節點。
2.  **執行狀態**：Visual Agent 依據台詞規劃拍攝畫面與開源素材清單，並標記肖像權警示。
3.  **資料輸出**：寫入本地檔案：
    *   `./handoff/visual_output.json`

---

## 3. Reviewer 審查與修正軌跡 (Review & Revision Loop)

本系統執行過程中，在 GUI 介面成功觸發並記錄了一次「**自動語速審查與修正循環**」：

1.  **首輪審查 (Round 1 - REJECTED)**：
    *   **偵測事件**：Reviewer Agent 讀取 `visual_output.json` 時，發現 **Scene 2 旁白字數高達 41 字（時長僅 10 秒）**，語速為 4.1 字/秒，超過系統設定的舒適語速上限（4.0 字/秒）。
    *   **GUI 輸出狀態**：Reviewer 節點亮起紅燈，在介面輸出 `STATUS: REJECTED`。
    *   **修正指派**：系統寫入 `./handoff/reviewer_feedback.json`，並發送修訂通知（Revision Request）要求 Script Agent 縮減 Scene 2 字數。

2.  **自動修正與二輪審查 (Round 2 - APPROVED)**：
    *   **修正行為**：Script Agent 讀取反饋 JSON，將 Scene 2 旁白由 41 字精簡為 27 字。
    *   **通過審查**：Visual Agent 重新產生對應分鏡後，Reviewer Agent 二度審查，確認語速降至 2.7 字/秒，無其他事實與版權風險，GUI 介面亮起綠燈，輸出 `STATUS: APPROVED`。

---

## 4. 最終整合與工作流終止 (Finalizer Agent)

1.  **操作**：Reviewer 通過後，GUI 將 APPROVED 狀態與腳本傳遞至 Finalizer Agent。
2.  **執行狀態**：Finalizer 完成格式化，並產出最終的拍攝與法規檢核清單。
3.  **資料輸出**：寫入最終輸出目錄：
    *   `./outputs/final_shooting_list.json`
4.  **系統狀態**：工作流成功終止（Halted），關閉所有 Agent 節點。