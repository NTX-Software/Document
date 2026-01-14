# GitHub Settings Check List

Please have the administrator (Admin) go to `Settings` -> `Branches` -> `Add branch protection rule` and configure the following:

### 🔒 Protection Rules for `main` Branch
- [ ] **Branch name pattern**: `main`
- [ ] **Require a pull request before merging**: Check (Enabled)
    - [ ] **Require approvals**: Set to `2` or more
- [ ] **Require status checks to pass before merging**: (Check if CI/CD is present)
- [ ] **Do not allow bypassing the above settings**: Check (Prevent accidental bypass)
- [ ] **Lock branch**: (Optional) Only enable for strict release windows

### 🔒 Protection Rules for `develop` Branch
- [ ] **Branch name pattern**: `develop`
- [ ] **Require a pull request before merging**: Check (Enabled)
    - [ ] **Require approvals**: Set to `2` (Mandatory Code Review)
- [ ] **Require status checks to pass before merging**: (Recommended check to ensure Build Pass)

### ⚙️ General Settings
- [ ] **Default branch**: Recommended setting: `develop` (for devs to see progress) or `main` (for stable view).
- [ ] **Automatically delete head branches**: Check (Auto-delete feature branches after merge).

### 👮‍♂️ Ruleset: Enforce Branch Naming (New!)
Go to `Settings` -> `Rules` -> `Rulesets` -> `New ruleset` -> `New branch ruleset`.

- **Name**: `Enforce Branch Naming`
- **Enforcement status**: `Active`
- **Target branches**:
    - **Include by pattern**: `*` (or `**` to include all branches)
- **Rules**:
    - [ ] **Restrict branch names**: Check
        1. Click **Add restriction**.
        2. In the "Add a metadata restriction" dialog:
            - **Applies to**: Select `Branch name`.
            - **Requirement**: Select `Must match a given regex pattern`.
            - **Matching pattern**: Enter `^(main|develop|feature/.*|bugfix/.*|hotfix/.*|release/.*)$`
        3. Click **Add**.
        - *Note: This regex ensures only these standard branch types can be pushed.*
