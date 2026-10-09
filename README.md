# atlas-marketplace

Public Atlas APM marketplace **registry only**. It indexes external packages and their dependencies; it does not vendor their source.

## Why

This is the public registry for the Atlas family. It is **not** a skill, and
it is **not** the source tree for the packages it lists. 

## Catalog

| Package | Source | Release | Pin |
| --- | --- | --- | --- |
| [`okf`](https://github.com/sergio-sisternes-epam/okf) | [sergio-sisternes-epam/okf](https://github.com/sergio-sisternes-epam/okf) | v0.2.1 | tag `v0.2.1` (SHA `5246f7b193b58a32ac8a15fc76aedf37c42b042c`) |
| [`atlas`](https://github.com/sergio-sisternes-epam/atlas) | [sergio-sisternes-epam/atlas](https://github.com/sergio-sisternes-epam/atlas) | v0.13.1 | tag `v0.13.1` (SHA `b012e92ef10aaaee451e99253ea2968066521ec7`) |
| [`discuss`](https://github.com/sergio-sisternes-epam/discuss) | [sergio-sisternes-epam/discuss](https://github.com/sergio-sisternes-epam/discuss) | v0.5.0 | tag `v0.5.0` (SHA `480fc5fc9f0b1c280cd2301dccbf76ff63ddbc4e`) |
| [`think`](https://github.com/sergio-sisternes-epam/think) | [sergio-sisternes-epam/think](https://github.com/sergio-sisternes-epam/think) | v0.1.0 | tag `v0.1.0` (SHA `874613a67018c74ee95f857416fb315d2f80b92b`) |
| [`atlas-cartograph`](https://github.com/sergio-sisternes-epam/atlas-cartograph) | [sergio-sisternes-epam/atlas-cartograph](https://github.com/sergio-sisternes-epam/atlas-cartograph) | v0.4.3 | tag `v0.4.3` (SHA `4470256eca4379af8715773a80d6664843b524a2`) |
| [`autogenesis`](https://github.com/sergio-sisternes-epam/autogenesis) | [sergio-sisternes-epam/autogenesis](https://github.com/sergio-sisternes-epam/autogenesis) | v0.8.1 | tag `v0.8.1` (SHA `f901d0df2ac04a4641b78b1c7f2100185725a4b1`) |
| [`atlas-tasks`](https://github.com/sergio-sisternes-epam/atlas-tasks) | [sergio-sisternes-epam/atlas-tasks](https://github.com/sergio-sisternes-epam/atlas-tasks) | v0.6.2 | tag `v0.6.2` (SHA `0803af1b078cac1482814c86b5ee16f082f9a080`) |
| [`atlas-people`](https://github.com/sergio-sisternes-epam/atlas-people) | [sergio-sisternes-epam/atlas-people](https://github.com/sergio-sisternes-epam/atlas-people) | v0.1.2 | tag `v0.1.2` (SHA `605ee9a7c20d3c68af37cb410ca43be67475574c`) |

Pin column SHAs are peeled commits (`tag^{}`). After `apm pack`, generated
`sha` is the GitHub object for the tag (annotated tag object when the tag is
annotated).

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
`atlas-cartograph@atlas`, `autogenesis@atlas`, `atlas-tasks@atlas`,
`atlas-people@atlas`.

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
