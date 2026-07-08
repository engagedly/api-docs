# Engagedly API Documentation

Source for the **[Engagedly API Reference](https://api.engagedly.com/beta)** documentation. The site is built with [Slate](https://github.com/slatedocs/slate) on top of [Middleman](https://middlemanapp.com/), written in Markdown, and published to GitHub Pages.

![Deploy](https://github.com/engagedly/api-docs/actions/workflows/deploy.yaml/badge.svg)

## Features

- **Single-page, responsive layout** — description on the left, code samples on the right; looks good on desktop, tablet, phone, and in print.
- **Just Markdown** — all content (including code samples) is plain Markdown.
- **Multi-language code samples** with tabbed switching.
- **Syntax highlighting** for [100+ languages](https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers) via Rouge, no config required.
- **Auto-generated, smooth-scrolling table of contents** that tracks your position.
- **RTL support** for right-to-left languages.

## Prerequisites

- **Linux or macOS** (Windows is unsupported).
- **Ruby 3.4.9** — the version is pinned in [`.ruby-version`](.ruby-version); tools like `rbenv`/`rvm` will pick it up automatically. The `Gemfile` reads its Ruby requirement from that same file.
- **Bundler** — ships with Ruby 3.4.9. If `bundle` isn't found, run `gem install bundler`.
- **Node.js** — used as the JavaScript runtime (via ExecJS) for the asset pipeline during builds.

## Local development

```shell
# clone the repo
git clone https://github.com/engagedly/api-docs.git
cd api-docs

# install dependencies
bundle install

# start the live-reloading dev server
bundle exec middleman server
```

The docs are then served at **http://localhost:4567** and rebuild automatically as you edit.

## Building the static site

```shell
bundle exec middleman build --clean
```

The generated site is written to the `build/` directory.

## Editing the docs

- **`source/index.html.md`** — the main document and its front matter (title, language tabs, list of includes, `api_endpoint`, etc.).
- **`source/includes/`** — the content is split into partials (`_users.md`, `_departments.md`, `_activities.md`, …). To add a new section, create `source/includes/_your_section.md` and add `your_section` to the `includes:` list in `source/index.html.md`.

See the Slate wiki for [Markdown syntax](https://github.com/slatedocs/slate/wiki/Markdown-Syntax) reference.

## Deployment

Deployment is automated via **GitHub Actions** ([`.github/workflows/deploy.yaml`](.github/workflows/deploy.yaml)). On every push to `master` (or a manual `workflow_dispatch`), the workflow builds the site with Middleman and publishes `build/` to GitHub Pages. There's no manual deploy step.

## Credits

Built on the excellent [Slate](https://github.com/slatedocs/slate) (originally by [Robert Lord](https://lord.io)) and [Middleman](https://middlemanapp.com/), with syntax highlighting by [Rouge](https://github.com/rouge-ruby/rouge) and icons from [Font Awesome](https://fontawesome.com/).
