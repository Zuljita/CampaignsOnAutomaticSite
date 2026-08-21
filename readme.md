# Campaigns on Automatic — public site

Static site for [Campaigns on Automatic](https://campaignsonautomatic.com),
the campaign lens of the On Automatic family — a read-first browser for
Campaign Vaults. Same design system as the Dungeons and Hexes sites, with a
lapis-blue primary. (This repo is the product site; the vault FORMAT — spec,
schema, validator, example vault — lives in
[CampaignsOnAutomatic](https://github.com/Zuljita/CampaignsOnAutomatic).)

## Layout

- `index.html` — product homepage (hero is a real screenshot: the run view
  over a region exported by Hexes on Automatic)
- `tour.html` — the views, screenshotted against real vaults
- `vault.html` — the Campaign Vault format under the app
- `releases.html` — build status; download cards light up when the first
  `campaigns-continuous` build publishes
- `privacy.html`, `404.html`
- `styles.css` — design-system entry point (`tokens/` + `components/`)
- `site.css` — page layout
- `data/downloads.json` — placeholder release metadata (no urls until the
  first build; the mirror workflow overwrites it)

No build step. Every page is plain HTML + CSS with a little inline JS.

## Deploy

`.github/workflows/deploy.yml` deploys to Cloudflare Pages on push to `main`
(`wrangler pages deploy . --project-name campaignsonautomatic`). It needs:

- repo secret `CLOUDFLARE_API_TOKEN` (same token the sibling sites use)
- repo variable `CLOUDFLARE_ACCOUNT_ID`
- a Pages project named `campaignsonautomatic` (direct upload) in the account

The public home is `https://campaignsonautomatic.com/` — the zone is already
in the same Cloudflare account. Add apex + `www` as custom domains on the
Pages project and Cloudflare writes the proxied CNAMEs itself. Canonical
URLs, `robots.txt` and `sitemap.xml` assume that origin.

## Bugs

User-facing issues go to the family's public tracker:
<https://github.com/Zuljita/DungeonsOnAutomaticSite/issues> (say it's
Campaigns).

Campaigns on Automatic is an original, unofficial, non-resale fan game aid by
Kyle Norton for GURPS and the Dungeon Fantasy Roleplaying Game, used per the
SJ Games Online Policy. Not affiliated with or endorsed by Steve Jackson
Games.
