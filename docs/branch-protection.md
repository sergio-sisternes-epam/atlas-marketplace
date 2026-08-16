# Branch protection checklist (main)

Apply in GitHub → Settings → Branches → Branch protection rule for `main`:

1. Require a pull request before merging
2. Require approvals (at least 1)
3. Require status checks to pass: `validate-and-pack` (after first CI run on a PR)
4. Do not allow bypassing the above for administrators (recommended)
5. Restrict who can push to matching branches (optional)

Publish of a new package pin = merge of a PR that updates `apm.yml` + packed artefacts.
