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
