# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Personal portfolio site for SaqrWare (Omar Saqr), served by GitHub Pages at `saqrware.com` (see `CNAME`). It is a single-page Jekyll site using the GitHub Pages–supported `jekyll-theme-minimal` theme. There is no build tooling, tests, or Gemfile in the repo — GitHub Pages builds and deploys automatically on push to `master`.

## Local preview

No Gemfile is checked in. To preview locally, use the `github-pages` gem so plugin/theme versions match production:

```sh
gem install github-pages
jekyll serve   # http://localhost:4000
```

## Structure

- `index.md` — main page content (projects list). Most changes happen here.
- `_layouts/default.html` — a local override of the minimal theme's default layout. Its customization is `{% include bio.html %}` and `{% include contact.html %}` in the sidebar `<header>`. It still references theme-provided files that are not in this repo (`head-custom.html` include, `assets/js/scale.fix.js`, `{% seo %}`); these resolve from the theme gem at build time.
- `_includes/bio.html` — bio text shown in the sidebar (plain HTML, not Markdown).
- `_includes/contact.html` — contact links rendered as a row of Font Awesome icons in the sidebar (Font Awesome is loaded from cdnjs in the layout's `<head>`).
- `assets/css/style.scss` — imports the theme stylesheet (`@import "{{ site.theme }}"`, requires the empty front matter at the top) then adds `.contact` styles. Avoid bare `<ul>` in the sidebar: the theme absolutely-positions `header ul` at narrow widths (for download buttons).

## Content conventions

Projects in `index.md` follow a consistent blockquote format — keep new entries matching it:

```md
**[Name](url)**
> *Type (e.g. Chrome Extension, Web App, CLI Tool)*
> One-paragraph description.
> * **Features:** Item · Item · Item
```

Commit messages are short imperative summaries (e.g. "Add html2markdown project").
