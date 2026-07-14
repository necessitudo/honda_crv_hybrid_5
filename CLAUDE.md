# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

A Jekyll static site (Russian language) hosted on GitHub Pages, documenting ownership info for the Honda CR-V Hybrid RT5/RT6: manuals, wiring diagrams, and user tips/procedures. It is served at `https://necessitudo.github.io/honda_crv_hybrid_5`.

## Commands

```bash
bundle install          # install gems (first run / after Gemfile changes)
bundle exec jekyll serve  # run local dev server with live rebuild (http://localhost:4000/honda_crv_hybrid_5/)
bundle exec jekyll build  # build static site into _site/
```

There is no test suite or linter configured for this project.

## Architecture

- **Theme**: uses `remote_theme: sighingnow/jekyll-gitbook` (configured in [_config.yml](_config.yml)), not the local `minima` gem listed in the Gemfile. Theme-level layouts/includes are pulled remotely at build time and are not present in this repo.
- **`_config.yml`**: site-wide settings (title, description, baseurl, remote theme, kramdown/GFM options, TOC settings). Changes here require restarting `jekyll serve`.
- **`_data/globals.yml`**: central place for external links (Yandex Disk manuals, wiring diagrams, etc.), referenced in content via `{{ site.data.globals.<key> }}`. Add new external resource links here rather than hardcoding URLs in posts.
- **`_posts/`**: content lives here as dated Jekyll posts (`YYYY-MM-DD-title.markdown`), each with `layout`, `title`, `date`, and `category`/`categories` front matter. This is a knowledge-base/wiki site rather than a chronological blog — new content is generally added as new posts or appended to existing ones (e.g. [_posts/2025-06-05-manuals.markdown](_posts/2025-06-05-manuals.markdown) aggregates manuals, wiring diagrams, and user tips under headed sections).
- **`_layouts/default.html`** and **`_layouts/page.html`**: currently empty, effectively falling back to the remote theme's layouts of the same name.
- **`404.html`**: custom 404 page with Russian copy; note it links to `/blog/` and `/contact/` which do not currently exist as routes.
- Site content and comments are written in Russian; keep new content consistent with that.
