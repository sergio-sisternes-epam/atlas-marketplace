# Contributing to atlas-marketplace

This repository is a private **registry only**. Do not vendor package source
trees here. Upstream packages stay in their own repositories.

## Pin / registry change

1. Point `marketplace.packages[].ref` at an immutable commit SHA (preferred) or
   a repository-supported release tag. Record the matching package name,
   source (`owner/repo`), and `version` when the release version is known.
   Verify the published release tag resolves to the pinned commit and its
   package manifest declares the same version before updating the catalog.
   Include the source release URL and resolved commit SHA in the pull request
   so reviewers can verify the pin's provenance.
   Keep release-scope qualifications in catalog documentation: knowledge/design
   releases must not be described as implemented runtime features.
   The release handoff must also state that existing consumers explicitly
   refresh the marketplace index and update their dependency with access to
   both private repositories; publication does not update installed extensions.
2. Do not edit `.claude-plugin/marketplace.json` by hand.
3. Use apm-cli 0.30.0 (same pin as CI) and run `apm pack`. `apm marketplace check` is optional: it currently fails for raw commit-SHA pins even when pack and CI succeed.

4. Commit `apm.yml` together with the generated `.claude-plugin/marketplace.json`.
5. Review `AGENTS.md`, `CHANGELOG.md` (`Unreleased`), `CONTRIBUTING.md`, and
   `README.md` in the same change.
6. Open a pull request against `main`. Wait for `validate-and-pack`. Human
   review and merge publishes the catalog.

The active default-branch ruleset requires the branch to be up to date and
`validate-and-pack` to pass from GitHub Actions. Resolve all review conversations
before merging. Copilot review is automatically requested for non-draft PRs and
new pushes; wait for and assess its feedback before the owner merges. Automatic
requests do not enforce review completion. Under the owner's single-maintainer
policy, zero approving reviews are required. Force pushes, deletion, and bypasses
are blocked. See `docs/branch-protection.md`.

Use `.github/pull_request_template.md` as the PR checklist.

## Published marketplace name

Catalog `name` is `atlas`. Document consumer registration as:

```bash
apm marketplace add sergio-sisternes-epam/atlas-marketplace --name atlas
apm install <pkg>@atlas
```

`--name atlas` is required because `apm marketplace add` defaults to the GitHub
repo name (`atlas-marketplace`).

`apm marketplace audit <name>` warns when a catalogued package's
`dependencies.apm` uses git shorthand instead of `pkg@atlas`.
Those fixes belong in the package repositories. After they release, re-pin
here. Do not edit upstream trees from this marketplace.

## Boundaries

- Do not push pins directly to `main`.
- Do not modify upstream package repositories from this marketplace.
- Do not create tags, releases, or source-package publications from this repo.
