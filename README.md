# BarCamp London XI

A static archive of the BarCamp London XI site, served at
[eleven.barcamplondon.org](https://eleven.barcamplondon.org).

## Hosting

It was a Nuxt site on Netlify (bcl11.netlify.com) until October 2026. The
source isn't here: `site/` is the generated site Netlify served (each page's
HTML shell, and the `_nuxt/` scripts and images that render it in the
browser), served by nginx on jiji, Cristiano's home server, behind its
Cloudflare tunnel. `nginx.conf` keeps Netlify's URL rules: `/about/` is
`about/index.html`, and `/about` redirects there.

A push to `main` runs `.github/workflows/publish.yml`: CI, then the image
`ghcr.io/cbetta/eleven.barcamplondon.org`, which it pins in jiji's
`docker-compose.yml` to deploy. `scripts/check.sh` checks every local link
resolves; `scripts/smoke.sh` builds the image and boots it.
