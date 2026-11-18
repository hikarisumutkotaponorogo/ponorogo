# V20 — Release Candidate, NOT production ready

This ZIP is the cumulative V1–V20 **Laravel source overlay** with offline QA and a reproducible Laravel 12 integration script. It is not a complete installed Laravel application; `vendor/`, Laravel framework, `.env`, and an active database are deliberately absent.

## Verified in this build
- Run `python3 tools/v20_quality_gate.py` to check PHP/Bash syntax, required files, basic routes, and accidental secret packaging.
- Static route/controller/migration audits are also available in `tools/`.

## REQUIRED to reach production readiness
1. On a development computer or CI runner with PHP 8.3+, Composer 2, required PHP extensions, SQLite and Python 3, run: `bash tools/integrate_laravel12.sh /absolute/path/to/new-hikari-test-app` (destination MUST NOT already exist). This downloads Laravel 12, copies overlay, runs migrations, seeding, route listing and PHPUnit tests. **Never run this against production data.**
2. Fix every runtime exception and failing test. Manually test admin authentication, authorization, lead capture, program and content CMS, media publishing, registration, and tracking consent.
3. Review public photos/videos for consent and private documents; do not publish passport/COE identifiers. Validate program costs, legal data, location, and official WhatsApp number.
4. Perform real browser checks at 360px/768px/desktop, including conversion events and forms. Confirm privacy notice and consent configuration.
5. Only then configure production MySQL, SSL, secure backups, APP_DEBUG=false, APP_ENV=production, cron, SMTP, storage, and domain document root pointing at `public/`.

## Known limitations
- Composer is unavailable in the current build environment; **Laravel runtime tests have not been executed**.
- The preview HTML is a visual reference, not proof of working CRM functionality.
- This is a release candidate pending end-to-end verification; do not upload directly as a finished live website.
