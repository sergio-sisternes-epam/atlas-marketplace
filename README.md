# apm-marketplace

Private APM marketplace **registry only** for Grok-native skills.

## Packages

| Package | Source | Pin |
|---------|--------|-----|
| `okf` | `sergio-sisternes-epam/okf` | SHA `d734f78c384e767e52ab81bf4c02ca5940d56363` |

## Consumer (private)

```bash
apm marketplace add sergio-sisternes-epam/apm-marketplace
apm install okf@apm-marketplace -t grok-build
```

Requires GitHub auth for private repos.

## Governance

- **Pin changes only via pull request** to `main` (no direct pin push).
- Enable **branch protection** on `main`: required PR, required reviewers, required status check `validate-and-pack` once CI is active. See `docs/branch-protection.md`.
- CI (GitHub Actions adapter): validate registry layout → `apm pack` → fail on `marketplace.json` drift.
- Canonical model lives in the apm skill (`references/ci-cd-canonical.md`); this workflow is an **example adapter**, not the model.

## Authoring a pin update

1. Point `marketplace.packages[].ref` (or version) at the package commit/tag.
2. Run `apm pack` and commit `.claude-plugin/marketplace.json`.
3. Open PR; wait for CI; human review and merge.
