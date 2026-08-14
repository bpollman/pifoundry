# pifoundry.com

Static site for Pi Foundry — a home for small mobile apps and side projects.
Plain HTML/CSS, no build step. Hosted free on GitHub Pages.

## Files

| File | Purpose |
|------|---------|
| `index.html` | Home page — hero, about, projects grid |
| `privacy-policy.html` | Ooooby privacy policy (app stores link here — keep it live) |
| `styles.css` | All styling; responsive + automatic dark mode |
| `assets/` | favicon, images, social preview |
| `CNAME` | Tells GitHub Pages to serve at `pifoundry.com` |

## Preview locally

```sh
cd pifoundry-site
python3 -m http.server 8000
# open http://localhost:8000
```

## Add a new project

Open `index.html`, find the `TEMPLATE` comment inside `<div class="grid">`, and copy the
`<article class="card">` block. For a live app keep the two store buttons; for a retired
app add `class="card-archived"` and swap the buttons for a `<span class="badge">`.

## Deploy to GitHub Pages

1. Create a repo (recommended: **`pifoundry.github.io`** under the PiFoundry account/org,
   or any repo name).
2. Push these files to the `main` branch.
3. Settings → Pages → Build and deployment → Source: **Deploy from a branch**, branch `main`, `/root`.
4. Wait for the green check, then visit the `*.github.io` URL to verify before touching DNS.

## Point pifoundry.com at GitHub Pages (DNS — done at your domain registrar)

Currently DNS points at Google Sites. Replace it with:

**Apex `pifoundry.com` — A records:**
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```
(Optional IPv6 — AAAA records:)
```
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```

**`www` subdomain — CNAME:**
```
www  ->  pifoundry.github.io
```

After DNS propagates (minutes to a few hours): Settings → Pages → check **Enforce HTTPS**.

> Tip: verify the site on the `*.github.io` URL first, then cut DNS over last so there's no downtime.

`pifoundry.org` currently also points at the old Google Site; you can point it here too or leave it.
