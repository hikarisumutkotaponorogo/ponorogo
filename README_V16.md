# V16 — Reproducible Laravel integration setup

This is **still a Laravel 12 source overlay**, not a framework installation or a deployable production package.

## Added
- Composer 2 validation and non-interactive dependency installation in `tools/integrate_laravel12.sh`.
- Three Laravel HTTP smoke tests in `tests/Feature/V16SmokeTest.php` (homepage, ad landing page, admin login protection).
- GitHub Actions workflow `.github/workflows/laravel-integration.yml` to install Laravel and run the tests on an Ubuntu runner with PHP 8.3 and SQLite.
- Static audit runner `tools/verify_v16.sh`.

## To run locally
1. Install PHP 8.3+, extensions required by Laravel, Composer 2, Python 3, and SQLite PHP extension.
2. Extract this ZIP, then run `bash tools/verify_v16.sh`.
3. Run `bash tools/integrate_laravel12.sh /absolute/path/to/NEW/hikari-app` (target must not exist).
4. Inspect test failures and fix them before deployment. The installer is **local/test only**, not a production installer.

## Important
- CI workflow is prepared but **not executed** here; it runs only when pushed to a GitHub repository with Actions enabled.
- Database, login, forms, and web pages are **not yet verified in a live Laravel runtime**.
- Keep sensitive documents out of public directories; configure real verified WhatsApp, legal details, consent, SSL, MySQL and backups before launch.
