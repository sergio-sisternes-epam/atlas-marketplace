# Default-branch protection

The active [Protect default branch ruleset](https://github.com/sergio-sisternes-epam/apm-marketplace/rules/22792606)
targets `~DEFAULT_BRANCH` (currently `main`). It was configured with owner approval
on 2026-09-10.

1. Require a pull request before merging.
2. Require an up-to-date branch and passing `validate-and-pack` from GitHub Actions.
3. Require all review conversations to be resolved.
4. Block force pushes and branch deletion, with no bypass actors (including administrators).
5. Automatically request Copilot review for non-draft PRs and new pushes.

The owner approved zero required approving reviews for this single-maintainer
repository. Code-owner approval and last-push approval are not required. Stale
approvals are dismissed on new pushes.

Automatic Copilot review requests do not guarantee review completion before
merge and depend on Copilot access and available quota. Wait for and assess
Copilot feedback before the owner merges. Copilot's separate preview approval
settings were not enabled by this change.

Publish of a new package pin = merge of a PR that updates `apm.yml` + packed artefacts.
