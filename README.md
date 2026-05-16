# mudgar-stores

A monorepo for the **mudgar smoke test**: three separate Shopify storefronts, each
testing a distinct proposition for selling mudgars (Indian clubs) in the UK.

> **Stage:** smoke test. No real inventory yet. Full refunds if sourcing fails.

---

## The three stores

Each store is a forked & customised copy of Shopify's [Dawn](https://github.com/Shopify/dawn) theme,
pushed to its own Shopify store. The folder names below are stable internal
identifiers — actual brand names are decided per-store and live in [`docs/brands.md`](docs/brands.md).

| Folder | Dev store | Segment | Angle |
| --- | --- | --- | --- |
| `themes/fitness/` | `mudgar-strong-shoulders.myshopify.com` | Functional fitness | Shoulder durability, grip strength. Offset weight & thick handles train what dumbbells can't. |
| `themes/combat/`  | `mudgar-combat-sports.myshopify.com`    | Combat sports (BJJ / MMA / wrestling) | Pehlwani heritage, shoulder injury prevention, grip for gi work. |
| `themes/aesthete/`| `mudgar-aesthetic.myshopify.com`        | Conscious living | Ritual, craft, beautiful hardwood object for daily practice. |

---

## Repo layout

```
mudgar-stores/
├── themes/
│   ├── aesthete/      # Dawn fork — conscious-living store
│   ├── fitness/       # Dawn fork — functional-fitness store
│   └── combat/        # Dawn fork — combat-sports store
├── shared/            # Reusable snippets, design tokens, pattern notes
├── docs/
│   ├── plan.md        # Overall smoke test plan
│   ├── brands.md      # Brand directions per store
│   ├── suppliers.md   # Supplier contacts & lead times
│   └── decisions.md   # Running log of key decisions
└── README.md
```

### `themes/<store>/` vs `shared/`

- **`themes/<store>/`** — everything that expresses a single store's identity:
  Liquid templates, sections, store-specific snippets, assets (CSS, JS, images),
  copy, settings. This is what Shopify CLI actually pushes to the store.
- **`shared/`** — anything we want to keep in sync across stores: design tokens
  (spacing, type scales, base colours), reusable Liquid snippets that aren't
  brand-specific, pattern notes, and shared documentation. **Nothing in
  `shared/` is auto-pulled into themes** — when a shared snippet is adopted by
  a store, it's copied into that store's theme. The folder is a library, not a
  symlink target.

Rule of thumb: if changing it should change all three stores at once, it's
*shared*. If it expresses brand voice or visual identity, it's *per-store*.

---

## Working with a store locally

### Prerequisites (install once)

- **Node.js** ≥ 18 LTS (20 LTS recommended). Check with `node -v`.
- **Shopify CLI** (installed globally via npm):
  ```bash
  npm install -g @shopify/cli @shopify/theme
  ```
- A **Shopify Partner account** with a development store per brand.

### Day-to-day commands

All commands are run from inside a specific theme folder. Example for the fitness store:

```bash
cd themes/fitness

# Start a local dev server with hot reload, served against the dev store
shopify theme dev --store mudgar-strong-shoulders.myshopify.com

# Pull the latest live theme down (overwrites local — be careful)
shopify theme pull --store mudgar-strong-shoulders.myshopify.com

# Push local changes up to the dev store as an unpublished theme
shopify theme push --store mudgar-strong-shoulders.myshopify.com --unpublished

# Run theme-check linter
shopify theme check
```

Equivalent stores for the other two folders:

| Folder | `--store` value |
| --- | --- |
| `themes/combat/`   | `mudgar-combat-sports.myshopify.com` |
| `themes/aesthete/` | `mudgar-aesthetic.myshopify.com` |

The first time you run any of these, Shopify CLI will open a browser to
authenticate you against the store. Auth state is cached in `~/.config/shopify/`,
not in this repo.

---

## Branching convention

- **`main`** — stable. Only merged work that's been reviewed in a dev store.
- **`<store>-dev`** — active work on a single store (e.g. `fitness-dev`,
  `combat-dev`, `aesthete-dev`). Push freely; merge into `main` when a chunk
  of work is done and pushed live.
- **`shared-dev`** — for changes touching `shared/` that will then be pulled
  into multiple stores.

Keep one store's `-dev` branch focused on that store. If a change touches more
than one store, do it on `shared-dev` first, then propagate.

---

## Decision log

All non-obvious decisions (theme structure, brand naming, supplier choices,
pivots) get a line in [`docs/decisions.md`](docs/decisions.md). Cheap to write,
priceless when you're three months in and can't remember why you did something.
