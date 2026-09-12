# atlas-marketplace

Public Atlas APM marketplace **registry only**. It indexes external packages and their dependencies; it does not vendor their source.

## Why

This is the public registry for the Atlas family. It is **not** a skill, and
it is **not** the source tree for the packages it lists. 

## Catalog

| Package | Source | Release | Pin |
| --- | --- | --- | --- |
| `okf` | `sergio-sisternes-epam/okf` | v0.2.1 | SHA `5246f7b193b58a32ac8a15fc76aedf37c42b042c` |
| `atlas` | `sergio-sisternes-epam/atlas` | v0.11.2 | SHA `579e8090273ce991ea0717abed0775dc03f28de2` |
| `discuss` | `sergio-sisternes-epam/discuss` | v0.3.10 | SHA `c1c0936d9a0346dce7d877646046c918de335d69` |
| `think` | `sergio-sisternes-epam/think` | v0.1.0 | SHA `874613a67018c74ee95f857416fb315d2f80b92b` |
| `atlas-cartograph` | `sergio-sisternes-epam/atlas-cartograph` | v0.4.1 | SHA `961297c0b88a65473e8922fe14aee937d481c059` |
| `autogenesis` | `sergio-sisternes-epam/autogenesis` | v0.7.0 | SHA `9b8763a362d69faf3eeb99612cd307078c19a881` |

## Install

Add the catalog once, then install packages from it:

```bash
apm marketplace add sergio-sisternes-epam/atlas-marketplace --name atlas
apm install okf@atlas
```

`--name atlas` is required so installs and package deps resolve as `pkg@atlas`.
Without it, `apm marketplace add` defaults the local name to the GitHub repo
(`atlas-marketplace`). Re-add if you previously registered this catalog as
`sergio-sisternes-epam`, `apm-marketplace`, or `me`. 

Other packages: `atlas@atlas`, `discuss@atlas`, `think@atlas`,
`atlas-cartograph@atlas`, `autogenesis@atlas`.

## Use

Add the catalog, then install one package:

```bash
apm marketplace add sergio-sisternes-epam/atlas-marketplace --name atlas
apm install okf@atlas
```

## Related

This repository is **registry only**. Package source, issues, and releases live
in the repositories listed in the catalog table. Do not vendor those trees here.

## Contributing

Pin changes only via pull request to `main`. See [CONTRIBUTING.md](CONTRIBUTING.md)
for the pin-update procedure.

## License

Copyright 2026 Sergio Sisternes.

Licensed under the [Apache License 2.0](LICENSE).
