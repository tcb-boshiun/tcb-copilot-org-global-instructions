# 🔒 TCB ‑ Enterprise Security Rules

此文件定義所有專案的最低資安要求。Copilot 必須依此檢查程式與 PR 內容。

---

## 1. Backend Security

- 禁止使用字串拼接來生成 SQL，必須使用 parameterized query / ORM。  
- 不得在 log 中輸出敏感資訊，例如密碼 / Token / 身分證／個資／金融資訊。  
- 所有外部輸入（HTTP body / query / header / path variable）都必須做 validation。  
  - 使用 `@Valid` + annotation 或手動驗證並回傳明確錯誤碼。  
- 所有需要授權的 API 必須驗證 token／權限，不可跳過驗證。  
- 不得將 internal exception message 回傳给前端，以避免敏感資訊洩漏。

---

## 2. Frontend Security

- 禁止對不可信內容使用 `v-html` （或其他直接插入 HTML 的方式）。  
- 所有 API 呼叫必須處理 error 狀態（e.g. 4xx / 5xx / network error / timeout）  
- UI 不得顯示完整錯誤堆疊，也不得顯示敏感資訊。  
- 若存 token，建議使用 httpOnly cookie；若使用 localStorage / sessionStorage，需有明確設計與保護。  

---

## 3. Copilot 對資安問題的反饋格式

當 Copilot 偵測到潛在資安問題，回覆必須包含：

1. 檔案 + 行號  
2. 問題類型（例如 SQL injection / XSS / Token handling）  
3. 潛在後果（例如資料外洩、權限繞過、CSRF）  
4. 修正建議程式碼範例  
5. 建議該 PR 不通過 (除非修正)  
