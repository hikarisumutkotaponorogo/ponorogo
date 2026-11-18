# V15 — Production readiness and verified content defaults

This package remains a **Laravel 12 source overlay**, not a complete Laravel installation.

## Changes
- Cleared unverified address and legal-document text from seed defaults. Add verified details through admin settings before publication.
- Added `tools/production_readiness.php` to report missing framework, vendor, environment, PHP extensions, permissions, APP_KEY, and debug settings. A passing result does not replace application testing.
- Added `V15SeedSafetyTest` to assert empty official WhatsApp, legal, and address defaults.
- Retained V1–V14 features and tests.

## Install and test on a PHP/Composer-equipped development machine
```bash
bash tools/integrate_laravel12.sh /absolute/path/to/new/hikari-app
cd /absolute/path/to/new/hikari-app
php artisan test
php /path/to/V15-overlay/tools/production_readiness.php "$PWD"
```
The installer creates a new Laravel project and uses **SQLite for local testing only**. It must not be used as a production deployment script. Configure MySQL, SSL, backups, document root, mail, and verified official content before publishing.

## Test status
Static PHP lint and existing Python route/controller/migration audits were run in this environment. Full Laravel feature tests were **not** run: Composer and required PHP extensions are unavailable here. Never interpret prepared tests as passing tests.
