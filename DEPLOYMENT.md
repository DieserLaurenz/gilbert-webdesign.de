# Deployment

This project deploys to Cloudflare as a Worker, not via the old Pages Functions path.

## Current setup

- Astro 6 with `@astrojs/cloudflare`
- GitHub Actions workflow: `.github/workflows/cloudflare-workers.yml`
- Deploy command: `npx wrangler@4.73.0 deploy --config dist/server/wrangler.json`
- Worker config source: `wrangler.jsonc`

## Required GitHub secrets

- `CLOUDFLARE_API_TOKEN`
- `CLOUDFLARE_ACCOUNT_ID`

## Required Cloudflare state

- Custom domains `gilbert-webdesign.de` and `www.gilbert-webdesign.de` must belong to the Worker `gilbert-webdesign`
- Conflicting DNS records for `@` / `www` must not point to old Pages hosts

## What broke before

- Astro 6 generated a Worker-oriented Cloudflare output
- Cloudflare Pages Git builds still tried to treat the project like Pages Functions
- This caused `_worker.js/index.js` resolution errors and later domain/DNS conflicts

## Useful checks

- Local build: `npm run build`
- Confirm generated worker config: `dist/server/wrangler.json`
- If deploy fails on secrets, check GitHub Actions repository secrets
- If deploy fails on domain attach, check Cloudflare DNS records and Worker custom domains
