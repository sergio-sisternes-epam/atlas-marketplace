# Changelog

All notable changes to this marketplace catalog are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## Unreleased

### Added

- Catalog entries for Atlas-ecosystem packages pinned to latest stable release commits:
  - `atlas` v0.9.0 (`2b6659e5440886c7abbd9ad10686fa3a0100813b`)
  - `discuss` v0.3.8 (`d77c9f9c4c952d327811bfec9cfa764a6c56d1d6`)
  - `think` v0.1.0 (`874613a67018c74ee95f857416fb315d2f80b92b`)
  - `atlas-cartograph` v0.1.1 (`3f9fe350cb745b2b122a5d1d667f98ac5783f1b8`)
  - `autogenesis` v0.4.1 (`990d4f1a3e761bafb0385c91a0afbde38b3bd9ea`)

### Changed

- `atlas` pin from v0.9.0 to v0.9.1 (`a1074e5dfd8cc8236132e7615063628407e35b6a`), which resolves `okf` through this marketplace instead of a git SHA.
- Catalog identity from `apm-marketplace` to `sergio-sisternes-epam`. Consumers must register with `apm marketplace add sergio-sisternes-epam/apm-marketplace --name sergio-sisternes-epam` and install as `pkg@sergio-sisternes-epam`.
- `atlas-cartograph` pin from v0.1.0 to v0.1.1 (`3f9fe350cb745b2b122a5d1d667f98ac5783f1b8`).
- `okf` pin from `d734f78c384e767e52ab81bf4c02ca5940d56363` to v0.2.1 (`5246f7b193b58a32ac8a15fc76aedf37c42b042c`).
- Marketplace CI adapter pin from `apm-cli==0.28.0` to `apm-cli==0.30.0` so pack and drift checks match local generation.
