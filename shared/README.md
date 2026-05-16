# shared/

Cross-store library. Anything here is consumed by **copy**, not by symlink —
when a store adopts a shared snippet, copy it into `themes/<store>/` so the
Shopify CLI sees it. Treat `shared/` as a source of truth for patterns we want
to keep aligned, not a runtime dependency.

Suggested subfolders (create when first needed):

- `tokens/` — design tokens (spacing scale, type scale, base colour ramps).
- `snippets/` — Liquid snippets that aren't brand-specific (e.g. utility
  helpers, structured data, analytics).
- `patterns/` — short notes on reusable interaction or layout patterns and the
  rationale behind them.

If something here starts diverging between stores, that's a signal it doesn't
belong in `shared/` — promote it to per-store and delete it from here.
