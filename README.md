# Лови цвет — сайт для App Review

Статические страницы без сборки и без JS. Английская версия в корне (её открывает ревьюер),
русская в `ru/`. Ссылки относительные: сайт работает и в подпапке GitHub Pages, и в корне своего домена.

| Файл | Назначение | Куда вписать в App Store Connect |
| --- | --- | --- |
| `index.html`, `ru/index.html` | об игре, правила, режимы | Marketing URL (необязательно) |
| `privacy.html`, `ru/privacy.html` | политика конфиденциальности | App Privacy → Privacy Policy URL |
| `support.html`, `ru/support.html` | поддержка, вопросы, контакт | Support URL |
| `styles.css` | оформление в стиле игры | |

Отдельные условия использования не нужны: игра бесплатная, без контента от пользователей и без покупок, действует
стандартное лицензионное соглашение Apple (Standard EULA). Если появятся покупки или подписка, понадобится `terms.html`
и ссылка на него в приложении.

## Локально

```bash
python3 -m http.server 8000 --directory site
# http://localhost:8000/
```

## Вариант 1. GitHub Pages (как «Книга рецептов»)

Отдельный репозиторий `lovi-cvet-site` с содержимым `site/` в корне, затем
**Settings → Pages → Deploy from a branch → `main` / `(root)`**.

Адреса:
- https://zxus777.github.io/lovi-cvet-site/
- https://zxus777.github.io/lovi-cvet-site/privacy.html
- https://zxus777.github.io/lovi-cvet-site/support.html
- русские: те же адреса с `ru/`

## Вариант 2. Свой домен на Cloudflare (как migno.app)

`wrangler.jsonc` в корне репозитория с `"assets": { "directory": "site" }` и `routes` на домен, деплой
`npx wrangler deploy` (подробности в `headache-book/docs/LANDING.md`).

## После публикации

- Открываются все шесть страниц, переключатель EN/RU работает в обе стороны, светлая и тёмная темы читаются.
- Ссылка на почту открывает почтовый клиент.
- Адреса политики и поддержки вписаны в приложение (Настройки) и в App Store Connect.
- Когда игра выйдет, добавить на главную кнопку App Store и `<meta name="apple-itunes-app" content="app-id=…">`.
- Любая правка текста — в обеих версиях и с новой датой «Last updated / Обновлено».
