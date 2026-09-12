# atlas-marketplace

Public Atlas APM marketplace **registry only**. It indexes external packages;
it does not vendor package source.

## Packages

| Package | Source | Release | Pin |
|---------|--------|---------|-----|
| `okf` | `sergio-sisternes-epam/okf` | v0.2.1 | SHA `5246f7b193b58a32ac8a15fc76aedf37c42b042c` |
| `atlas` | `sergio-sisternes-epam/atlas` | v0.11.2 | SHA `579e8090273ce991ea0717abed0775dc03f28de2` |
| `discuss` | `sergio-sisternes-epam/discuss` | v0.3.10 | SHA `c1c0936d9a0346dce7d877646046c918de335d69` |
| `think` | `sergio-sisternes-epam/think` | v0.1.0 | SHA `874613a67018c74ee95f857416fb315d2f80b92b` |
| `atlas-cartograph` | `sergio-sisternes-epam/atlas-cartograph` | v0.4.1 | SHA `961297c0b88a65473e8922fe14aee937d481c059` |
| `autogenesis` | `sergio-sisternes-epam/autogenesis` | v0.6.0 | SHA `04e3a83c662fb61b22a9959979185049a25810ea` |

## Consumer

Atlas v0.11.2 resolves `okf` through this marketplace (`okf@atlas`). Discuss
v0.3.10 resolves `atlas` through this marketplace (`atlas@atlas`). Autogenesis
v0.6.0 resolves Atlas, OKF, Discuss, and Think as `pkg@atlas`. Durable
discussion is catalog `discuss@atlas`. Runtime help, getting-started, and
visualise paths remain unimplemented.

```bash
apm marketplace add sergio-sisternes-epam/atlas-marketplace --name atlas
apm install <pkg>@atlas
```

`--name atlas` is required. `apm marketplace add` defaults the local name to
the GitHub repo (`atlas-marketplace`). Pass `--name atlas` so installs and
package deps resolve as `pkg@atlas`. Re-add if you previously registered this
catalog as `sergio-sisternes-epam`, `apm-marketplace`, or `me`.

Optional `-t` selects a consumer target when the project does not already
declare one.

After a catalog PR merges, consumers must still refresh the index and update
dependencies from the consuming project. Catalog publication does not
automatically update installed extensions or user-scope dependencies:

```bash
apm marketplace update atlas
apm update <pkg>@atlas
```

## Governance

- **Pin changes only via pull request** to `main` (no direct pin push).
- The active **Protect default branch** ruleset requires PRs, up-to-date `validate-and-pack` checks from GitHub Actions, and resolved review conversations. It blocks force pushes and deletion, with no bypass actors.
- Copilot reviews are requested automatically for non-draft PRs and new pushes. No approving review is required under the owner's single-maintainer policy; automatic review requests are not a review-completion merge gate. See `docs/branch-protection.md`.
- CI (GitHub Actions adapter): validate registry layout → `apm pack` with `apm-cli==0.30.0` → fail on `marketplace.json` drift.
- Canonical model lives in the apm skill (`references/ci-cd-canonical.md`); this workflow is an **example adapter**, not the model.

## Authoring a pin update

1. Point `marketplace.packages[].ref` at the published release commit/tag and keep `version` aligned with the pinned package manifest.
2. Run `apm pack` with apm-cli 0.30.0 and commit `.claude-plugin/marketplace.json`. `apm marketplace check` is optional: it currently fails for raw commit-SHA pins even when pack and CI succeed.
3. Keep `AGENTS.md`, `CHANGELOG.md`, `CONTRIBUTING.md`, and `README.md` aligned.
4. Open PR; wait for CI; human review and merge.

See `CONTRIBUTING.md` for the full procedure.

## License

Copyright 2026 Sergio Sisternes.

Licensed under the [Apache License 2.0](LICENSE).
