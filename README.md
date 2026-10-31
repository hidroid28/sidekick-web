# Sidekick Web

The Next.js frontend for Sidekick, a practical AI assistant for sole traders and everyday admin. It needs the Sidekick API, which is a separate NestJS service in the [`sidekick`](https://github.com/hidroid28/sidekick) repo.

## Run locally

Start the API first, then run:

```powershell
npm install
copy .env.example .env.local
npm run dev
```

Open http://localhost:3000.

## Deploy on Vercel

1. Import this repo in Vercel. It detects Next.js, so the default build settings work.
2. Add `NEXT_PUBLIC_API_URL`, set to the public URL of the API, such as `https://sidekick-api.onrender.com`.
3. Deploy.
4. On the API, set `WEB_ORIGIN` to your Vercel production URL, such as `https://sidekick-web.vercel.app`.

`NEXT_PUBLIC_API_URL` is built in at build time, so redeploy after changing it. Never put a secret in a `NEXT_PUBLIC_` variable, because those values reach the browser.

The API allows requests from one address only, its `WEB_ORIGIN`. Vercel preview deployments have other addresses, so they cannot reach the API. Use the production URL.

Payment links use `WEB_ORIGIN` as their address, so it must be this site's public URL.

## Shared code

`lib/shared.ts` is a copy of `packages/shared/src/index.ts` from the `sidekick` repo. When the API's schemas or types change, update this copy to match.

## Checks

```powershell
npm test
npm run typecheck
```
