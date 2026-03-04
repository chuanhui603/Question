## 1) 畫面與欄位對應

### 1. 左側流量表欄位串接
 **H2O2 即時加藥量 是下述其中一個欄位嗎?**
  - `amount_H2O2_P_209AB`
  - `amount_BaCl2_P_210AB`
  - `amount_PLM_P_211AB`
### 2. 中間COP硼廢水處理流程串接
- **pH 值**
    - `pH_202_A`
- **氧化反應槽是下述其中一個欄位嗎?**
    - `ORP_1`, 
    - `ORP_2`, 
    - `ORP_3` 
- **進水流量**：
    - `flow_FIT201`（$m^3$）
- **廢水排放量**：
    - `flow_waste`（$m^3$）
### 3. 右側長條圖欄位串接
- **儲槽液位**
  - `level_B_waste_collect`（收集池）
  - `level_react`（反應槽）
  - `level_B_waste_medium`（中繼池）
- **藥劑殘量（%）**
  - `H2SO4_LIT_116`
  - `NaOH_LIT_117`
  - `H2O2_LIT_209`
  - `BaCl2_LIT_210`

- **加藥/反應狀態**
  - `switch_dose_H2O2`
  - `switch_react_BaCl2`
- **脫水系統**
  - `switch_dewater_run`
  - `switch_dewater_error`

## 2) 資料串接問題
1.  **右上角nav疑問**
   ![右上角 nav 畫面](./右上角nav.jpg)
  - 這個廠務工程師是有要接資料庫?

2. **警報閥值（Thresholds）缺失**
   - 目前表格有「`setting` / `proceed`」，但缺乏明確高低警報值（Hi/Lo/HH/LL）
   - 雖有 `LS206-(HH)` 等字樣，但較像硬體開關點，未必可直接當前端告警規則
   - 影響：前端無法正確顯示紅框/紅燈異常狀態

3. **計算欄位責任不明**
   - 如 `calc_H2O2`、`calc_dose`
   - 需確認由後端直接提供，或由前端用原始欄位即時計算
   - 影響：API 設計、更新頻率、前端效能與一致性

4. **單位轉換規範不明**
   - 液位單位可能同時出現 `%` 與 `mm`
   - 需定義前端統一顯示單位與換算規則
   - 影響：長條圖/液位圖比例可能錯誤
