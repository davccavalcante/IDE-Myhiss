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

### Post-release fixes

Per [Keep a Changelog 1.1.0](https://keepachangelog.com/en/1.1.0/), post-release
fixes for this version are listed below; the package version stays at
`1.0.0-alpha`. Each entry is timestamped in UTC ISO 8601.

- **2026-05-21T22:49:19Z** — Fix `.github/workflows/release.yml`: pass `GITHUB_TOKEN` to the `npm install` step. The `@vscode/ripgrep` postinstall script queries `api.github.com/repos/microsoft/ripgrep-prebuilt/releases/tags/v15.0.1` unauthenticated, hitting the public rate limit on shared CI runners (HTTP 403).
- **2026-05-21T22:49:19Z** — Remove 15 upstream-only workflows from `.github/workflows/` (`api-proposal-version-check.yml`, `chat-lib-package.yml`, `chat-perf.yml`, `component-fixtures.yml`, `copilot-setup-steps.yml`, `monaco-editor.yml`, `no-engineering-system-changes.yml`, `pr.yml`, `pr-darwin-test.yml`, `pr-linux-cli-test.yml`, `pr-linux-test.yml`, `pr-node-modules.yml`, `pr-win32-test.yml`, `sessions-e2e.yml`, `telemetry.yml`) and the helper `check-clean-git-state.sh`. These targeted Microsoft-internal CI infrastructure and consumed runner minutes without producing Myhiss artifacts.
- **2026-05-21T22:49:19Z** — Remove `.github/dependabot.yml`. The upstream configuration was opening weekly dependency-update pull requests against actions and devcontainer definitions that no longer apply to this fork.
- **2026-05-21T22:49:19Z** — Close auto-opened Dependabot pull requests (#1–#5) and delete their source branches.
- **2026-05-21T22:49:19Z** — Cancel queued workflow runs from the removed upstream workflows.
- **2026-05-21T22:49:19Z** — GitHub repository configuration: set homepage to `https://myhiss.im`; add topics `ide`, `code-editor`, `vscode-fork`, `electron`, `typescript`, `ai`, `llm`, `developer-tools`, `open-source`, `macos`, `apple-silicon`, `myhiss`, `idemyhiss`.
- **2026-05-21T22:49:19Z** — Enable branch protection on `main`: deny force-push, deny deletion, require linear history, require pull request before merge, and require the `detect-version` status check from the Release workflow.
