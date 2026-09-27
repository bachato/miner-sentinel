# Changelog

All notable changes to MinerSentinel are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.2.0] - 2026-09-27

Operator-focused release: in-app Activity and device Controls, two new solo pool collectors, retention and push channels, plus a dependency and container hardening pass.

### Added

- **Activity journal** — persist collector alerts in-app with filters, awareness fields, and an Activity page for fleet events without leaving the dashboard.
- **Device Controls** — MinerWatch-style remote actions (reboot, fan, Bitaxe frequency/voltage presets, Avalon workmode) with capability discovery per make.
- **LAN discovery** — find miners on the local network from Settings to speed up onboarding.
- **Advisor panel** — actionable hints on device views for common health and config issues.
- **Push notification channels** — ntfy, Gotify, and generic webhook support alongside Telegram and Discord.
- **Data retention** — configurable pruning via management command to keep time-series growth under control.
- **BTC PoW Lab pool collector** — hybrid solo public API stats and Settings fields.
- **Parasite Pool collector** — public stats from parasite.space (Bitcoin address) with Settings UI and tests.
- **Operator tutorial** — step-by-step guide at `docs/TUTORIAL.md`, plus refreshed dashboard screenshots.

### Changed

- Notifications settings UI expanded for multi-channel configuration and alert rules.
- Overview and Mining dashboards surface Activity and Controls entry points more clearly.
- Umbrel / compose Postgres image pin updated as part of the security refresh.

### Fixed

- Cleared known HIGH/CRITICAL advisories across app images by upgrading Django to **5.2 LTS**, refreshing frontend dependencies (React Router, Vitest, and related packages), and hardening Dockerfiles.
- Pinned Postgres image digests in compose files for reproducible, digest-locked deploys.
- Vite production builds with esbuild 0.28 by raising the build target to **es2022** (avoids unsupported destructuring downleveling).

### Security

- Library and container vulnerability remediation across backend, frontend, and data-service images (#31).

## [1.1.0] - 2026-08-10

Unified multi-make device registry and shared time-series schema.

### Added

- Canonical `devices` registry with make-aware identity for Bitaxe, Avalon, NMAxe, NerdNOS, and related firmwares.
- Shared mining, hardware, and system time-series tables replacing per-vendor silos.
- NMAxe and NerdNOS collectors alongside updated Bitaxe and Avalon adapters.
- Notification rules migration and upgrade verification tooling.

### Changed

- API and UI rewritten around the unified device model and analytics endpoints.
- README and Umbrel packaging updated for the multi-make fleet story.

### Removed

- Legacy per-make device and pool tables after data migration.

## [1.0.3] - 2026-06-01

### Changed

- Umbrel Docker image digests updated to v1.0.3.

[1.2.0]: https://github.com/dcbert/miner-sentinel/compare/1.1.0...1.2.0
[1.1.0]: https://github.com/dcbert/miner-sentinel/compare/1.0.3...1.1.0
[1.0.3]: https://github.com/dcbert/miner-sentinel/releases/tag/1.0.3
