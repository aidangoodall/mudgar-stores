# Decision log

A running record of decisions that shape the project. Append-only — if a
decision is later reversed, add a new entry rather than editing the old one.

**Format:** one entry per decision.

```
## YYYY-MM-DD — <short title>
**Decision:** what was decided.
**Rationale:** why, including alternatives considered.
**Impact:** what this changes downstream (optional).
```

---

## 2026-05-16 — Dawn baselines land on `main`
**Decision:** All three Dawn forks are committed to `main` as an unmodified
baseline (one shared commit, three folders). Per-store customisation happens
on `fitness-dev` / `combat-dev` / `aesthete-dev` branches off that commit.
**Rationale:** Keeps the three baselines in lockstep, makes pulling future
Dawn upstream releases tractable (one merge into `main`, then merge `main`
back into each `-dev` branch), and lets anyone cloning fresh see all three
stores side by side.
**Impact:** Treat the baseline commit as scaffolding, not stable work — the
"main = reviewed/published" rule from the README applies to customisations
made *on top of* the baseline, not the baseline itself. Dawn source:
https://github.com/Shopify/dawn (cloned with `--depth=1`, history stripped).

## 2026-05-16 — Shopify dev store handles
**Decision:** The three Shopify development stores are named:
- `mudgar-strong-shoulders.myshopify.com` → `themes/fitness/`
- `mudgar-combat-sports.myshopify.com`    → `themes/combat/`
- `mudgar-aesthetic.myshopify.com`        → `themes/aesthete/`

**Rationale:** Descriptive handles map cleanly to each segment without locking
in a customer-facing brand name (which is still TBD per store). Folder names
stay generic; the Shopify-side handle carries the segment hint.
**Impact:** Customer-facing domains and brand names will live separately from
these dev store handles. The `.myshopify.com` URL is only used during build.

## 2026-05-16 — Monorepo for three smoke-test stores
**Decision:** Manage all three stores (`fitness`, `combat`, `aesthete`) in a
single git repo, with one Dawn fork per store under `themes/<store>/` and a
`shared/` folder for cross-store assets.
**Rationale:** Three stores share a product (mudgars) and most engineering
concerns. A monorepo makes it cheap to lift patterns between stores and keeps
the smoke test's parallel structure visible. Cost of splitting later is low if
one brand graduates beyond the smoke test.
**Impact:** Shopify CLI commands are run from inside each `themes/<store>/`
folder, not from the repo root.
