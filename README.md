# apm-marketplace

Private APM marketplace **registry only** for Grok-native skills.

## Packages

| Package | Source | Release | Pin |
|---------|--------|---------|-----|
| `okf` | `sergio-sisternes-epam/okf` | v0.2.1 | SHA `5246f7b193b58a32ac8a15fc76aedf37c42b042c` |
| `atlas` | `sergio-sisternes-epam/atlas` | v0.9.0 | SHA `2b6659e5440886c7abbd9ad10686fa3a0100813b` |
| `discuss` | `sergio-sisternes-epam/discuss` | v0.3.8 | SHA `d77c9f9c4c952d327811bfec9cfa764a6c56d1d6` |
| `think` | `sergio-sisternes-epam/think` | v0.1.0 | SHA `874613a67018c74ee95f857416fb315d2f80b92b` |
| `atlas-cartograph` | `sergio-sisternes-epam/atlas-cartograph` | v0.1.0 | SHA `2372272dc5c282f1b1a472483a412ef394971764` |
| `autogenesis` | `sergio-sisternes-epam/autogenesis` | v0.4.1 | SHA `990d4f1a3e761bafb0385c91a0afbde38b3bd9ea` |

## Consumer (private)

```bash
apm marketplace add sergio-sisternes-epam/apm-marketplace
apm install okf@apm-marketplace
apm install atlas@apm-marketplace
apm install discuss@apm-marketplace
apm install think@apm-marketplace
apm install atlas-cartograph@apm-marketplace
apm install autogenesis@apm-marketplace
```

Requires GitHub auth for private repos. Optional `-t` selects a consumer target
when the project does not already declare one.

## Governance

- **Pin changes only via pull request** to `main` (no direct pin push).
- Enable **branch protection** on `main`: required PR, required reviewers, required status check `validate-and-pack` once CI is active. See `docs/branch-protection.md`.
- CI (GitHub Actions adapter): validate registry layout → `apm pack` with `apm-cli==0.30.0` → fail on `marketplace.json` drift.
- Canonical model lives in the apm skill (`references/ci-cd-canonical.md`); this workflow is an **example adapter**, not the model.

## Authoring a pin update

1. Point `marketplace.packages[].ref` (or version) at the package commit/tag.
2. Run `apm pack` with apm-cli 0.30.0 and commit `.claude-plugin/marketplace.json`. `apm marketplace check` is optional: it currently fails for raw commit-SHA pins even when pack and CI succeed.
3. Keep `AGENTS.md`, `CHANGELOG.md`, `CONTRIBUTING.md`, and `README.md` aligned.
4. Open PR; wait for CI; human review and merge.

See `CONTRIBUTING.md` for the full procedure.
