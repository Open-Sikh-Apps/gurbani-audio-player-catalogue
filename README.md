# Gurbani Paath Player catalogue

Static JSON for [gurbani-paath-player](https://github.com/Open-Sikh-Apps/gurbani-paath-player). Audio files do **not** go here.

Cloudflare Pages project: `gurbani-paath-player-catalogue`. Deploy with Wrangler Direct Upload from GitHub Actions. Do **not** use Pages “Connect to Git”.

## Publish

1. Edit `catalogue.json`. Set `"version"` one higher than the last live publish.
2. Set the **same** integer in `catalogue.version.json`.
3. Push to `main` (or run the **Deploy** workflow from the Actions tab).

CI checkouts the app repo and runs Valibot (`scripts/validate-catalogue.ts`). Upload happens only after that passes.

Upload order if you ever use the Cloudflare dashboard: `catalogue.json` first, then `catalogue.version.json`.

## App URL

```
EXPO_PUBLIC_CATALOGUE_BASE_URL=https://gurbani-paath-player-catalogue.pages.dev
```
