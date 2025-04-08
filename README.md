# Cloud Native Assignment 2

## 說明

本repo為雲原生應用程式開發的Assignment 2，包括：

- 建立公開 Repository
- 建立並使用多個分支
- Pull Request 操作與留言互動
- Issue 與 Template 的建立與使用
- 設計 GitHub Action，自動執行成功與失敗的測試

---

## 分支設計

| 分支名稱 | 說明 |
|----------|------|
| `main`   | 主分支 |
| `hw1-p`  | 測試成功的 GitHub Action |
| `hw1-f`  | 測試失敗的 GitHub Action |

---

## Pull Request 操作

- **PR from `hw1-p` to `main`**：
  - 觸發 GitHub Action，並通過 
  - 有留言互動，包含程式碼層級留言
- **PR from `hw1-f` to `main`**：
  - 觸發 GitHub Action，並失敗

---

## Issue 與模板

- 本專案有建立一個 Issue，並維持 open 狀態
- 使用 `.github/ISSUE_TEMPLATE/bug_report.md` 建立 Issue Template，方便標準化回報格式

---

## GitHub Action 設計

本作業使用 GitHub Action 自動執行工作流程，並根據 PR 來源分支名稱決定是否通過：

```yaml
if [[ "$GITHUB_HEAD_REF" == "hw1-f" ]]; then
  exit 1 # 故意讓 hw1-f PR 失敗
else
  exit 0 # 其餘分支通過
fi
```
## ✔️ 成功與失敗條件

- **成功條件**：來自 `hw1-p` 的 PR → 成功執行 GitHub Action
- **失敗條件**：來自 `hw1-f` 的 PR → 故意觸發錯誤，GitHub Action 執行失敗

