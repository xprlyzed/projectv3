# Test Credentials — artirdim.com (Laravel + Inertia + Vue)

App served by Laravel via php-fpm 8.2 + nginx on port 3000 (supervisor programs: `laravel-fpm`, `laravel-nginx`, `laravel-scheduler`, `laravel-queue`, plus `mariadb`, `redis`).
Preview URL: https://46defd5c-9fff-4a49-8207-7061500e5505.preview.emergentagent.com

## Test Accounts (password for all: `password`)
| Role   | Email            |
|--------|------------------|
| Admin  | admin@test.com   |
| Seller | seller@test.com  |
| Buyer  | buyer@test.com   |

## DB (MySQL / MariaDB)
- DB: `auction`  User: `auction`  Pass: `auction123`  Host: 127.0.0.1:3306

## Live-stream test note
- Live auction slug: `antika-masa-saati-ve-vazo-seti-T4Yf` (`is_live=1`, status active) — use for testing live-stream UI, mobile & desktop fullscreen live rooms.
- LiveKit is configured in `.env` (LIVEKIT_URL / API_KEY / API_SECRET set).
