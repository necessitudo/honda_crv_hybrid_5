# Honda CR-V Hybrid RT5/RT6

Статический сайт на Jekyll (на русском языке), опубликованный на GitHub Pages:
https://necessitudo.github.io/honda_crv_hybrid_5

Сайт-база знаний по эксплуатации Honda CR-V Hybrid RT5/RT6: мануалы, электрические схемы и пользовательские советы/процедуры.

## Требования

- Ruby 3.x (системный Ruby на macOS может быть слишком старым для зависимостей `github-pages`/`nokogiri` — при необходимости поставьте актуальную версию, например через Homebrew: `brew install ruby@3.3`)
- Bundler

## Установка и запуск

```bash
bundle install                 # установка гемов (при первом запуске / после изменения Gemfile)
bundle exec jekyll serve       # локальный сервер с live-rebuild
```

Сайт будет доступен на http://localhost:4000/honda_crv_hybrid_5/

Сборка статики в `_site/`:

```bash
bundle exec jekyll build
```

Тестов и линтеров в проекте нет.

## Структура проекта

- [`_config.yml`](_config.yml) — общие настройки сайта (заголовок, описание, baseurl, remote theme, kramdown/GFM, TOC).
- [`_data/globals.yml`](_data/globals.yml) — внешние ссылки (мануалы на Яндекс.Диске, схемы электрики и т.д.), используются в контенте через `{{ site.data.globals.<key> }}`.
- [`_posts/`](_posts/) — контент в виде датированных Jekyll-постов (`YYYY-MM-DD-title.markdown`). Сайт устроен как база знаний, а не хронологический блог: новый материал обычно добавляется как новый пост или дописывается в существующий (например, [`_posts/2025-06-05-manuals.markdown`](_posts/2025-06-05-manuals.markdown) объединяет мануалы, схемы и советы по разделам).
- [`_layouts/`](_layouts/) — `default.html` и `page.html` сейчас пустые и наследуют одноимённые layout'ы из удалённой темы.
- [`404.html`](404.html) — страница 404 с русским текстом (ссылки на `/blog/` и `/contact/`, которых пока нет как маршрутов).

## Тема

Используется `remote_theme: sighingnow/jekyll-gitbook` (см. [`_config.yml`](_config.yml)), а не локальный гем `minima` из `Gemfile`. Layout'ы и include'ы темы подтягиваются удалённо во время сборки и в репозитории не хранятся.

## Добавление контента

Новые внешние ссылки (мануалы, схемы и т.п.) добавляйте в [`_data/globals.yml`](_data/globals.yml), а не хардкодьте URL прямо в постах. Контент и комментарии пишутся на русском языке — придерживайтесь этого стиля.
