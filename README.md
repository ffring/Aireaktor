# РЕАКТОР — Landing Pages

Лендинги для курса РЕАКТОР (Plaan Academy).

## Сайты

| URL | Описание |
|-----|----------|
| https://aireaktor.ru | Основной лендинг курса РЕАКТОР |
| https://aireaktor.ru/web | Страница регистрации на открытый урок |

## Структура

```
/
├── index.html          # Основной лендинг
├── web/
│   └── index.html      # Открытый урок (GetCourse popup)
├── img/                # Изображения
│   ├── denis-hero.jpg
│   ├── module-*.png    # Иллюстрации программы
│   ├── case-*.png      # Скриншоты showcase
│   └── bonus-*.png     # Иллюстрации бонусов
├── _headers            # Cloudflare security headers
└── _redirects          # Cloudflare redirects
```

## Деплой

Хостинг: **Cloudflare Pages** (проект `aireaktor`)

```bash
cd /tmp/aireaktor-minimal
source ~/.openclaw/.env
CLOUDFLARE_API_TOKEN="$CLOUDFLARE_API_KEY" \
CLOUDFLARE_ACCOUNT_ID="adddfd68d98205987d250f720b5acf60" \
npx wrangler pages deploy . --project-name=aireaktor --branch=main --commit-dirty=true
```

## Ключевые элементы

### aireaktor.ru
- Логотип РЕАКТОР. в header
- Hero с кнопкой "Посмотреть программу" → скроллит к #program
- 4 модуля программы с иллюстрациями
- Showcase "Что создают вайбкодеры" — case-*.png скриншоты
- 16 бонусов с value stacking
- Ценообразование: 202 000₽ → 29 900₽ (скидка 85%)
- Floating CTA "Забронировать место"
- FAQ accordion
- GetCourse форма (#pricing)

### aireaktor.ru/web
- Страница регистрации на открытый урок 12.02
- Кнопка → popup с GetCourse формой (iframe)
- Countdown таймер
- Динамический счётчик мест (274/500)
- Футер: PLAAN ACADEMY

## Security Headers

- HSTS (1 год + preload)
- X-Frame-Options: DENY
- CSP с разрешением edu.plaan.ai
- X-Content-Type-Options: nosniff

## Changelog

### 2026-02-07
- Добавлен логотип РЕАКТОР. на aireaktor.ru
- Исправлен smooth scroll (убрана зависимость от nav)
- "В результате курса:" — увеличен шрифт
- Floating CTA: "Записаться 29 900₽" → "Забронировать место"
- Убрана строка "Доступ к урокам... 10 000₽"
- Ценность: 212 000₽ → 202 000₽
- Showcase: заменены иллюстрации на скриншоты (case-*.png)
- /web: popup GetCourse вместо inline формы
- /web: PLAAN ACADEMY в футере
- Убран API ключ из кода (security fix)

### 2026-02-06
- Первоначальный деплой
- Security headers (HSTS, CSP, X-Frame-Options)
- GTM tracking
