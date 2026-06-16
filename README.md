# Pin Share — Website (GitHub Pages)

Лендинг + Privacy Policy + Terms of Use под публикацию через GitHub Pages.

## Файлы

| Файл | Зачем |
|---|---|
| `index.html` | Лендинг (фичи + ссылки на privacy/terms) |
| `privacy.html` | Privacy Policy — нужен для App Store Connect |
| `terms.html` | Terms of Use — нужен для App Store Connect |
| `style.css` | Тёмная тема под бренд (green accent `#7BAE7E`) |

## Перед публикацией

В файлах используется placeholder-домен `pinshare.app` и email `onlinekirillandreevich@gmail.com`. Если у тебя другой домен/email — пройдись поиском по всем `.html` и замени.

Также проверь даты «Effective date / Last updated» — стоит 1 января 2026. Перед запуском поставь актуальную дату.

## Деплой на GitHub Pages

### Способ 1 — через UI (проще)

1. Создай новый репозиторий на GitHub, например `pinshare-website`.
2. Загрузи все 4 файла (`index.html`, `privacy.html`, `terms.html`, `style.css`) в корень.
3. Settings → Pages → Source: **Deploy from a branch** → Branch: **main** / **(root)** → Save.
4. Через 1-2 минуты сайт будет доступен по `https://<your-username>.github.io/pinshare-website/`.

### Способ 2 — через терминал

```bash
cd /Users/kirillproncev/Desktop/My\ Apps/LocationShare-specs/website
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin git@github.com:<your-username>/pinshare-website.git
git push -u origin main
```
Затем включи Pages в Settings → Pages как в способе 1.

### Кастомный домен (опционально)

1. Купи домен (`pinshare.app` через Namecheap / Cloudflare / etc).
2. В GitHub Settings → Pages → Custom domain → введи свой домен.
3. У регистратора пропиши DNS:
   - `A` records на `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Или `CNAME` на `<your-username>.github.io`
4. В UI GitHub Pages поставь ☑ Enforce HTTPS.

## URL'ы для App Store Connect

Когда сайт зальёшь — итоговые URL должны быть:

- **Privacy Policy URL**: `https://<домен>/privacy.html`
- **Terms of Use URL** (в App Description): `https://<домен>/terms.html`
- **Support URL**: `https://<домен>/index.html` (или `mailto:onlinekirillandreevich@gmail.com`)

Вставь их в App Store Connect → App Information.

## Локальный preview

В Mac предустановлен Python, открой папку и запусти:

```bash
cd /Users/kirillproncev/Desktop/My\ Apps/LocationShare-specs/website
python3 -m http.server 8000
```

Открой `http://localhost:8000/` в браузере.

## Что НЕ делать

- ❌ Не публикуй в публичном репо ключи Adapty/PostHog (они в Xcode-проекте, не в сайте).
- ❌ Не меняй структуру URL после публикации сайта в App Store Connect (Apple Review может пометить как broken link, если ссылка в Description укажет в никуда).
- ❌ Не используй Privacy Policy / Terms «от балды». Если планируешь scale > 10k MRR — отдай на review юристу (для MVP достаточно).
