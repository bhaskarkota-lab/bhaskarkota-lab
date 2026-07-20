# Setup

This repo powers the `bhaskarkota-lab` GitHub profile page. Everything below is
one-time setup after you push it.

## 1. Repo requirements

- Repo name must exactly match your GitHub username: **`bhaskarkota-lab`**
  (this is what makes `README.md` render on your profile).
- Repo must be **public**.

## 2. Enable workflow write access

Both workflows commit files back to the repo, so Actions needs write
permission:

`Settings → Actions → General → Workflow permissions → Read and write permissions → Save`

## 3. `snake.yml` — contribution snake

Runs daily, regenerates the animated contribution graph, and pushes the SVGs
to an `output` branch. No secrets needed — it works out of the box with the
built-in `GITHUB_TOKEN`.

First run: trigger it manually once from `Actions → Generate contribution
snake → Run workflow`. That creates the `output` branch the README already
points to:

```
https://raw.githubusercontent.com/bhaskarkota-lab/bhaskarkota-lab/output/github-contribution-grid-snake.svg
```

## 4. `metrics.yml` — profile metrics card

Uses [lowlighter/metrics](https://github.com/lowlighter/metrics), which needs
a personal access token (the default `GITHUB_TOKEN` can't read enough about
your account for the `community` and `habits` plugins):

1. Create a **classic** PAT: `Settings → Developer settings → Personal access
   tokens → Tokens (classic)` with scopes `repo` and `read:user`.
2. Add it to this repo as a secret named **`METRICS_TOKEN`**:
   `Settings → Secrets and variables → Actions → New repository secret`.
3. Trigger the workflow once manually to generate the first `assets/metrics.svg`.

## 5. Assets

All visuals live in `assets/` as plain SVG — no external badge services, so
nothing breaks if a third-party API goes down.

| File | Used for |
|---|---|
| `hero.svg` | Top banner |
| `ai-dashboard.svg` | Platform module overview |
| `architecture.svg` | System architecture diagram |
| `roadmap.svg` | Roadmap timeline |
| `footer.svg` | Closing banner |
| `logo.svg` | Small mark, reusable anywhere a favicon-sized logo is needed |
| `background.svg` | Tileable decorative pattern, kept as a raw asset for reuse outside the README (e.g. a social preview image) |

### Design tokens

If you edit or extend an asset, keep it consistent with the rest:

**Palette**
| Token | Hex | Use |
|---|---|---|
| Midnight Navy | `#1B2A4A` | Primary background |
| Navy Deep | `#131F3A` | Panel background |
| Dark Gold | `#B8860B` | Structural lines, rules, borders |
| Gold Light | `#D4A72C` | Emphasis text, core node |
| Emerald | `#0B6E4F` | Secondary accent, module markers |
| Paper | `#F4EFE6` | Primary text on dark |
| Muted Slate | `#7C8CA8` / `#9FB0C8` | Secondary text |

**Type**
| Role | Face |
|---|---|
| Display | `Georgia, 'Times New Roman', serif` |
| Body | `Helvetica, Arial, sans-serif` |
| Data / labels | `Consolas, 'SF Mono', monospace` |

**Signature motif** — filled and outline circles ("answer bubbles"), a nod to
the OMR bubble-sheet exam system at the core of the product. Filled = done or
active; outline = planned. Used in the roadmap markers, the module cards, and
the corner registration marks on the hero/footer.

Fonts are all system/web-safe on purpose — GitHub's SVG sanitizer strips
external font imports, so anything else won't render.

## 6. Personalizing

Search-and-replace if you fork this for someone else:

- `bhaskarkota-lab` → their GitHub username
- The LinkedIn URL in `README.md`
- Name, location, and bio lines in `README.md` and `assets/hero.svg`
- Palette hex values above, if they want a different identity
