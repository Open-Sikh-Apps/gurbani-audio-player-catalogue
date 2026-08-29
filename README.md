# Gurbani Paath Player catalogue

Static JSON for [gurbani-paath-player](https://github.com/Open-Sikh-Apps/gurbani-paath-player). Audio files do **not** go here.

Cloudflare Pages project: `gurbani-paath-player-catalogue`. Deploy with Wrangler Direct Upload from GitHub Actions. Do **not** use Pages “Connect to Git”.

## Publish

1. Edit `catalogue.json`. Set `"version"` one higher than the last live publish.
2. Set the **same** integer in `catalogue.version.json`.
3. You can omit `byteSize` on new `sehaj_paath` / `audiobook` tracks. CI HEADs each URL (6 at a time), writes the object size, validates, then uploads.
4. Push to `main` (or run the **Deploy** workflow from the Actions tab). On `main`, CI also commits filled `byteSize` values so the next publish does not probe those tracks again.

CI checkouts the app repo, runs `scripts/fill-catalogue-bytesize.ts`, then Valibot (`scripts/validate-catalogue.ts`). Upload happens only after that passes. Sanity is not required.

Upload order if you ever use the Cloudflare dashboard: `catalogue.json` first, then `catalogue.version.json`.

## App URL

```
EXPO_PUBLIC_CATALOGUE_BASE_URL=https://gurbani-paath-player-catalogue.pages.dev
```
