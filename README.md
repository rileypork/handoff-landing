# handoff-landing

Marketing site for Speckit feature `002-acquisition-landing`.

Handoff is the LA Marketplace delivery API for agents. This repo is brand plus access request only. It is not a consumer booking app.

## T002 audit (removed from the old POC)

The previous `index.html` was a consumer courier page. Removed:

- Hero "Found it? We'll get it."
- SMS / Photon "Text us" CTA and phone number
- Instagram / Facebook "Message us" and `@texthandoff` product CTAs
- On-page Marketplace quote form (listing URL, ZIPs, item type, notes)
- `formsubmit.co` quote post that invented a checkout-adjacent flow
- Neighborhood booking tags as the primary product surface

Kept and reused:

- Ink `#0A0A0A`, cobalt `#2F5BFF`, chalk `#F2F0EB`
- Westside LA framing
- Contact inbox `handoff@agentmail.to` for API access only
- Static files (no app router, no `/v1` proxy)

## Local

    python3 -m http.server 4173

Open `http://127.0.0.1:4173/`.

## Deploy (T016)

Existing GitHub homepage: `https://texthandoff.vercel.app`

- GitHub Pages workflow is in `.github/workflows/pages.yml` and deploys on push to `main`. Pages is not enabled on the repo today (`has_pages: false`). Enabling it needs Riley in repo Settings → Pages → GitHub Actions.
- The Vercel production project behind `texthandoff.vercel.app` is not in the Vercel account this agent can see. Do not create a second Vercel project. After merge to `main`, if that project is still connected to `rileypork/handoff-landing`, it should pick up the rewrite.
- Soft URL after merge (if the existing Vercel git hook is live): `https://texthandoff.vercel.app`
- If production does not update: Riley signs into the Vercel project tied to this repo (or enables GitHub Pages) and deploys `main`. No extra secrets belong in this frontend.

## Access path

Request API access → `mailto:handoff@agentmail.to`. No Stripe, no payment fields, no live pricing.

## Speckit

Source of truth lives in `rileypork/handoff-delivery-api` under `specs/002-acquisition-landing/`. Copy lock is `brand-advisory.md`.
