# Changelog

All notable changes to PieSocket Server are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## v5.0.2 - 2026-09-03

### Changed
- **v4 frames name their channel.** Every frame delivered on a `/v4/` connection
  now carries a `system::channel` field — the same key a client sets to address a
  secondary subscription — so a multiplexed client can route inbound messages to
  the right channel. The `system:binary` frame's `channel` field was renamed to
  `system::channel` to match.

## v5.0.0 - 2026-09-02

### Added
- **v4 protocol (`/v4/:channel`)** — a single WebSocket connection can subscribe
  to multiple channels with `system:subscribe` / `system:unsubscribe` control
  frames. The connect-time channel stays the default; other messages target it
  unless they carry a `system::channel` field.
- **Delta-based presence on v4** — `system:member_joined` / `system:member_left`
  carry only the member that changed instead of the whole roster; use
  `system:get_members` to (re)fetch the full list. The same identified user
  across several connections counts as one member.
- **Binary on v4 needs no opt-in** — any binary WebSocket frame is delivered as a
  `system:binary` event; `?binary=1` / `binary-` channels are no longer required.
- **v3 and v4 traffic is fully isolated.** Publish to v4 clients with the new
  `POST /api/v4/publish`, and read a v4 channel's presence roster with
  `POST /api/v4/members`. `POST /api/publish` and `POST /api/members` now target
  v3. Management endpoints (`/api/management/*`) are unchanged and apply to both.

## [4.7.7] - 2026-08-27

### Added
- Log partitioning to keep log tables bounded and improve query performance on high-volume clusters.

## [4.7.6] - 2026-08-06

### Fixed
- Miscellaneous fixes and internal improvements.

## [4.7.5] - 2026-08-06

### Fixed
- Fixed a crash under certain runtime conditions.

## [4.7.4] - 2026-07-26

### Changed
- Webhooks and API keys endpoints are now paginated.

## [4.7.3] - 2026-07-26

### Added
- Support for the `PIE_CLUSTER_ID` environment variable.

## [4.7.2] - 2026-07-25

### Added
- Health check API endpoint.

## [4.7.1] - 2026-07-24

### Fixed
- Internal fixes.

## [4.7.0] - 2026-07-24

### Added
- Improved webhook logging.

### Fixed
- DNS resolution issues in clustered deployments.
- Various webhook delivery bugs.

## [4.5.9] - 2026-07-22

### Fixed
- Multiple stability and webhook-related bug fixes.

## [4.5.0] - 2026-07-21

### Fixed
- Bug fixes and general improvements.

## [4.4.8] - 2026-07-21

### Added
- Prometheus-style metrics endpoint.
- `app.max_messages_per_day` support.
- Cluster host label on metrics.
- `PIE_CLUSTER` environment variable support.
- User ID support.

### Fixed
- Message counting accuracy.
- Metrics scraper fixes.
- Database migration runner fixes.
