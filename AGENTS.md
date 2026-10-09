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

Pins are cloneable release tags (`v{version}`) for the latest verified stable
GitHub release of each external package. Do not set `ref` to a raw commit SHA:
Copilot and `git clone --branch` cannot fetch a SHA.

After `apm pack` (apm-cli 0.30.0), generated `sha` is the GitHub object for
that tag: an annotated tag object ID when the tag is annotated, or the commit
when the tag is lightweight. Do not hand-edit `.claude-plugin/marketplace.json`
to substitute `ref^{}` — the pack drift check regenerates it. Parenthetical
values below are peeled commits (`tag^{}`) for provenance.

- `okf` → `sergio-sisternes-epam/okf` @ `v0.2.1` (`5246f7b193b58a32ac8a15fc76aedf37c42b042c`)
- `atlas` → `sergio-sisternes-epam/atlas` @ `v0.13.1` (`b012e92ef10aaaee451e99253ea2968066521ec7`)
- `discuss` → `sergio-sisternes-epam/discuss` @ `v0.5.0` (`480fc5fc9f0b1c280cd2301dccbf76ff63ddbc4e`)
- `think` → `sergio-sisternes-epam/think` @ `v0.1.0` (`874613a67018c74ee95f857416fb315d2f80b92b`)
- `atlas-cartograph` → `sergio-sisternes-epam/atlas-cartograph` @ `v0.4.3` (`4470256eca4379af8715773a80d6664843b524a2`)
- `autogenesis` → `sergio-sisternes-epam/autogenesis` @ `v0.8.1` (`f901d0df2ac04a4641b78b1c7f2100185725a4b1`)
- `atlas-tasks` → `sergio-sisternes-epam/atlas-tasks` @ `v0.6.2` (`0803af1b078cac1482814c86b5ee16f082f9a080`)
- `atlas-people` → `sergio-sisternes-epam/atlas-people` @ `v0.1.2` (`605ee9a7c20d3c68af37cb410ca43be67475574c`)

Never modify those upstream repositories from this marketplace.

Atlas v0.13.1 resolves `okf` through this marketplace (`okf@atlas`). It ships
runtime **help** and **getting-started** modules, the four-layer memory model,
and `memory-migrate`. On SCHEMA 2.0 stores an overlay may carry one
package-metadata extension slot, and `schema upgrade --to 2.0` checks installed
overlays before applying. Visualise remains unimplemented. There is no dedicated
sleep or consolidate command.
Discuss v0.5.0 resolves `atlas` through this marketplace (`atlas@atlas`). It stores live discussion in the confirmed Atlas of the active project. `discuss-atlas` stays that package repository's own Atlas. It still ships runtime **help** and **getting-started** modules.
Atlas-cartograph v0.4.3 resolves `atlas` through this marketplace (`atlas@atlas`). It ships Apache-2.0 LICENSE on the pinned tree and idle rotation speed control.
Autogenesis v0.8.1 resolves Atlas, OKF, Discuss, and Think through this marketplace (`pkg@atlas`). Durable discussion is catalog `discuss@atlas` at Discuss `v0.5.0`. Think support nest-loads catalog `think@atlas`. It ships parent-routed **help** and **getting-started** operations. CI no longer requires `APM_READ_TOKEN` for public Atlas-family sources.
Atlas-tasks v0.6.2 requires an installed Atlas (Atlas 0.12.0 or later) and a target Atlas the user names; it does not declare `atlas@atlas` as an APM dependency. It mounts its overlay onto that Atlas with `atlas schema install <atlas-tasks-package>/contributions/atlas-tasks --root <atlas-root>` and then `atlas compile`. The overlay installs on SCHEMA 1.0 and SCHEMA 2.0 stores. Consumers upgrading from v0.6.1 re-run `atlas schema install` (no `--force`) on each Atlas holding the overlay; on SCHEMA 1.0 stores they do so before any `schema upgrade --to 2.0`.
Atlas-people v0.1.2 runs on an operator-supplied people Atlas (store id and push remote come from the install config; the package ships placeholders only) and writes only with `atlas_target: confirmed`. It composes with an installed `atlas` plus an Atlas compile/commit/push helper and, for the one-shot import, an Apple Notes reader skill; it declares no APM dependencies, and those two helpers are not in this catalog.

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

1. Change only `marketplace.packages[]` in `apm.yml` (name, source, version, cloneable release-tag `ref`, description). Keep `version` aligned with the package manifest at the pinned release. `ref` must be a tag `git clone --branch` can fetch (Atlas pattern `v{version}`). Verify the tag peels to the expected commit before changing. Immutability is the generated `sha` in `.claude-plugin/marketplace.json`.
2. Run `apm pack` with apm-cli 0.30.0 (same pin as CI). `apm marketplace check` is optional after pack.
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
