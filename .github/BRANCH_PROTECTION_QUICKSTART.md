# Quick Start: Branch Protection Setup

This guide provides the minimal steps needed to enable branch protection for the `main` branch.

## Prerequisites

- Repository owner or admin access to https://github.com/afrigino/semiosphere-ontology
- The files in this PR have been merged to the `main` branch

## Setup Steps (5 minutes)

### 1. Navigate to Branch Settings

```
GitHub → Repository → Settings → Branches → Add rule
```

### 2. Configure Branch Protection

**Branch name pattern:** `main`

**Enable these checkboxes:**

✅ Require a pull request before merging
  - ✅ Require approvals: 1
  - ✅ Dismiss stale pull request approvals when new commits are pushed
  - ✅ Require review from Code Owners

✅ Require status checks to pass before merging
  - ✅ Require branches to be up to date before merging
  - Add status checks (search for these exact names):
    - `shacl`
    - `render-mermaid`
    - `Branch Protection Compliance`

✅ Require conversation resolution before merging

✅ Require linear history

✅ Do not allow bypassing the above settings

❌ Allow force pushes (disabled)

❌ Allow deletions (disabled)

### 3. Save

Click **Create** at the bottom of the page.

## Verification

After saving, try to:
1. Push directly to `main` - should be rejected ✓
2. Create a PR - should require approvals and passing checks ✓

## What This Protects

- ✅ Prevents direct pushes to main
- ✅ Requires code review from @afrigino
- ✅ Ensures SHACL validation passes
- ✅ Ensures diagrams render correctly
- ✅ Enforces commit message quality
- ✅ Prevents sensitive file commits
- ✅ Validates required files exist

## Need Help?

See [BRANCH_PROTECTION.md](BRANCH_PROTECTION.md) for detailed documentation.

## Implementation Details

The following files implement branch protection:

- `.github/CODEOWNERS` - Defines code ownership (requires @afrigino approval)
- `.github/workflows/branch-protection.yml` - Automated quality checks
- `.github/workflows/shacl.yml` - Validates ontology integrity
- `.github/workflows/render-mermaid.yml` - Validates diagram rendering

All workflows run automatically on pull requests to `main`.
