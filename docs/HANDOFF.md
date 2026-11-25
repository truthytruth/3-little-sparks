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

## Shop on the page (built 2026-11-25, branch `claude/tender-euler-n4g83h`, not merged)
- The page loads Spark Stock's shop script (`https://sparkstock.app/shop/embed.js`) into `#shop`.
  While the shop is closed the page looks exactly as before (big Whatnot/Vinted buttons, "coming
  soon"). Once it's open, or with `?preview=<key>` (the key is in Spark Stock › Settings › Website
  shop), the logo shrinks, Whatnot and Vinted become a compact row up top, and the shop shows under
  "Shop our pieces". The `body:has(#shop[data-spark-shop-state="ready"])` rules do the switch.
- Shop colors and fonts come from the page's `--spark-shop-*` variables (plum buttons, Nunito and
  Cormorant Garamond). Plan: `docs/plans/WEBSITE_SHOP_PLAN.md` in `truthytruth/Spark-Stock`.
