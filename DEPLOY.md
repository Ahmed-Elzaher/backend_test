# Railway Deployment Guide

This repository deploys on [Railway](https://railway.app) using Railway's automatic Laravel/PHP Railpack/Nixpacks detection. No custom Dockerfile or Apache configuration is required.

---

## 1. Railway Environment Variables

In your Railway service dashboard, navigate to **Variables** and configure the following:

| Variable | Value | Description |
|---|---|---|
| `APP_NAME` | `SkillMatch` | Your application name |
| `APP_ENV` | `production` | Application environment |
| `APP_DEBUG` | `false` | Disable debug mode in production |
| `APP_KEY` | `base64:...` | Generate locally via `php artisan key:generate --show` |
| `APP_URL` | `https://your-service.up.railway.app` | Your generated Railway public domain |
| `LOG_CHANNEL` | `stderr` | Outputs logs to Railway deployment logs |
| `DB_CONNECTION` | `mysql` | MySQL database driver |
| `DB_HOST` | `${{MySQL.MYSQLHOST}}` | Railway internal MySQL host reference |
| `DB_PORT` | `${{MySQL.MYSQLPORT}}` | Railway internal MySQL port reference |
| `DB_DATABASE` | `${{MySQL.MYSQLDATABASE}}` | Railway MySQL database name reference |
| `DB_USERNAME` | `${{MySQL.MYSQLUSER}}` | Railway MySQL username reference |
| `DB_PASSWORD` | `${{MySQL.MYSQLPASSWORD}}` | Railway MySQL password reference |

> **Note:** If your Railway MySQL service is named differently (e.g. `mysql`), update the prefix in `${{MySQL....}}` to match your service name (e.g. `${{mysql.MYSQLHOST}}`).

---

## 2. Service Settings in Railway Dashboard

In your Laravel service under **Settings**:

1. **Deploy Settings**:
   - **Pre-deploy Command**: Set to `php artisan migrate --force`
   - **Custom Start Command**: **Empty / None** (Railway Nixpacks automatically detects Laravel and serves it)
2. **Networking**:
   - Click **Generate Domain** (under *Public Networking*) to obtain your `https://....up.railway.app` URL.
   - Copy this URL into the `APP_URL` variable above.

---

## 3. Troubleshooting

- **500 Server Error**:
  - Check Railway **Deploy Logs**.
  - Ensure `APP_KEY` is set and valid (run `php artisan key:generate --show` locally and paste the full string into `APP_KEY`).
  - Ensure `LOG_CHANNEL=stderr` is set so the exact exception details print in the Railway log console.

- **Database Connection Refused / Access Denied**:
  - Verify that the database service named `MySQL` is running in the same Railway project.
  - Verify variable references match: `${{MySQL.MYSQLHOST}}`, `${{MySQL.MYSQLPORT}}`, `${{MySQL.MYSQLDATABASE}}`, `${{MySQL.MYSQLUSER}}`, `${{MySQL.MYSQLPASSWORD}}`.

- **Mixed Content / HTTP instead of HTTPS**:
  - Proxies are already trusted via `$middleware->trustProxies(at: '*')` in `bootstrap/app.php`.
  - Ensure `APP_URL` uses `https://`.
