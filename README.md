# TCB ‑ Copilot Org Global Instructions

此 repo 用來集中管理 **TCB 組織層級** 的 GitHub Copilot 規則，供所有專案共用。內容包含：

- 全域 PR Review 規則  
- API / DTO 契約規則  
- 安全性標準  
- Review 格式與輸出標準  

## 📦 使用方式

1. 在你的專案中加入本 repo 為 submodule，例如：

```bash
git submodule add https://github.com/tcb-boshiun/tcb-copilot-org-global-instructions .copilot/org
```

2. 在專案根目錄建立 `.copilot/config.yaml`，並加入以下設定：

```yaml
version: 1

rules:
  - description: "Organization-level global rules"
    include:
      - "org/global/*.md"
    guidance: |
      請優先遵守 org/global 內所有全域規則文件。

  - description: "Project-level rules"
    include:
      - "project/*.md"
    guidance: |
      請同時遵守本專案的 instructions.md 以及 context.md（若有）。

style:
  language: "zh-TW"
  tone: "technical"
  format: "clean"

assistant:
  avoid_deprecated: true
  prefer_small_changes: true
  follow_project_conventions: true
```

3. 建議所有 TCB 的專案統一採用此 repo 作為 Copilot 全域規則來源，以確保跨專案一致性與安全性。

---

## 📁 global/ 資料夾內容說明

- `global.md` — 全域總則  
- `security.md` — 全域資安 / 安全性規範  
- `api-contract.md` — API / DTO / Contract 聯動規則  
- `review-format.md` — Copilot Review 結果格式標準  
