# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog 1.1.0](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html).

All timestamps are UTC ISO 8601.

## [1.0.0-alpha] — 2026-05-21T21:53:19Z

This version represents the **upstream fork baseline only**. No Myhiss-specific
application features are present yet. The packaged macOS application still
launches with upstream `Code - OSS` branding; product rebranding will land in
a later release.

### Added

- Initial Myhiss fork baseline from [`microsoft/vscode`](https://github.com/microsoft/vscode) at commit `987c9597516278c9fcf10d963a0592ce1384ab93` (VSCode `1.121.0`).
- Project ownership and metadata: David C Cavalcante (`davcavalcante@proton.me`).
- Apache License 2.0 (`LICENSE`) for Myhiss-original code, with upstream MIT attribution preserved in `NOTICE` and `ThirdPartyNotices.txt`.
- GitHub Actions release workflow (`.github/workflows/release.yml`): on push to `main`, detects the version in `package.json`, creates the matching tag `v<version>` if missing, builds the macOS Apple Silicon application, packages it as a ZIP, and publishes a GitHub Release with the artifact attached.
