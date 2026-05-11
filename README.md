# @mentronig/tokens

Single source of truth for the Mentronig brand tokens. Used portfolio-wide by Web apps, Print artefacts, Mermaid diagrams, and AI-UI surfaces to keep the brand visually consistent.

## What is in here

| File | Purpose |
|------|---------|
| `src/colors.css` | CSS Custom Properties for all 7 Mentronig colors. Drop-in for any CSS framework or raw HTML. |
| `src/tailwind-preset.css` | Tailwind v4 `@theme` block. Import via `@import "@mentronig/tokens/src/tailwind-preset.css"` in your `globals.css`. |
| `src/index.css` | Barrel that re-exports `colors.css` and `tailwind-preset.css`. |
| `src/index.ts` | TypeScript constants for non-CSS consumers (Mermaid, JS-driven diagrams, design tokens in JS code). |

## Token reference

| Token | Hex | Role |
|-------|-----|------|
| Deep Base | `#141928` | Primary background (60-70% of surface) |
| Lead Cyan | `#00FFFF` | Primary accent (10-15% of surface, focus, active state) |
| Phase Orange | `#FFA032` | Warnings, risks, highlighted heuristics |
| Success Green | `#00FF78` | Success, go-live, completion |
| Text Primary | `#E6E6E6` | Body copy. Never use pure white. |
| Text Muted | `#64748B` | Metadata, captions, secondary labels |
| Table Divider | `#1E293B` | Borders and dividers in dark surfaces |
| Accent Purple | `#C084FC` | Tertiary accent for Onboarding-Doku-Pattern. **Never interactive** -- Lead Cyan stays primary. Since 0.2.0. |
| Chapter 01 | `#C084FC` | Chapter colour 01 in Onboarding-Doku multi-color palette. Since 0.2.0. |
| Chapter 02 | `#FBBF24` | Chapter colour 02. Since 0.2.0. |
| Chapter 03 | `#60A5FA` | Chapter colour 03. Since 0.2.0. |
| Chapter 04 | `#EF4444` | Chapter colour 04. Since 0.2.0. |
| Chapter 05 | `#22C55E` | Chapter colour 05. Since 0.2.0. |

> **Pattern scope:** The chapter palette is structural, not interactive. Use only for chapter headers, sub-chapter badges and bullets in onboarding and training documentation. Do not use as a general interaction accent — that role stays with Lead Cyan. See vault `00 Kontext/Branding-Guide.md` section "Onboarding-Doku-Pattern" and reference mockup `sandbox/webDesignProject/mockups/aria-curriculum-style/` for the full pattern definition.

## Install

The package is published to GitHub Package Registry. Configure your project root with an `.npmrc`:

```
@mentronig:registry=https://npm.pkg.github.com
```

For private consumers, add a personal access token with `read:packages`:

```
//npm.pkg.github.com/:_authToken=${GITHUB_TOKEN}
```

Then install:

```
pnpm add @mentronig/tokens
```

## Use

### Tailwind v4

In your `globals.css`:

```css
@import "tailwindcss";
@import "@mentronig/tokens/src/tailwind-preset.css";
```

Then use the tokens as utilities: `bg-deep-base`, `text-text-primary`, `border-lead-cyan`.

### Plain CSS

```css
@import "@mentronig/tokens/src/colors.css";

.element {
  background: var(--color-deep-base);
  color: var(--color-text-primary);
  border-color: var(--color-lead-cyan);
}
```

### TypeScript

```ts
import { colors } from "@mentronig/tokens";

const accentHex = colors.leadCyan; // "#00ffff"
```

## Versioning

Semver. The package is in `0.x` until the first portfolio-wide consumer (DomainForge + ARIA) ships against it. The first `1.0.0` release marks portfolio-stable token contract.

## Publishing

Publishes happen automatically via GitHub Actions on push to `main` when `src/**` or `package.json` change. See `.github/workflows/publish.yml`.

## License

MIT. See `LICENSE`.
