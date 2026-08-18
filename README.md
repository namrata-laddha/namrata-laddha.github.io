# namrata-laddha.github.io

Personal site for Namrata G. Laddha — avionics and power electronics engineer for space systems.

Live at **https://namrata-laddha.github.io**

Built on [al-folio](https://github.com/alshedivat/al-folio) (Jekyll), restyled with a custom design layer.

---

## Running it locally

Requires **Ruby 3.3.x** (match the version CI uses), **ImageMagick**, and **Node.js**.

```bash
bundle install
bundle exec jekyll serve --port 8080 --livereload
```

Then open http://localhost:8080.

### Windows notes

Two gotchas, both local-only — CI on Ubuntu is unaffected:

- **ImageMagick.** The `jekyll-imagemagick` plugin shells out to `convert`, but on Windows that name resolves to `C:\Windows\System32\convert.exe` (the disk-format utility). ImageMagick 7 installs only `magick.exe`. Put a `convert.cmd` shim earlier on `PATH` that forwards to `magick.exe`, or set `imagemagick.enabled: false` in `_config.yml` while developing.
- **Node.js is not optional.** Without a JS runtime, ExecJS falls back to Windows JScript, `jekyll-terser` throws a `SyntaxError` on every modern JS file, and **those files are silently dropped from `_site`** — which breaks dark mode, search, and image zoom with no obvious error. Install Node.

## Where things live

| What                                  | Where                                         |
| :------------------------------------ | :-------------------------------------------- |
| Site config, nav, feature toggles     | `_config.yml`                                 |
| Bio / landing page                    | `_pages/about.md`                             |
| CV content                            | `assets/json/resume.json` (jsonresume format) |
| CV page settings and PDF link         | `_pages/cv.md`, `assets/pdf/`                 |
| Publications                          | `_bibliography/papers.bib`                    |
| Projects                              | `_projects/*.md`                              |
| Blog posts                            | `_posts/` (empty for now)                     |
| Social links                          | `_data/socials.yml`                           |
| **Design layer**                      | `_sass/_custom.scss`                          |
| Design tokens (color, radius, shadow) | `_sass/_variables.scss`, `_sass/_themes.scss` |

### Two things worth knowing

- `assets/json/resume.json` **overrides** `_data/cv.yml`. The CV page renders from the JSON; the YAML file has been removed to avoid the ambiguity.
- All visual customization lives in `_sass/_custom.scss`, imported last. Upstream al-folio files are left almost untouched so the theme can still be updated from upstream. To re-theme the whole site, change `$accent` in `_sass/_variables.scss`.

## Adding content

**A project:** add `_projects/my-project.md` with `layout: page`, a `title`, `description`, and an `importance` number (lower sorts first). Add `img: assets/img/projects/thing.jpg` to give the card a thumbnail. Set `related_publications: true` and use a `cite` tag to pull in a bibliography entry.

**A publication:** add a BibTeX entry to `_bibliography/papers.bib`. Mark `selected={true}` to feature it on the landing page. Quote month values (`month = {May}`, not `month = may`) — an unquoted month is parsed as a BibTeX macro and leaks into other entries.

**A blog post:** add `_posts/YYYY-MM-DD-title.md`. Re-enable `rss_icon` in `_data/socials.yml` once there is something to subscribe to.

## Deployment

Pushing to `main` triggers `.github/workflows/deploy.yml`, which builds the site and publishes it to GitHub Pages. The same workflow runs on pull requests but **skips deployment**, so a PR is a free check that the production build works before it goes live.
