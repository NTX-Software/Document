# Contributing Guide 專案貢獻指南

歡迎加入本專案！為了確保代碼品質與協作順暢，請務必遵守以下開發流程。

## 🌳 分支策略 (Branching Model)

本專案採用雙主線分支策略：

| 分支名稱 (Branch) | 用途 (Purpose) | 權限/規則 (Rules) |
| :--- | :--- | :--- |
| **`main`** | **穩定發佈版本** (Production Ready) | 🛡️ **Protected**: 禁止直接 Push。僅接受來自 `develop` 的 PR 做為正式發佈。 |
| **`develop`** | **開發整合主線** (Integration) | 🛡️ **Protected**: 禁止直接 Push。所有新功能必須合併回此處。 |
| `feature/*` | **新功能開發** | 從 `develop` 分支出去。範例：`feature/login-api` |
| `bugfix/*` | **Bug 修復** | 從 `develop` 分支出去。範例：`bugfix/login-error` |
| `hotfix/*` | **緊急修復** (Hotfix) | 從 `main` 分支出去。範例：`hotfix/critical-crash` |

## 🚀 開發流程 (Development Workflow)

### 1. 開始開發 (Start)
請務必從 `develop` 分支建立您的工作分支：
> [!IMPORTANT]
> **強制命名規則 (Naming Policy Enforced)**: 專案已設定嚴格規則。您 **無法** 推送不符合 `feature/*`, `bugfix/*`, 或 `hotfix/*` 格式的分支。

```bash
# 1. 切換回 develop 並更新到最新
git checkout develop
git pull origin develop

# 2. 建立新分支 (請依照命名規則)
# 功能開發:
git checkout -b feature/your-feature-name
# 或 Bug 修復:
# git checkout -b bugfix/your-bug-name
# 或 Hotfix (緊急修復):
# git checkout -b hotfix/your-hotfix-name
```

### 2. 提交與推送 (Commit & Push)
開發完成後，請將分支推送到 GitHub：

```bash
git push -u origin feature/your-feature-name
```

### 3. 建立 Pull Request (PR) -> `develop`
1.  在 GitHub 上發起 Pull Request。
2.  **Base (目標分支)** 選擇 `develop`。
3.  **Compare (來源分支)** 選擇您的 Feature 分支。
4.  填寫 PR 內容 (請參考 PR Template)。
5.  指定 Reviewers 進行 Code Review。

### 4. 審查與合併 (Review & Merge)
*   必須通過 CI/CD 測試 (如有)。
*   必須獲得至少 1 位 Reviewer 的核准 (Approve)。
*   合併後，您的程式碼正式進入 `develop` 開發主線。

## 📦 發佈流程 (Release to Main)
*(通常由 QA 或 Tech Lead 執行)*

當 `develop` 分支經過 QA 驗證穩定後：
1.  建立 **Pull Request**: `develop` -> `main`。
2.  確認所有測試通過。
3.  合併至 `main`。
4.  在 `main` 上打上標籤 (Tag) 發佈版本：`git tag -a v1.0.0 -m "Release v1.0.0"`。
