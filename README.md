# The American Gift — Pre-order Landing Page

Single-page static site for **The American Gift** by Eduardo G. "Eddy" Perez, Jr.
(Wiley, Fall 2026). Deployed via **GitHub Pages**.

## Structure
```
index.html        ← the page (HTML + inline page styles)
assets/
  brand.css       ← brand tokens + shared components
  _Y1A7140.jpg    ← hero photo
  _Y1A7342.jpg    ← about portrait
  cover-front.png ← book cover
  storm-ring-*.svg← background motif
.nojekyll         ← REQUIRED: tells GitHub Pages not to run Jekyll, which would
                    otherwise drop the underscore-prefixed photos (_Y1A7140.jpg…)
CNAME             ← custom domain for GitHub Pages
```

No build step. GitHub Pages serves `index.html` from the repo root.

## Pre-order form → HighLevel
The form sends each submission to a **HighLevel Inbound Webhook**.

**To go live:** open `index.html`, find `HIGHLEVEL_WEBHOOK_URL` near the bottom, and
paste the webhook URL from your HighLevel workflow's *Inbound Webhook* trigger:

```js
const HIGHLEVEL_WEBHOOK_URL = "https://services.leadconnectorhq.com/hooks/....";
```

Payload sent (JSON): `{ name, email, source, page, submitted_at }`.

Until a URL is set, the form validates and shows the success state but only keeps a
local copy (safe demo — nothing is sent).

## Local preview
```
python3 -m http.server 8090 --directory .
# open http://localhost:8090
```
