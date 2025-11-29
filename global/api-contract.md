# 📡 TCB ‑ API & DTO Contract Rules

定義所有專案在處理 API / DTO / 型別對應時應遵守的基本標準。

---

## 1. 後端 API 規則

- API 路徑設計須穩定、明確，避免頻繁重命名。  
- 不可直接暴露 Entity，所有輸入／輸出均須經由 DTO。  
- Request DTO、Response DTO 與 Domain Model 必須分離。  
- 若變動 API 路徑、DTO 欄位、Response 結構 → 必須視為 Breaking Change。

---

## 2. 前端對應規則

- 每個後端 DTO，都必須在前端建立對應的 TypeScript interface。  
- 若後端 DTO change，必須同步更新前端 interface + 所有使用該欄位的 component / service / composable。  
- 禁止使用 `any` 作為型別掩蓋。  

---

## 3. Copilot 的檢查責任

在 PR Review 時，Copilot 應：

1. 檢查後端是否有 controller / DTO / response 變動。  
2. 若有 → 搜尋前端呼叫對應是否同步修正接口 / 型別。  
3. 若前端未同步更新 → 必須回報「改 A 壞 B 的跨模組風險」。  
4. 若你在 project context 有提供 controller ↔ api mapping 表，Copilot 應依 mapping 做 cross‑check。
