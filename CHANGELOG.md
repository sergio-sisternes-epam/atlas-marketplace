# Changelog

All notable changes to this marketplace catalog are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## Unreleased

### Added

- GitHub issue and pull request templates for bugs, features, and contribution
  checks.
- Catalog entries for Atlas-ecosystem packages pinned to latest stable release commits:
  - `atlas` v0.9.0 (`2b6659e5440886c7abbd9ad10686fa3a0100813b`)
  - `discuss` v0.3.8 (`d77c9f9c4c952d327811bfec9cfa764a6c56d1d6`)
  - `think` v0.1.0 (`874613a67018c74ee95f857416fb315d2f80b92b`)
  - `atlas-cartograph` v0.1.1 (`3f9fe350cb745b2b122a5d1d667f98ac5783f1b8`)
  - `autogenesis` v0.4.1 (`990d4f1a3e761bafb0385c91a0afbde38b3bd9ea`)

### Changed

- Root `README.md` restructured to the catalog family outline (purpose, why,
  catalog table, install, use, related, contributing, license). Ruleset and CI
  internals stay in `CONTRIBUTING.md`.
- Consumer `README.md` Install documents only the public marketplace path
  (`apm marketplace add … --name atlas` then `apm install <pkg>@atlas`). Git-tag,
  clone, and post-install CLI setup are not consumer install methods.
- Consumer documentation now describes this catalog as a public registry-only marketplace. Register with `apm marketplace add sergio-sisternes-epam/atlas-marketplace --name atlas` and install as `pkg@atlas`. After a catalog merge, consumers must still run `apm marketplace update atlas` and update dependencies; publication does not update installed packages.
- `autogenesis` pin from v0.4.3 to v0.6.0 (`04e3a83c662fb61b22a9959979185049a25810ea`). v0.6.0 removes the parent-routed Discuss adapter; durable discussion is catalog `discuss@atlas`. Existing consumers must refresh the marketplace index and update the dependency; publication does not update installed extensions.
- Repository licensing changed from MIT to Apache-2.0.
- `atlas-cartograph` pin from v0.4.0 to v0.4.1 (`961297c0b88a65473e8922fe14aee937d481c059`), which resolves `atlas` through marketplace `atlas` (`atlas@atlas`).
- `autogenesis` pin from v0.4.2 to v0.4.3 (`b6d8556e183c78cc0293feaa096e0db3b0cbdc01`), which resolves Atlas, OKF, Discuss, and Think through marketplace `atlas` (`pkg@atlas`).
- `discuss` pin from v0.3.9 to v0.3.10 (`c1c0936d9a0346dce7d877646046c918de335d69`), which resolves `atlas` through marketplace `atlas` (`atlas@atlas`).
- `atlas` pin from v0.11.1 to v0.11.2 (`579e8090273ce991ea0717abed0775dc03f28de2`), which resolves `okf` through marketplace `atlas` (`okf@atlas`).
- Catalog identity from `sergio-sisternes-epam` to `atlas`. GitHub repository renamed to `sergio-sisternes-epam/atlas-marketplace`. Consumers must register with `apm marketplace add sergio-sisternes-epam/atlas-marketplace --name atlas` and install as `pkg@atlas`.
- `atlas` pin from v0.11.0 to v0.11.1 (`75b7d317d7619d14951d9e2ecc163d87b9c10f38`), which connects Atlas help knowledge and Cartograph onboarding design. This is a knowledge/design release only; runtime help, getting-started, and visualise paths remain unimplemented.
- `atlas-cartograph` pin from v0.3.0 to v0.4.0 (`0e391ffb530252874b5ed163a17228a471789a12`), which improves session chat, full-screen citation navigation, draft retention, and the Options and search layout.
- `atlas` pin from v0.10.0 to v0.11.0 (`1c5a4158d5ff091bc2de78d6303cddf7e9bb4418`), which adds shared vs dedicated store hosting (`atlas store init` / `store rehost`).
- Default-branch governance now uses an active ruleset requiring PRs, up-to-date `validate-and-pack` checks, and resolved review conversations, with no force pushes, deletion, or bypass actors. Copilot review is automatically requested for non-draft PRs and new pushes; the owner approved zero required approvals for the single-maintainer workflow.
- `atlas-cartograph` pin from v0.2.0 to v0.3.0 (`fe6de71e56422bda09dd0a92cf59d683d883e396`), which adds volumetric galaxies and an always-visible "Search stars" toolbar input with keyboard-accessible results.
- `atlas` pin from v0.9.1 to v0.10.0 (`3818586da56331949b03fe746ef21693d3c84169`), which adds opt-in SCHEMA 2.0 Semantic Memory Recall.
- `atlas` pin from v0.9.0 to v0.9.1 (`a1074e5dfd8cc8236132e7615063628407e35b6a`), which resolves `okf` through this marketplace instead of a git SHA.
- `discuss` pin from v0.3.8 to v0.3.9 (`95b51910378fa8245b67e70a42cbf1be840b620b`), which resolves `atlas` through this marketplace instead of git tag `v0.8.15`.
- `autogenesis` pin from v0.4.1 to v0.4.2 (`01000d02c4c3588a4afc75a967f7d6002d116c9b`), which resolves Atlas, OKF, Discuss, and Think through this marketplace instead of git shorthands.
- Catalog identity from `apm-marketplace` to `sergio-sisternes-epam`. Consumers must register with `apm marketplace add sergio-sisternes-epam/apm-marketplace --name sergio-sisternes-epam` and install as `pkg@sergio-sisternes-epam`.
- `atlas-cartograph` pin from v0.1.0 to v0.1.1 (`3f9fe350cb745b2b122a5d1d667f98ac5783f1b8`).
- `atlas-cartograph` pin from v0.1.1 to v0.2.0 (`584c6843fd04e0fe27c2ba67bb9be67158b37a4c`), which adds schema-aware Core/contribution type layers, consistent navigation-index labels, hookless native startup, and state-preserving reload.
- `okf` pin from `d734f78c384e767e52ab81bf4c02ca5940d56363` to v0.2.1 (`5246f7b193b58a32ac8a15fc76aedf37c42b042c`).
- Marketplace CI adapter pin from `apm-cli==0.28.0` to `apm-cli==0.30.0` so pack and drift checks match local generation.
