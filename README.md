# SkillMatch Backend API

> Laravel 11 / 12 backend with JWT Authentication, Inertia/React starter, and OpenAPI documentation.

---

## 🚀 Features

- **Authentication**: JWT Auth (`tymon/jwt-auth`) via `auth:api` guard + Laravel Fortify.
- **API Documentation**: OpenAPI 3.1 & Swagger UI via `darkaonline/l5-swagger` at `/api/documentation`.
- **Localization**: Multi-language support (`en`, `ar`).
- **Database**: Eloquent ORM supporting MySQL, PostgreSQL, and SQLite.
- **Frontend / Admin UI**: Inertia.js with React & TypeScript.

---

## ⚙️ Environment Variables (.env)

Below is the complete list of environment variables. You can copy and paste this into your local `.env` or into your deployment platform (e.g. Render, Railway, Forge).

```env
APP_NAME=SkillMatch
APP_ENV=production
APP_KEY=base64:dvPSpwB89tSyd0VVDRMN8t9Z65BApBe3eDLun3KQGWM=
APP_DEBUG=false
APP_URL=http://localhost:8000

STATIC_OTP_ENABLED=false
STATIC_OTP_CODE=123456

APP_LOCALE=en
APP_FALLBACK_LOCALE=en
APP_FAKER_LOCALE=en_US

APP_MAINTENANCE_DRIVER=file
BCRYPT_ROUNDS=12

LOG_CHANNEL=stderr
LOG_STACK=single
LOG_DEPRECATIONS_CHANNEL=null
LOG_LEVEL=info

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=skillmatch
DB_USERNAME=root
DB_PASSWORD=

SESSION_DRIVER=database
SESSION_LIFETIME=120
SESSION_ENCRYPT=false
SESSION_PATH=/
SESSION_DOMAIN=null

BROADCAST_CONNECTION=log
FILESYSTEM_DISK=local
QUEUE_CONNECTION=database

CACHE_STORE=database
MEMCACHED_HOST=127.0.0.1

REDIS_CLIENT=phpredis
REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379

MAIL_MAILER=log
MAIL_SCHEME=null
MAIL_HOST=127.0.0.1
MAIL_PORT=2525
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_FROM_ADDRESS="hello@example.com"
MAIL_FROM_NAME="${APP_NAME}"

AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=
AWS_USE_PATH_STYLE_ENDPOINT=false

VITE_APP_NAME="${APP_NAME}"
JWT_SECRET=5IbJF1l9AeoPfjj9jf82TSllAQytc4YOYEj57sJDjn8KBcJNblHR06jU7TnJ6npX
```

---

## 🛠️ Local Development Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yousefhatem12/backend_skillmatch_laravel.git
   cd backend_skillmatch_laravel
   ```

2. **Install PHP dependencies:**
   ```bash
   composer install
   ```

3. **Install JavaScript dependencies:**
   ```bash
   npm install
   ```

4. **Environment setup:**
   ```bash
   cp .env.example .env
   php artisan key:generate
   php artisan jwt:secret
   ```

5. **Run Database Migrations & Seeds:**
   ```bash
   php artisan migrate --seed
   ```

6. **Start the Development Servers:**
   ```bash
   php artisan serve
   # In a separate terminal:
   npm run dev
   ```

---

## 📚 API Documentation

Once the server is running, explore the interactive Swagger documentation at:
```
http://localhost:8000/api/documentation
```
Or inspect the static OpenAPI spec located at [docs/openapi.yaml](docs/openapi.yaml).
