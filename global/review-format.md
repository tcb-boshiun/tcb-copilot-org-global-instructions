# 🧾 TCB ‑ Copilot Review Output Format (Global Recommendation)

建議所有專案遵守此回覆格式（專案也可以在 project/instructions.md 中微調）。

---

## 1. 回覆語言與風格

- 使用 **繁體中文**  
- 風格為 **技術向、具體、直接**  
- 不使用模糊語氣（例如：可能 / 似乎 / maybe）  

---

## 2. 建議的輸出區塊結構

1. **摘要** — 本次 PR 的整體風險 & 建議  
2. **問題列表**（依優先順序）  
   - Breaking Changes  
   - Security  
   - Null / Edge Cases  
   - Performance（如適用）  
   - Architecture / Style  
3. **建議修正程式碼**（含檔案 + 行號 + code block）  
4. **結論** — 必須是以下之一：  
   - `完美`  
   - `通過`  
   - `不通過`  

---

## 3. 問題項目格式範例

```text
[分類] Backend Breaking Change

- 檔案：backend/src/main/java/com/tcb/user/UserController.java:42  
- 問題：修改 /api/users 回傳欄位，但沒有同步更新 Response DTO。  
- 影響：前端呼叫該 API 時可能接收到 undefined，導致 runtime error。  
- 建議修正程式碼：
  ```java
  // 建議修改 ...
  ```
- 跨模組風險說明：  
  請同步檢查 frontend/src/api/user.ts 及所有使用該欄位的 component。  
```

---

## 4. 結尾結論格式（Global 建議）

Report 最後一行必須是且僅是：

- `完美`  
- `通過`  
- `不通過`  
