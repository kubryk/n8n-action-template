# n8n Template

Docker Compose шаблон для швидкого розгортання n8n з SQLite.

## Особливості

- ✅ Просте розгортання з Docker Compose
- ✅ Використання SQLite (не потрібен окремий PostgreSQL)
- ✅ Налаштування через змінні середовища
- ✅ GitHub Actions workflow для автоматичного деплою на VPS

## Швидкий старт

### Локальна розробка

1. Скопіюйте `.env.example` в `.env` (якщо є) або створіть `.env` файл:
```env
N8N_HOST=localhost
N8N_PROTOCOL=http
WEBHOOK_URL=http://localhost:5678/
GENERIC_TIMEZONE=UTC
```

2. Запустіть контейнери:
```bash
docker compose up -d
```

3. Відкрийте браузер: http://localhost:5678

### Продакшн деплой

1. Створіть `.env` файл на сервері з налаштуваннями:
```env
N8N_HOST=yourdomain.com
N8N_PROTOCOL=https
WEBHOOK_URL=https://yourdomain.com/
GENERIC_TIMEZONE=Europe/Kyiv
```

2. Використайте GitHub Actions workflow для автоматичного деплою або запустіть вручну:
```bash
docker compose up -d
```

## Структура проекту

- `docker-compose.yml` - конфігурація Docker Compose
- `.github/workflows/deploy.yml` - GitHub Actions workflow для деплою
- `.env` - змінні середовища (не завантажується в git)

## Змінні середовища

| Змінна | Опис | За замовчуванням |
|--------|------|------------------|
| `N8N_HOST` | Хост для n8n | `localhost` |
| `N8N_PROTOCOL` | Протокол (http/https) | `http` |
| `WEBHOOK_URL` | URL для webhook | `http://localhost:5678/` |
| `GENERIC_TIMEZONE` | Часовий пояс | `UTC` |

## GitHub Actions Deploy

Workflow дозволяє автоматично деплоїти на VPS через GitHub Actions. Для використання:

1. Перейдіть в Actions → Deploy n8n
2. Натисніть "Run workflow"
3. Введіть дані вашого VPS:
   - SSH Host (IP або домен)
   - SSH User
   - SSH Port (за замовчуванням 22)
   - SSH Private Key (PEM формат)
   - Вміст .env файлу

## Ліцензія

MIT

