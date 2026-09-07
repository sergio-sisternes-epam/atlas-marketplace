# Agent notes for apm-marketplace

This repository is a **registry-only** private APM marketplace. It indexes
external packages; it does not vendor skill source trees.

## Source versus generated

| Path | Role |
|------|------|
| `apm.yml` | Authoritative marketplace catalog (`marketplace.packages`) |
| `.claude-plugin/marketplace.json` | Generated consumer catalog; do not edit by hand |
| `.github/workflows/marketplace-ci.yml` | CI adapter: layout validate → `apm pack` (apm-cli 0.30.0) → drift check |
| `README.md` | Consumer usage and pin table |
| `CONTRIBUTING.md` | Pin-update and PR procedure |
| `CHANGELOG.md` | User-visible catalog history (`Unreleased` first) |

Do not add `SKILL.md` or `.apm/skills/` at the marketplace root.

## Current catalog pins

Pins are immutable commit SHAs for the latest verified stable GitHub release of
each external package:

- `okf` → `sergio-sisternes-epam/okf` @ `5246f7b193b58a32ac8a15fc76aedf37c42b042c` (v0.2.1)
- `atlas` → `sergio-sisternes-epam/atlas` @ `2b6659e5440886c7abbd9ad10686fa3a0100813b` (v0.9.0)
- `discuss` → `sergio-sisternes-epam/discuss` @ `d77c9f9c4c952d327811bfec9cfa764a6c56d1d6` (v0.3.8)
- `think` → `sergio-sisternes-epam/think` @ `874613a67018c74ee95f857416fb315d2f80b92b` (v0.1.0)
- `atlas-cartograph` → `sergio-sisternes-epam/atlas-cartograph` @ `2372272dc5c282f1b1a472483a412ef394971764` (v0.1.0)
- `autogenesis` → `sergio-sisternes-epam/autogenesis` @ `990d4f1a3e761bafb0385c91a0afbde38b3bd9ea` (v0.4.1)

Never modify those upstream repositories from this marketplace.

## Catalog change procedure

1. Change only `marketplace.packages[]` in `apm.yml` (name, source, immutable `ref`, description).
2. Run `apm pack` with apm-cli 0.30.0 (same pin as CI). `apm marketplace check` is optional: it currently fails for raw commit-SHA pins even when pack and CI succeed.
3. Commit the matching `.claude-plugin/marketplace.json`.
4. Keep `AGENTS.md`, `CHANGELOG.md`, `CONTRIBUTING.md`, and `README.md` aligned.
5. Open a pull request; publish is merge to `main` after review and CI.
