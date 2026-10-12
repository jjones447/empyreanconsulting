# Empyrean Consulting website

Static source for `https://empyreanconsulting.com/`. The root page presents the software-development practice; the previous consulting page is retained at `/about/`.

## Current hosting

The production domain is served by GitHub Pages from `jjones447/empyreanconsulting` `main` at the repository root. `CNAME` supplies the custom domain. A merge to `main` can publish immediately; review branches and pull requests are **not** production deployments. Do not merge a design draft merely to obtain a preview.

Cloudflare account access does not mean this site is deployed on Cloudflare Pages. Any hosting move needs a separate plan covering DNS, mail, verification records, the integration policy URLs, and rollback. The static website is not an OAuth callback or token store.

## Source map

| Path | Purpose |
| --- | --- |
| `index.html` | Software-development homepage. |
| `about/index.html` | Preserved consulting practice page, with links adjusted for its new location. |
| `assets/site.css` | Homepage styling. |
| `assets/logo-gear.png`, `assets/logo-full.png` | Existing brand assets. |
| `integrations/index.html` | Internal Google integration information and links to separate QuickBooks pages. |
| `integrations/privacy/index.html` | Google integration privacy notice. |
| `integrations/quickbooks/index.html` | EVI EIP Books information. |
| `integrations/quickbooks/privacy/index.html` | EVI EIP Books privacy notice. |
| `integrations/quickbooks/terms/index.html` | EVI EIP Books terms. |
| `CNAME` | GitHub Pages custom domain. |

The QuickBooks integration pages identify Empyrean LLC as publisher and EVI as the separate company whose books may be connected. The static pages do not imply that a production QuickBooks API connection is live.

## Draft review

Open `index.html` and `about/index.html` directly for a source-level preview where the local browser permits it. Relative links are used throughout. Check desktop and mobile widths, keyboard navigation, About content, and all integration links before approving a merge. Do not edit the published integration policy pages as a side effect of a homepage change.
