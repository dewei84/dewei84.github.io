# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository overview

This is `dewei84.github.io`, a GitHub Pages site with two distinct kinds of content living side by side:

1. **A Jekyll family-memories blog** (site root) — built on the [Lanyon](https://github.com/poole/lanyon) theme (a [Poole](https://github.com/poole/poole) child theme), publishing short posts (mostly a video + a caption) about the author's family.
2. **Standalone single-page project apps** under `projects/` — self-contained HTML/CSS/JS pages unrelated to Jekyll, each its own mini-project with independent styling and no shared build system.

The site is served at `https://dewei.sg` (see `CNAME`) via GitHub Pages' native Jekyll build — there is no CI workflow and no committed `Gemfile`/`Gemfile.lock` (both are gitignored), so it relies on GitHub Pages' default Jekyll/gem versions rather than a pinned Bundler setup.

## Commands

There is no package manager, linter, or test suite in this repo. Development is Jekyll's standard local-serve loop:

```bash
bundle install          # first time only, if you have a local Gemfile/gems
bundle exec jekyll serve   # serve at http://localhost:4000 with live rebuild
# or, without Bundler:
jekyll serve
```

There are no build/lint/test commands to run — verify changes by serving the site locally and checking pages in a browser, or by opening the relevant `projects/*/index.html` file directly (they need no server since they're static, dependency-free HTML files).

## Architecture

### Jekyll blog (site root)

- `_config.yml` — site settings (title, tagline, `baseurl`, `permalink: pretty`, `paginate: 5`, author info, `jekyll-paginate` plugin).
- `_layouts/default.html` — outer HTML shell: includes `head.html`, renders the masthead/title, wraps `{{ content }}`, and a footer. All other layouts extend this one.
- `_layouts/page.html` — for standalone pages (`layout: page` front-matter), e.g. `about.md`.
- `_layouts/post.html` — for blog posts: renders the post title/content, then a "Keep Exploring" section of up to 3 related posts sampled from the same `categories`.
- `_includes/head.html` — `<head>` contents: fonts, stylesheet links (`public/css/{poole,syntax,lanyon,custom}.css`), Open Graph meta tags (auto-derived poster image/description for posts by parsing content), favicon, RSS `<link>`, and the Simple Analytics script tag.
- `_includes/sidebar.html` — collapsible nav drawer; auto-populates a link for every page whose front-matter has `layout: page` (sorted by URL), plus a hardcoded Home link.
- `index.html` (`layout: default`) — the homepage. Groups posts by `categories` and renders them under section headings, with `category_order = "Together,Chloe,Brian"` forced first, followed by any other categories alphabetically.
- `_posts/` — one Markdown file per memory, named `YYYY-MM-DD-slug.md`. Post front-matter is minimal: `layout: post`, `title`, `categories` (a single category, currently one of `Brian`, `Chloe`, or `Together`). Body content starts with `<!--more-->` (the excerpt separator) followed by an embedded `<video>` (hosted on an external S3 bucket, `poster` attribute set to a matching thumbnail) and a short caption. Follow this exact pattern for new posts.
- `about.md`, `404.md` — standalone pages using `layout: page`/`layout: default` respectively.
- `atom.xml` — RSS/Atom feed template (`layout: null`), iterates `site.posts`.
- `public/css/` — `poole.css` and `lanyon.css` are the vendored theme styles (avoid editing unless updating the theme itself); `custom.css` holds this site's own dark-theme overrides (colors, fonts, spacing) and is the right place for visual tweaks; `syntax.css` is for code-block highlighting.
- `public/js/script.js` — the only site JS: toggles the sidebar drawer via a checkbox hack and closes it on outside clicks.

**Adding a new post**: create `_posts/YYYY-MM-DD-descriptive-slug.md` with `layout: post`, a `title`, and a single `categories` value; keep the `<!--more-->` + `<video poster="...">` + caption structure used by existing posts unless the post has no video.

**Adding a new top-level page**: add a `.md` file with `layout: page` front-matter at the repo root — it will automatically appear in the sidebar nav (see `_includes/sidebar.html`) without further wiring.

### Standalone project pages (`projects/`)

Each subdirectory under `projects/` is an independent, self-contained static page — not part of the Jekyll build pipeline (no front-matter, no shared layout). Each is a single `index.html` with all CSS and JS inlined in `<style>`/`<script>` tags, using CSS custom properties for theming (including `prefers-color-scheme: dark` support) and no external JS frameworks or build tooling. They're linked to from the main site only if explicitly referenced elsewhere; treat each project folder as isolated — changes to one must not assume anything about the Jekyll layouts/includes above.

- `projects/ai-stack-map/index.html` — "The AI Stack" interdependence map, a dark-themed data-viz single-pager.
- `projects/tour-de-france-2026/` — a Tour de France 2026 stage tracker (`index.html` plus its own favicons). This one maintains a `CHANGELOG.md` recording notable changes (added/changed/fixed/known limitations) — update it when making non-trivial changes to this project, following its existing format.

When editing a project page, keep everything self-contained in that one `index.html` (no new external dependencies) unless the project already pulls in something like Google Fonts.
