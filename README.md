# apm-marketplace

Private APM marketplace **registry only** for Grok-native skills.

## Packages

| Package | Source | Release | Pin |
|---------|--------|---------|-----|
| `okf` | `sergio-sisternes-epam/okf` | v0.2.1 | SHA `5246f7b193b58a32ac8a15fc76aedf37c42b042c` |
| `atlas` | `sergio-sisternes-epam/atlas` | v0.10.0 | SHA `3818586da56331949b03fe746ef21693d3c84169` |
| `discuss` | `sergio-sisternes-epam/discuss` | v0.3.9 | SHA `95b51910378fa8245b67e70a42cbf1be840b620b` |
| `think` | `sergio-sisternes-epam/think` | v0.1.0 | SHA `874613a67018c74ee95f857416fb315d2f80b92b` |
| `atlas-cartograph` | `sergio-sisternes-epam/atlas-cartograph` | v0.2.0 | SHA `584c6843fd04e0fe27c2ba67bb9be67158b37a4c` |
| `autogenesis` | `sergio-sisternes-epam/autogenesis` | v0.4.2 | SHA `01000d02c4c3588a4afc75a967f7d6002d116c9b` |

## Consumer (private)

```bash
apm marketplace add sergio-sisternes-epam/apm-marketplace --name sergio-sisternes-epam
apm install okf@sergio-sisternes-epam
apm install atlas@sergio-sisternes-epam
apm install discuss@sergio-sisternes-epam
apm install think@sergio-sisternes-epam
apm install atlas-cartograph@sergio-sisternes-epam
apm install autogenesis@sergio-sisternes-epam
```

`apm marketplace add` defaults the local name to the GitHub repo (`apm-marketplace`).
Pass `--name sergio-sisternes-epam` so installs and package deps resolve as
`pkg@sergio-sisternes-epam`. Re-add if you previously registered this catalog as
`me` or `apm-marketplace`.

Requires GitHub auth for private repos. Optional `-t` selects a consumer target
when the project does not already declare one.

## Governance

- **Pin changes only via pull request** to `main` (no direct pin push).
- Enable **branch protection** on `main`: required PR, required reviewers, required status check `validate-and-pack` once CI is active. See `docs/branch-protection.md`.
- CI (GitHub Actions adapter): validate registry layout → `apm pack` with `apm-cli==0.30.0` → fail on `marketplace.json` drift.
- Canonical model lives in the apm skill (`references/ci-cd-canonical.md`); this workflow is an **example adapter**, not the model.

## Authoring a pin update

1. Point `marketplace.packages[].ref` at the published release commit/tag and keep `version` aligned with the pinned package manifest.
2. Run `apm pack` with apm-cli 0.30.0 and commit `.claude-plugin/marketplace.json`. `apm marketplace check` is optional: it currently fails for raw commit-SHA pins even when pack and CI succeed.
3. Keep `AGENTS.md`, `CHANGELOG.md`, `CONTRIBUTING.md`, and `README.md` aligned.
4. Open PR; wait for CI; human review and merge.

See `CONTRIBUTING.md` for the full procedure.
