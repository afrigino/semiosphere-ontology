# Branch Protection Configuration

This document describes the branch protection rules that should be configured for the `main` branch of this repository.

## Why Branch Protection?

This repository is intended to function as a **canonical, citable reference artifact** (as stated in the README). Branch protection ensures:

- Theoretical integrity is maintained through required validation checks
- Changes are reviewed before merging
- Accidental direct pushes to main are prevented
- The commit history remains clean and traceable

## Required Configuration Steps

### 1. Access Repository Settings

1. Navigate to the repository on GitHub: https://github.com/afrigino/semiosphere-ontology
2. Click on **Settings** tab
3. In the left sidebar, click **Branches** under "Code and automation"

### 2. Add Branch Protection Rule

Click **Add branch protection rule** and configure the following:

#### Branch Name Pattern
```
main
```

#### Protection Settings

**Require a pull request before merging**
- ✅ Enable this option
- ✅ Require approvals: **1** (or more if desired)
- ✅ Dismiss stale pull request approvals when new commits are pushed
- ✅ Require review from Code Owners (ensures CODEOWNERS file is respected)

**Require status checks to pass before merging**
- ✅ Enable this option
- ✅ Require branches to be up to date before merging
- Required status checks to select (search for these exact names after creating a PR):
  - `shacl` (from SHACL Validation workflow)
  - `render-mermaid` (from Render Mermaid Diagrams workflow)
  - `Branch Protection Compliance` (from Branch Protection Checks workflow)

**Require conversation resolution before merging**
- ✅ Enable this option (ensures all review comments are addressed)

**Require signed commits** (optional but recommended)
- ☐ Enable if you want to require GPG signatures on commits

**Require linear history** (optional but recommended)
- ✅ Enable this option (prevents merge commits, requires rebase or squash)

**Do not allow bypassing the above settings**
- ✅ Enable this option (applies rules to administrators)
- Note: Administrators can still temporarily disable protection if needed for emergency fixes

**Restrict who can push to matching branches** (optional)
- ☐ Enable if you want to restrict direct pushes to specific users/teams
- If left disabled, the "Require a pull request" rule will prevent direct pushes

**Allow force pushes**
- ❌ Disable this option (prevents force pushes which could rewrite history)

**Allow deletions**
- ❌ Disable this option (prevents accidental deletion of the main branch)

### 3. Save the Protection Rule

Click **Create** or **Save changes** at the bottom of the page.

## Verification

After configuring branch protection, verify it's working:

1. Try to push directly to main - it should be rejected
2. Create a test PR and verify that:
   - The SHACL validation check must pass
   - The Mermaid rendering check must pass
   - At least one approval is required
   - Code owner review is required for files matching CODEOWNERS patterns

## CODEOWNERS File

The `.github/CODEOWNERS` file has been created to define code ownership. This ensures that:

- All changes require approval from @afrigino
- Core ontology files (`/ont/`, `/shacl/`) require explicit approval
- Tests and documentation changes require approval
- Workflow changes require approval

## CI/CD Integration

The existing GitHub Actions workflows will automatically run on:
- Pull requests to any branch
- Direct pushes to any branch (will be prevented on main after protection is enabled)

Required checks:
- **SHACL Validation** (`.github/workflows/shacl.yml`) - Ensures ontology validity
- **Render Mermaid Diagrams** (`.github/workflows/render-mermaid.yml`) - Ensures diagrams render correctly

## Emergency Override

If an administrator needs to bypass branch protection in an emergency:

1. Go to Settings → Branches → Edit the branch protection rule
2. Temporarily uncheck "Do not allow bypassing the above settings"
3. Make the emergency fix
4. Re-enable the protection setting

## Additional Recommendations

1. **Enable branch protection for tags** (optional):
   - Protect version tags to prevent accidental modification
   - Pattern: `v*` for semantic version tags

2. **Set up branch deploy protection** (if using GitHub Environments):
   - Configure deployment environments with required reviewers

3. **Monitor security alerts**:
   - Enable Dependabot alerts
   - Enable Secret scanning
   - Enable Code scanning (if available)

4. **Regular audits**:
   - Periodically review who has write access to the repository
   - Review and update CODEOWNERS as needed
   - Ensure branch protection rules remain enforced

## References

- [GitHub Branch Protection Documentation](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)
- [CODEOWNERS Documentation](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners)
- [Required Status Checks](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches#require-status-checks-before-merging)
