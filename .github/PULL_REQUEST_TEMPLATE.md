## Related issue

Fixes #

External substantive pull requests need a linked issue first. Maintainer-authored small docs or maintenance may skip that wait.

## Human scope approval

- [ ] A human approved this scope before agent implementation
- [ ] Maintainer-authored small docs or maintenance (scope approval not required)

## Agent-authored work

- [ ] The pull request author owns any agent-generated diffs
- [ ] This pull request was not opened by an unattended agent as the GitHub author

## Summary

<!-- What changed and why. -->

## Type of change

- [ ] Bug fix
- [ ] Feature / package change
- [ ] Breaking change
- [ ] Documentation
- [ ] Maintenance / refactor
- [ ] Marketplace pin / catalog change

## Shared checklist

- [ ] No secrets, tokens, or private paths are included
- [ ] Generated files were regenerated, not hand-edited
- [ ] Lockfiles and packed outputs match source when this repository produces them
- [ ] `CHANGELOG.md` is updated, or the change is N/A
- [ ] `CONTRIBUTING.md` local checks were run

## Repo extras

- [ ] `apm.yml` pin/version updated if this is a catalog change
- [ ] `apm pack` regenerated `.claude-plugin/marketplace.json` (no hand edits)
- [ ] Package repo tip matches the pin (SHA/tag)
- [ ] No skill source trees added to this registry repo
- [ ] Validate (layout + packages)
- [ ] Build (pack, no drift)
- [ ] Publish = merge after review under branch protection
