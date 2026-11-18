# V19 — Security & Deployment Preparation

This version retains all V18 source and adds:
- `tools/deploy_v19.sh`: fail-closed preflight, dry-run default, backup confirmation before deployment, maintenance-mode cleanup trap.
- `tools/security_preflight_v19.py`: source/public-directory checks.
- `DEPLOYMENT_CPANEL_V19.md`: step-by-step hosting and rollback runbook.

**Limitations:** Source overlay only. Laravel framework installation, database migrations and automated feature tests have NOT been executed. No claim of production readiness. V20 must prioritize a successful end-to-end runtime verification.
