# Contributing Guide

Welcome to the project! To ensure code quality and smooth collaboration, please adhere to the following development workflow.

## 🌳 Branching Model

This project uses a dual main branch strategy:

| Branch Name | Purpose | Rules |
| :--- | :--- | :--- |
| **`main`** | **Production Ready** | 🛡️ **Protected**: Direct Push is forbidden. Only accepts PRs from `develop` for official releases. |
| **`develop`** | **Integration** | 🛡️ **Protected**: Direct Push is forbidden. All new features must be merged here. |
| `feature/*` | **Feature Development** | Branched from `develop`. Example: `feature/login-api` |
| `bugfix/*` | **Bug Fixes** | Branched from `develop`. Example: `bugfix/login-error` |
| `hotfix/*` | **Hotfix** | Branched from `main`. Example: `hotfix/critical-crash` |

## 🚀 Development Workflow

### 1. Start Development
Always create your work branch from `develop`.
> [!IMPORTANT]
> **Naming Policy Enforced**: The repository uses strict rules. You **cannot** push branches that do not match `feature/*`, `bugfix/*`, or `hotfix/*`.

```bash
# 1. Checkout develop and pull latest
git checkout develop
git pull origin develop

# 2. Create new branch (Follow naming convention)
# Feature:
git checkout -b feature/your-feature-name
# Or Bugfix:
# git checkout -b bugfix/your-bug-name
# Or Hotfix:
# git checkout -b hotfix/your-hotfix-name
```

### 2. Commit & Push
After development, push your branch to GitHub:

```bash
git push -u origin feature/your-feature-name
```

### 3. Create Pull Request (PR) -> `develop`
1.  Open a Pull Request on GitHub.
2.  Set **Base (Target)** to `develop`.
3.  Set **Compare (Source)** to your Feature branch.
4.  Fill in the PR content (refer to PR Template).
5.  Assign Reviewers.

### 4. Review & Merge
*   Must pass CI/CD tests (if any).
*   Must receive at least 1 approval from Reviewer.
*   Once merged, your code officially enters the `develop` mainline.

## 📦 Release to Main
*(Usually performed by QA or Tech Lead)*

When `develop` is verified as stable by QA:
1.  Create **Pull Request**: `develop` -> `main`.
2.  Verify all tests pass.
3.  Merge to `main`.
4.  Tag the version on `main`: `git tag -a v1.0.0 -m "Release v1.0.0"`.
