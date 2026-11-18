# V17 — Role-based login guard and integration test expansion

## Changes
- Added seven Laravel feature tests for public pages, protected CRM and registration routes, editor/enrollment access, invalid login, unprivileged login and lead creation.
- Added an authorization guard after successful credential authentication: accounts without `dashboard.view` are signed out and receive a generic error instead of entering the admin dashboard.
- Added `tools/verify_v17.sh` for static audit and PHP syntax verification.

## Important verification status
- PHP syntax/static audit can be executed in this environment.
- Composer is not available here, so **Laravel HTTP tests, migrations and database execution are not verified**.
- This remains a Laravel 12 **source overlay**, not a complete framework installation. Use `tools/integrate_laravel12.sh` in a PHP 8.3+/Composer 2 environment to install and run tests. Fix any failures before production.
- The prior versions' templates, controllers and database migrations are preserved.
