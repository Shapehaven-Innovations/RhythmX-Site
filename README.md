# RhythmX site

Static landing page and guides for [RhythmX](https://github.com/Shapehaven-Innovations/RhythmX), a private menstrual cycle tracker for iPhone.

Live: https://rhythmx.shapehaveninnovations.com/

## Layout

| Path | Purpose |
| ---- | ------- |
| `index.html` | Landing page. Markup only; styles and script are shared |
| `guides/track-your-cycle-privately/` | Guide: four checks for any period tracker |
| `guides/menstrual-cycle-phases-reference/` | Reference: timing, hormones, symptoms and tips per phase |
| `assets/site.css`, `assets/site.js` | Shared styles (light and dark) and the mobile nav toggle |
| `assets/` | App icon (`icon.png`, rounded `icon-rounded.png` for the favicon), screenshots (`tab*.png` with `.webp` copies), `og.png` |
| `llms.txt`, `llms-full.txt` | Summary and full documentation for LLM crawlers |
| `robots.txt`, `sitemap.xml` | Crawler config |
| `CNAME` | Custom domain for GitHub Pages |

## Run locally

```sh
python3 -m http.server 8000
```

Open http://127.0.0.1:8000/. Pages use root-absolute paths, so serve from the repo root.

## Keeping content in sync

- The header and footer are copied into every page. Change them in all three pages together.
- `llms-full.txt` is the app README plus the text of both guides. Refresh it when either changes.
- Links marked `data-appstore` currently point to the GitHub repo because the App Store URL is not set. When the app is live, rewrite the `href` of every anchor with `data-appstore`, and update `downloadUrl` in the JSON-LD on `index.html` and the link in `llms.txt`.
- If the minimum iOS version or feature list changes, update `index.html`, `llms.txt` and the JSON-LD together.
- Regenerate `assets/icon-rounded.png` and `assets/og.png` if the app icon or Insights screenshot changes. Re-export `.webp` copies when `.png` screenshots change.
- Update `<lastmod>` in `sitemap.xml` and `dateModified` in a guide's JSON-LD when that guide changes.
