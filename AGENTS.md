# Agent notes for atlas-marketplace

This repository is a **public**, **registry-only** Atlas APM marketplace. It
indexes external packages; it does not vendor skill source trees.

## Source versus generated

| Path | Role |
|------|------|
| `apm.yml` | Authoritative marketplace catalog (`marketplace.packages`) |
| `.claude-plugin/marketplace.json` | Generated consumer catalog; do not edit by hand |
| `LICENSE` | Apache License 2.0 terms for this repository |
| `.github/workflows/marketplace-ci.yml` | CI adapter: layout validate → `apm pack` (apm-cli 0.30.0) → drift check |
| `README.md` | Consumer README: purpose, catalog pins, install/use |
| `CONTRIBUTING.md` | Pin-update and PR procedure |
| `CHANGELOG.md` | User-visible catalog history (`Unreleased` first) |
| `.github/ISSUE_TEMPLATE/` | Bug and feature issue templates |
| `.github/PULL_REQUEST_TEMPLATE.md` | Pull request checklist |

Do not add `SKILL.md` or `.apm/skills/` at the marketplace root.

## Current catalog pins

Pins are immutable commit SHAs for the latest verified stable GitHub release of
each external package:

- `okf` → `sergio-sisternes-epam/okf` @ `5246f7b193b58a32ac8a15fc76aedf37c42b042c` (v0.2.1)
- `atlas` → `sergio-sisternes-epam/atlas` @ `40e11c65e243236850c26fc6cd5a04acdd483eb4` (v0.12.0)
- `discuss` → `sergio-sisternes-epam/discuss` @ `af2d2fa4759c00d4ae77115c0fe710c439f8c958` (v0.4.0)
- `think` → `sergio-sisternes-epam/think` @ `874613a67018c74ee95f857416fb315d2f80b92b` (v0.1.0)
- `atlas-cartograph` → `sergio-sisternes-epam/atlas-cartograph` @ `9dcb9347f0c66d20a9607d2adc0474b69dd004f6` (v0.4.2)
- `autogenesis` → `sergio-sisternes-epam/autogenesis` @ `9b8763a362d69faf3eeb99612cd307078c19a881` (v0.7.0)

Never modify those upstream repositories from this marketplace.

Atlas v0.12.0 resolves `okf` through this marketplace (`okf@atlas`). It ships
runtime **help** and **getting-started** modules. Visualise remains unimplemented.
Discuss v0.4.0 resolves `atlas` through this marketplace (`atlas@atlas`). It ships runtime **help** and **getting-started** modules.
Atlas-cartograph v0.4.2 resolves `atlas` through this marketplace (`atlas@atlas`). It ships Apache-2.0 LICENSE on the pinned tree.
Autogenesis v0.7.0 resolves Atlas, OKF, Discuss, and Think through this marketplace (`pkg@atlas`). Durable discussion is catalog `discuss@atlas`. Think support nest-loads catalog `think@atlas`.

## Published marketplace name

Catalog `name` is `atlas`. Consumers must register with:

```bash
apm marketplace add sergio-sisternes-epam/atlas-marketplace --name atlas
apm install atlas@atlas
```

Canonical first consumer install is `atlas@atlas`. Package deps and installs use `pkg@atlas`. Do not use the GitHub-repo default
`atlas-marketplace` or a previous local alias such as `sergio-sisternes-epam`,
`apm-marketplace`, or `me`.

`apm marketplace audit` bypass warnings come from upstream git-shorthand
`dependencies.apm`. Fix those in the package repositories (child sessions),
then re-pin here. Do not edit those repos from this marketplace worktree.

## Catalog change procedure

1. Change only `marketplace.packages[]` in `apm.yml` (name, source, version, immutable `ref`, description). Keep `version` aligned with the package manifest at the pinned release commit.
2. Run `apm pack` with apm-cli 0.30.0 (same pin as CI). `apm marketplace check` is optional: it currently fails for raw commit-SHA pins even when pack and CI succeed.
3. Commit the matching `.claude-plugin/marketplace.json`.
4. Keep `AGENTS.md`, `CHANGELOG.md`, `CONTRIBUTING.md`, and `README.md` aligned.
5. Open a pull request; publish is merge to `main` after review and CI.

## Default-branch governance

The active `Protect default branch` ruleset targets the default branch (`main`).
It requires PRs, up-to-date `validate-and-pack` from GitHub Actions, and resolved
review conversations; force pushes, deletion, and bypasses are not allowed.
Copilot review is requested on non-draft PRs and new pushes. The owner approved
zero required approvals for this single-maintainer repository. Do not treat an
automatic review request as completed review or as authority to merge.
