# 問題文檔

##  <a id="water-quality-ph"></a> 一、 流量表單 對應欄位 {#water-quality-ph}

- **H2O2 即時加藥量**
  - `amount_H2O2_P_209AB`
  - `float`
- **BaCl_2 即時加藥量**
  - `amount_BaCl2_P_210AB`
  - `float`
- **水質監測**
  - **進水硼濃度**
    - `concentration_B`
    - `float`
  - **出水硼濃度**
    - 待確認
  - **進水量**
    - `flow_FIT201`
    - `float`
  - **出水量**
    - `flow_waste`
    - `float`

### 2. COP硼廢水處理流程 對應欄位

- **Raw Water 運作**
  - `flow_FIT201` > 0
- **pH 調整槽 狀態**
  - `pH_202_A`
- **氧化反應槽 狀態**
  - `ORP_1`
- **氧化反應槽 狀態**：
  - `sswitch_react_H2O2`
  - Boolean
- **化學沉降槽 狀態**：
  - `switch_dose_BaCl2`
  - Boolean
- **凝集槽 狀態**：
  - `switch_dose_Polymer`
  - Boolean
- **沉澱池 狀態**：
  - `switch_circ_filter`
  - Boolean
- **出水 狀態**：
  - `switch_filtrate_discharged`
  - Boolean

### 3. 統計長條圖 對應欄位

- **藥劑使用對比**
  
## 二、 資料處理問題

1. **右上角nav職位疑問**
 
![右上角 nav 畫面](img/右上角nav.jpg)
 廠務工程師這邊這個職位是有接資料庫?

2. **AI建議**

![AI建議](img/AI建議.jpg)
 這是前端處理還是資料庫有對應欄位?

3. **合規判斷**  

![合規判斷](img/合規判斷.png)
- 這裡只要前端處理?

4. **單位不一致**

 [進水量、出水量](#water-quality-ph) 對應欄位單位為(m³) 前端是mg/L 是否前端處理換算?
 [H2O2 即時加藥量、BaCl_2 即時加藥量](#water-quality-ph) 單位是L/min實作需換算為L/h(L/min*60) 是前端處理還是後端?

5. **系統狀態與告警**

-![系統狀態與告警](img/系統狀態與告警.jpg)
 這個需要傳什麼資料給前端，還是前端能自行處理?

6. **藥劑使用對比**

![藥劑使用對比](img/藥劑使用對比.jpg)
 這圖是左側H2O2 即時加藥量、BaCl2 即時加藥量的比較圖? 是純前端處理?

7. **資料庫實際資料**

目前我只收集到資料庫的 schema，但實際各欄位的儲存型態（如 int、string 等）大多尚未確認。