# LPK Hikari Sumut — cPanel/hPanel deployment runbook (V19)

**Status:** This archive is a source overlay, not an installable Laravel application. First run `tools/integrate_laravel12.sh` in a PHP 8.3+/Composer 2 environment with internet access, and resolve all failed runtime tests. Do not deploy this overlay as-is.

## Server acceptance checklist

- PHP version compatible with installed Laravel 12, PHP CLI and extensions: PDO, mbstring, openssl, XML, tokenizer, fileinfo; MySQL driver for production.
- Composer 2, SSH, cron, HTTPS certificate, backups, sufficient memory and disk.
- Domain document root points to Laravel `public/`, not the application root; `.env`, `storage`, `vendor` are outside the public web root.
- Database user has only the permissions needed; no root credentials.

## Safe sequence

1. Create **private** repository, separate staging and production `.env`; never commit credentials.
2. Integrate the overlay into a clean Laravel 12 project and run `php artisan migrate` and `php artisan test` against a disposable staging database.
3. Confirm no personal document images or identifiers are accidentally published; get explicit media publication approval.
4. Build frontend assets, run tests, and prepare an immutable release.
5. Provision MySQL and SSL; set `APP_ENV=production`, `APP_DEBUG=false`, `APP_URL=https://...`, `APP_KEY` via `php artisan key:generate` only once for the environment. Never regenerate an existing production key.
6. Point the domain document root to `public/`; set storage and bootstrap/cache writable by the PHP process.
7. Back up the production database and media **off-server**, verify backup integrity and rollback plan.
8. Run `php tools/production_readiness.php /path/to/full-app` and `python3 tools/security_preflight_v19.py /path/to/full-app`.
9. Run `bash tools/deploy_v19.sh /path/to/full-app` for a dry run. Only after approval and backup, run `CONFIRM_DEPLOY=YES BACKUP_CONFIRMED=YES bash tools/deploy_v19.sh /path/to/full-app`.
10. Configure cron `* * * * * cd /path/to/full-app && php artisan schedule:run >> /dev/null 2>&1`; test SMTP, forms, login, authorization, CMS, media, backups and consent tracking.
11. Inspect server logs and test mobile/desktop. Do not launch until runtime tests and security checks pass.

## Rollback

If release fails, restore the previous release, reverse compatible migrations only with an approved migration plan, and restore the verified database backup when needed. Do not blindly run `migrate:rollback` against production data.

## Outstanding blockers

Composer and Laravel runtime integration have not been executed in this build environment; no production-ready claim. Official WhatsApp number, legal documents, verified program prices, analytics IDs, domain and hosting details are pending.
