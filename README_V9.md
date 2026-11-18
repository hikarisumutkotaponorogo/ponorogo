# V9 — Installer, environment checks and deployment preparation

This package remains a **Laravel 12 source overlay**, not a complete Laravel installation. It includes cumulative V1–V9 source files.

## Changes
- Improved `tools/integrate_laravel12.sh`: validates PHP/Composer, creates a fresh Laravel 12 app, registers authorization provider, creates isolated SQLite DB, runs migrations and seed, lists routes and runs tests.
- Added `tools/preflight_v9.sh` to inspect PHP extensions and Composer availability.
- Preserves existing project files and does not overwrite a pre-existing destination.

## Run on a computer with PHP 8.3+, Composer 2 and internet

```bash
bash tools/preflight_v9.sh
bash tools/integrate_laravel12.sh /absolute/path/to/hikari-laravel-app
```

**Caution:** The integration script runs migrations on a fresh local SQLite test database, not the final MySQL database. It does not configure a production `.env`, SSL, queues, file permissions, backups or live payment/WhatsApp services. Never use a public-facing deployment without completing security review and real end-to-end tests.

## Current verification limits
The source was syntax checked with PHP CLI. The current build environment has no Composer, so Laravel framework integration and tests have **not** been executed. The V9 script itself is validated with `bash -n`.

## Privacy
Do not publish original passport/COE images or other personal identifiers without redaction and permission.
