# Changelog

All notable changes to PieSocket Server are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

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
