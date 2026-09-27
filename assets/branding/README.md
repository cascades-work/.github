# Cascades brand assets

This directory is a **published consumption copy** of the Cascades brand asset
set. It exists so GitHub and GitLab profile repositories and per-repository
READMEs have a stable, public URL to reference for logos, favicons, banners, and
social icons. It is **not** the source of truth.

## Canonical source

The canonical source of Cascades brand assets and design tokens is the
[`cascades-design`](https://github.com/cascades-work/cascades-design) repository:

| Concern | Canonical path in `cascades-design` |
|---------|-------------------------------------|
| Logo / mark / glyph / monogram / wordmark (SVG) | `src/assets/logos/` |
| Favicon set (SVG, PNG, `.ico`, apple-touch, safari-pinned) | `src/assets/favicons/` + `scripts/generate-favicon.mjs` |
| Original design source files (raster/editor exports) | `src/assets/logos-source/` |
| Color tokens | `src/tokens/colors.ts` |
| Typography tokens | `src/tokens/typography.ts` |
| Other tokens (spacing, radii, shadows, motion, materials) | `src/tokens/` |
| Compiled CSS (tokens, themes, typography) | `src/css/` (published to `dist/css/`) |

## Relationship (do not drift)

This tree is **generated from** `cascades-design` and copied here for
consumption. The two repositories are kept in sync by the following contract:

1. **Edit only upstream.** Brand assets and design tokens are authored in
   `cascades-design` under `src/assets/` and `src/tokens/`. Do not hand-edit the
   SVGs in this directory as if they were canonical.
2. **Publish downstream.** After an upstream change, regenerate raster
   derivatives (PNG sizes, favicons, banners) from the upstream SVGs and copy the
   result into `assets/branding/` here and into the mirroring `gitlab-profile`
   repository so the two profile trees stay identical.
3. **Treat this as read-only output.** Any divergence between this tree and
   `cascades-design` is drift and should be corrected by re-publishing, not by
   patching here.

## Asset provenance

| Asset | Origin |
|-------|--------|
| `logo/*.svg` | Verbatim from `cascades-design` `src/assets/logos/` |
| `logo/*-*.png` | Raster derivatives rendered from the upstream SVGs |
| `watermark/` | Monochrome mark on a transparent square canvas, derived from the upstream monogram geometry |
| `favicon/` | Monogram-derived; mirrors `cascades-design` `src/assets/favicons/` |
| `social/repository-banner.png`, `header-banner.png` | Pre-existing approved Cascades banners (`banner.png`, `hero-banner.png`) |
| `social/social-card.png` | 1200×630 Open Graph card derived from the repository banner |
| `social/icons/` | Third-party social glyphs; see `social/icons/README.md` |

## Design tokens

The canonical color tokens live in `cascades-design` `src/tokens/colors.ts`.
Relevant values referenced by these assets:

- `coal` `#101316` — dark mark background / primary ink
- `ink` `#080a0c` — deepest surface
- `cyan` `#2ed8e7` — accent used in the logo terminal stroke
- `text` `#ffffff` / light strokes `#f2f2f2` — mark on dark

Typography uses **Schibsted Grotesk** (see `cascades-design`
`src/tokens/typography.ts`). Do not substitute a different typeface when
regenerating raster wordmark/logo derivatives.
