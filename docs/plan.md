# Mudgar UK — Smoke Test Plan

## Goal

Test three distinct propositions for selling mudgars (Indian clubs) in the UK. Identify the strongest segment by CAC, conversion, and qualitative signal before committing to inventory or a single brand direction.

## Scope

Three separate Shopify stores, three brands, three domains, three ad campaigns. Managed centrally in one repo. Smoke test only — orders accepted with a full-refund fallback if sourcing fails on a given order.

## Propositions to test

### 1. Functional fitness — "Train what dumbbells can't"

The offset weight distribution and thick handle of a mudgar expose the weaknesses that balanced, easy-to-grip dumbbells hide. Lead on shoulder durability and crushing grip strength.

Target audience: kettlebell, mobility, and Onnit-adjacent. Functional fitness, calisthenics, longevity-curious.

### 2. Combat sports — "Built for the mat"

Pehlwani heritage gives instant credibility with grapplers. Lead on shoulder injury prevention and grip strength for gi work and clinch.

Target audience: BJJ, MMA, wrestling, boxing. Warm channel via existing BJJ contact.

### 3. Conscious living / aesthete — "A daily practice, made beautiful"

Position the mudgar as a beautiful object first, training tool second. Hardwood, hand-finished, ritual-oriented.

Target audience: yoga, slow living, interiors, Toast/Aesop/Daylesford demographic. Highest price point of the three.

### Deferred for round two

- South Asian diaspora gifting (Diwali, weddings, milestone gifts)
- B2B direct to gyms, dojos, studios

Different enough in approach and channel that they're better tested separately once round one results are in.

## Stack

- **Shopify Basic** × 3 stores (~£25/mo each)
- **3 domains** via Cloudflare or Namecheap
- **Custom themes** forked from Dawn, built locally with Claude Code and Shopify CLI
- **Payments:** Shopify Payments + Klarna/Clearpay
- **Analytics:** Meta Pixel, GA4, Hotjar on each store
- **Ad creative:** Gemini for imagery; commissioned photography for the aesthete store
- **Project management:** GitHub monorepo with shared docs, plus a simple tracking sheet for CAC/CVR/AOV per store

## Build approach

Fork Dawn three times. Maintain a `shared/` folder for any genuinely reusable components (cart, checkout patterns, design tokens) but treat each store as having its own visual identity — typography, palette, photography, voice. The aesthete store gets the most design investment. Fitness and combat can lean more functional.

Local tooling: Shopify CLI, VS Code, Claude Code. One Shopify dev store per brand before pushing live.

## Photography

- **Aesthete:** ~£800–£1,500 for proper lifestyle and product shots. Non-negotiable — this segment converts on aesthetic quality.
- **Fitness and combat:** lean on Gemini-generated imagery, stock, and short use-case video clips. ~£100–£300.

## Ads

- **Meta only** for round one. Visual product, all three audiences reachable, fast feedback loop.
- **£500 per store over 2–3 weeks** — £1,500 total ad spend.
- 2–3 creative variants per store, each testing a different hook within the proposition.
- Track CAC, CVR, CTR, cost per add-to-cart, email signups.

## Fulfilment fallback

Orders accepted at full price. When one converts, contact supplier to source the product. If sourcing fails or timing slips materially, full refund with an honest note.

Product page sets expectations clearly: *"Made to order. Ships in 3–4 weeks."*

## Success criteria

Per store, after £500 ad spend:

- **Strong:** CAC under £50–£70, CVR above 1%, repeat add-to-carts, organic signals (saves, DMs, signups)
- **Weak:** No purchases, CVR below 0.3%, no email signups
- **Mixed:** Email signups but no purchases — proposition resonates, but price or offer is wrong

The best-performing segment moves into round two with real inventory and proper fulfilment.

## Timeline

| Week | Focus |
|---|---|
| 1 | Brand directions, domains, dev stores set up, theme scaffolding begun |
| 2 | Build all three stores; commission aesthete photography; supplier conversation |
| 3 | Ad creative, pixel setup, soft launch |
| 4–6 | Run ads, gather data |
| 7 | Review, decide on round two |

## Budget

| Item | Cost |
|---|---|
| Shopify (3 × £25 × 2 months) | £150 |
| Domains | £30 |
| Aesthete photography | £1,000 |
| Other photography and assets | £200 |
| Ad spend | £1,500 |
| Buffer | £300 |
| **Total** | **~£3,200** |

## Open questions to resolve before build

1. Three brand names and visual directions
2. Supplier lead time and minimum viable order size for round two
3. Refund and communication script if sourcing fails on an order
4. Price points per segment (working assumption: £80–£140 fitness, £100–£160 combat, £200–£350 aesthete)

## Round two — provisional

Whichever segment wins:

- Commit to a small first batch of inventory
- Proper fulfilment and packaging
- Begin testing one of the deferred propositions (diaspora or B2B) in parallel
- Consider expanding ad channels beyond Meta if economics support it