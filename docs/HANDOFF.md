# Handoff: where things stand

Read this first in a new session (after `CLAUDE.md`).

## Current state (2026-11-02)
- Live at https://3littlesparks.com (GitHub Pages). Links: Whatnot and Vinted. The Mercari shop
  was removed on 2026-10-15.

## Planned: the site becomes a shop (2026-11-24)
- Owner's decisions: a full shop (galleries, product pages, cart, Stripe checkout) fed from Spark Stock,
  built there as the Pro "Website shop" feature; this site is the first shop. Whatnot and Vinted stay;
  sales on any side keep the others in step. Own Stripe account for 3 Little Sparks, live postage
  (labels in Pirate Ship), Michigan 6% tax on items for Michigan orders only, shipping not taxed.
- Plan: `docs/plans/WEBSITE_SHOP_PLAN.md` in `truthytruth/Spark-Stock`. Wording, look and policies on this
  site are approved by the shop owner before any change here.

## Shop on the page (live 2026-11-25, owner's yes; the shop is still closed, so the public sees the page as before)
- The page loads Spark Stock's shop script (`https://sparkstock.app/shop/embed.js`) into `#shop`.
  While the shop is closed the page looks exactly as before (big Whatnot/Vinted buttons, "coming
  soon"). Once it's open, or with `?preview=<key>` (the key is in Spark Stock › Settings › Website
  shop), the logo shrinks, Whatnot and Vinted become a compact row up top, and the shop shows under
  "Shop our pieces". The `body:has(#shop[data-spark-shop-state="ready"])` rules do the switch.
- Shop colors and fonts come from the page's `--spark-shop-*` variables (plum buttons, Nunito and
  Cormorant Garamond). Plan: `docs/plans/WEBSITE_SHOP_PLAN.md` in `truthytruth/Spark-Stock`.

## Email on the domain (live 2026-11-26)
- Real inboxes via **iCloud+ Custom Email Domain** (free with the family iCloud plan), not forwarding.
  The domain is on the owner's Apple account, shared with family: `support@3littlesparks.com` is the
  owner's; the shop owner has her own address on it in her own iCloud Mail. Both tested (receive).
  `sparkstock.app` is set up the same way (owner only, `support@`), receive and reply tested.
- DNS (Cloudflare): Apple's Cloudflare auto-setup replaced Email Routing's MX with iCloud's, merged
  the root SPF (`include:_spf.mx.cloudflare.net include:icloud.com`), added `apple-domain=` TXT and
  the `sig1._domainkey` CNAME. Website, Google verification, and Spark Stock's `cf-bounce` sending
  records were left alone.
- Setup tips: manual setup isn't offered for Cloudflare domains, so use Apple's Cloudflare route
  ("Unlock Email Routing records", then authorize). Add addresses as **new**, not "existing", unless
  they already receive mail, or Apple's check email goes nowhere.
- Open: Cloudflare Email Routing is still switched on for both domains but unused (harmless); can be
  turned off with the owner's OK.
