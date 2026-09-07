# Contributing to apm-marketplace

This repository is a private **registry only**. Do not vendor package source
trees here. Upstream packages stay in their own repositories.

## Pin / registry change

1. Point `marketplace.packages[].ref` at an immutable commit SHA (preferred) or
   a repository-supported release tag. Record the matching package name,
   source (`owner/repo`), and `version` when the release version is known.
   Verify the published release tag resolves to the pinned commit and its
   package manifest declares the same version before updating the catalog.
2. Do not edit `.claude-plugin/marketplace.json` by hand.
3. Use apm-cli 0.30.0 (same pin as CI) and run `apm pack`. `apm marketplace check` is optional: it currently fails for raw commit-SHA pins even when pack and CI succeed.

4. Commit `apm.yml` together with the generated `.claude-plugin/marketplace.json`.
5. Review `AGENTS.md`, `CHANGELOG.md` (`Unreleased`), `CONTRIBUTING.md`, and
   `README.md` in the same change.
6. Open a pull request against `main`. Wait for `validate-and-pack`. Human
   review and merge publishes the catalog.

Use `.github/pull_request_template.md` as the PR checklist.

## Boundaries

- Do not push pins directly to `main`.
- Do not modify upstream package repositories from this marketplace.
- Do not create tags, releases, or source-package publications from this repo.
