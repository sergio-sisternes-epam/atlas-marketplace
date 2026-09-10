# atlas-marketplace

Private Atlas APM marketplace **registry only**.

## Packages

| Package | Source | Release | Pin |
|---------|--------|---------|-----|
| `okf` | `sergio-sisternes-epam/okf` | v0.2.1 | SHA `5246f7b193b58a32ac8a15fc76aedf37c42b042c` |
| `atlas` | `sergio-sisternes-epam/atlas` | v0.11.2 | SHA `579e8090273ce991ea0717abed0775dc03f28de2` |
| `discuss` | `sergio-sisternes-epam/discuss` | v0.3.10 | SHA `c1c0936d9a0346dce7d877646046c918de335d69` |
| `think` | `sergio-sisternes-epam/think` | v0.1.0 | SHA `874613a67018c74ee95f857416fb315d2f80b92b` |
| `atlas-cartograph` | `sergio-sisternes-epam/atlas-cartograph` | v0.4.0 | SHA `0e391ffb530252874b5ed163a17228a471789a12` |
| `autogenesis` | `sergio-sisternes-epam/autogenesis` | v0.4.3 | SHA `b6d8556e183c78cc0293feaa096e0db3b0cbdc01` |

## Consumer (private)

Atlas v0.11.2 resolves `okf` through this marketplace (`okf@atlas`). Discuss
v0.3.10 resolves `atlas` through this marketplace (`atlas@atlas`). Autogenesis
v0.4.3 resolves Atlas, OKF, Discuss, and Think as `pkg@atlas`. Runtime
help, getting-started, and visualise paths remain unimplemented.

```bash
apm marketplace add sergio-sisternes-epam/atlas-marketplace --name atlas
apm install okf@atlas
apm install atlas@atlas
apm install discuss@atlas
apm install think@atlas
apm install atlas-cartograph@atlas
apm install autogenesis@atlas
```

`apm marketplace add` defaults the local name to the GitHub repo (`atlas-marketplace`).
Pass `--name atlas` so installs and package deps resolve as `pkg@atlas`. Re-add
if you previously registered this catalog as `sergio-sisternes-epam`,
`apm-marketplace`, or `me`.

Requires GitHub auth for private repos. Optional `-t` selects a consumer target
when the project does not already declare one.

Existing consumers need access to both this private marketplace and the private
package repository. After a catalog PR merges, explicitly refresh the index and
update the dependency from the consuming project:

```bash
apm marketplace update atlas
apm update atlas@atlas
apm update atlas-cartograph@atlas
```

Catalog publication does not automatically update installed extensions or
user-scope dependencies.

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
