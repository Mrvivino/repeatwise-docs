# RepeatWise docs site (source)

Plain Jekyll, the version built into GitHub Pages. No plugins, no external scripts, fonts or analytics (the privacy page says the site does not track).

## Layout

- `site/index.md`, `support.md`, `attribution.md`: hand-written pages.
- `site/guide/` and `site/legal/`: **generated** from `docs/user/*.md` and `docs/legal/*.md`. Do not edit them.
- `site/_layouts`, `site/assets/style.css`: layout and the single stylesheet (light/dark through `prefers-color-scheme`).

## Updating content

Edit the files in `docs/user/` or `docs/legal/`, then run `npm run site:sync`. `npm test` fails if the copies in `site/` are out of date.

Legal pages can show a "Draft - not yet reviewed by counsel" banner: set `draft: true` for the `legal` section in `scripts/site-sync.mjs` and re-run the sync. It is off since the placeholders were filled (2026-10-11).

## Publishing

The site is served by GitHub Pages from the **public** repository `Mrvivino/repeatwise-docs` (branch `main`, root folder, built-in Jekyll), because this app repository is private. Address: https://mrvivino.github.io/repeatwise-docs/ (`url` and `baseurl` in `_config.yml`). This is transitional, until a publisher site groups all apps; when the address changes, update `_config.yml`, `src/shared/support.ts`, `docs/marketplace/listing.md` and the Marketplace listing.

After `npm run site:sync`, run `scripts/site-publish.sh`. It copies `site/` into the public repository and pushes; Pages rebuilds in about a minute. Only `site/` is ever copied.

## Local preview (optional)

`cd site && bundle install && bundle exec jekyll serve`
