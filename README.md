# RepeatWise docs site (source)

Plain Jekyll, the version built into GitHub Pages. No plugins, no external scripts, fonts or analytics (the privacy page says the site does not track).

## Layout

- `site/index.md`, `support.md`, `attribution.md`: hand-written pages.
- `site/guide/` and `site/legal/`: **generated** from `docs/user/*.md` and `docs/legal/*.md`. Do not edit them.
- `site/_layouts`, `site/assets/style.css`: layout and the single stylesheet (light/dark through `prefers-color-scheme`).

## Updating content

Edit the files in `docs/user/` or `docs/legal/`, then run `npm run site:sync`. `npm test` fails if the copies in `site/` are out of date.

Legal pages show the banner "Draft - not yet reviewed by counsel". To remove it, set `draft: false` for the `legal` section in `scripts/site-sync.mjs` and re-run the sync. Keep every `[TO CONFIRM]` marker until resolved.

## Publishing (Kevin only, not done yet)

The workflow `.github/workflows/pages.yml` builds `site/` and deploys it with GitHub Actions.

1. Merge this work to `main`.
2. Repository Settings > Pages > Build and deployment > Source: **GitHub Actions**.
3. Run the "Docs site" workflow from the Actions tab (it never runs on push). The URL is shown in the workflow run, normally `https://mrvivino.github.io/repeatwise/`.
4. `baseurl` is already `/repeatwise`; set `url` in `site/_config.yml` if the address differs, then run the workflow again. Replace `<docs site URL>` in `docs/marketplace/submission-checklist.md`.
5. Fill the `[TO CONFIRM]` items (support email, Marketplace URL) and have counsel review the legal pages before announcing.

A repository on a free plan must be public for Pages. A custom domain can be set in the same Pages settings.

## Local preview (optional)

`cd site && bundle install && bundle exec jekyll serve`
