# GitHub 設定檢查清單 (Settings Check List)

請管理員 (Admin) 進入 `Settings` -> `Branches` -> `Add branch protection rule` 進行以下設定：

### 🔒 針對 `main` 分支的保護規則
- [ ] **分支名稱模式 (Branch name pattern)**: `main`
- [ ] **要求合併前建立 PR (Require a pull request before merging)**: 勾選 (開啟)
    - [ ] **要求核准 (Require approvals)**: 設定為 `2` 或更多
- [ ] **要求合併前通過狀態檢查 (Require status checks to pass before merging)**: (若有 CI/CD 請勾選)
- [ ] **不允許略過上述設定 (Do not allow bypassing the above settings)**: 勾選 (防止管理員手滑)
- [ ] **鎖定分支 (Lock branch)**: (選用) 如果是非常嚴格的發佈窗口才開啟

### 🔒 針對 `develop` 分支的保護規則
- [ ] **分支名稱模式 (Branch name pattern)**: `develop`
- [ ] **要求合併前建立 PR (Require a pull request before merging)**: 勾選 (開啟)
    - [ ] **要求核准 (Require approvals)**: 設定為 `2` (Code Review 強制性)
- [ ] **要求合併前通過狀態檢查 (Require status checks to pass before merging)**: (建議勾選，確保 Build Pass)

### ⚙️ 其他設定 (General)
- [ ] **預設分支 (Default branch)**: 建議設為 `develop` (方便開發者預設看到開發進度) 或 `main` (若希望預設展示穩定版)。
- [ ] **自動刪除 head 分支 (Automatically delete head branches)**: 勾選 (PR 合併後自動刪除 feature branch，保持乾淨)。

### 👮‍♂️ Ruleset: 強制分支命名 (Ruleset: Enforce Branch Naming)
請至 `Settings` -> `Rules` -> `Rulesets` -> `New ruleset` -> `New branch ruleset`。

- **名稱 (Name)**: `Enforce Branch Naming`
- **執行狀態 (Enforcement status)**: `Active`
- **目標分支 (Target branches)**:
    - **Include by pattern**: `*` (或 `**` 以選取所有分支)
- **規則 (Rules)**:
    - [ ] **限制分支名稱 (Restrict branch names)**: 勾選
        1. 點擊 **Add restriction** (新增限制)。
        2. 在 "Add a metadata restriction" 對話框中：
            - **Applies to**: 選擇 `Branch name`。
            - **Requirement**: 選擇 `Must match a given regex pattern`。
            - **Matching pattern**: 輸入 `^(main|develop|feature/.*|bugfix/.*|hotfix/.*|release/.*)$`
        3. 點擊 **Add**。
        - *注意：此 Regex 確保只有這些標準分支名稱能被建立或推送。*
