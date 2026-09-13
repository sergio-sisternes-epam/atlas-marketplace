# atlas-marketplace

Public Atlas APM marketplace **registry only**. It indexes external packages and their dependencies; it does not vendor their source.

## Why

This is the public registry for the Atlas family. It is **not** a skill, and
it is **not** the source tree for the packages it lists. 

## Catalog

| Package | Source | Release | Pin |
| --- | --- | --- | --- |
| [`okf`](https://github.com/sergio-sisternes-epam/okf) | [sergio-sisternes-epam/okf](https://github.com/sergio-sisternes-epam/okf) | v0.2.1 | SHA `5246f7b193b58a32ac8a15fc76aedf37c42b042c` |
| [`atlas`](https://github.com/sergio-sisternes-epam/atlas) | [sergio-sisternes-epam/atlas](https://github.com/sergio-sisternes-epam/atlas) | v0.12.0 | SHA `40e11c65e243236850c26fc6cd5a04acdd483eb4` |
| [`discuss`](https://github.com/sergio-sisternes-epam/discuss) | [sergio-sisternes-epam/discuss](https://github.com/sergio-sisternes-epam/discuss) | v0.4.0 | SHA `af2d2fa4759c00d4ae77115c0fe710c439f8c958` |
| [`think`](https://github.com/sergio-sisternes-epam/think) | [sergio-sisternes-epam/think](https://github.com/sergio-sisternes-epam/think) | v0.1.0 | SHA `874613a67018c74ee95f857416fb315d2f80b92b` |
| [`atlas-cartograph`](https://github.com/sergio-sisternes-epam/atlas-cartograph) | [sergio-sisternes-epam/atlas-cartograph](https://github.com/sergio-sisternes-epam/atlas-cartograph) | v0.4.2 | SHA `9dcb9347f0c66d20a9607d2adc0474b69dd004f6` |
| [`autogenesis`](https://github.com/sergio-sisternes-epam/autogenesis) | [sergio-sisternes-epam/autogenesis](https://github.com/sergio-sisternes-epam/autogenesis) | v0.7.0 | SHA `9b8763a362d69faf3eeb99612cd307078c19a881` |

## Install

Add the catalog once, then install packages from it:

```bash
apm marketplace add sergio-sisternes-epam/atlas-marketplace --name atlas
apm install atlas@atlas
```

`--name atlas` is required so installs and package deps resolve as `pkg@atlas`.
Without it, `apm marketplace add` defaults the local name to the GitHub repo
(`atlas-marketplace`). Re-add if you previously registered this catalog as
`sergio-sisternes-epam`, `apm-marketplace`, or `me`. 

Other packages: `okf@atlas`, `discuss@atlas`, `think@atlas`,
`atlas-cartograph@atlas`, `autogenesis@atlas`.

## Use

Add the catalog, then install one package:

```bash
apm marketplace add sergio-sisternes-epam/atlas-marketplace --name atlas
apm install atlas@atlas
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
