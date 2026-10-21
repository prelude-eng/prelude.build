# Prelude

A static landing page built with Astro 7 and Tailwind CSS 4. The approved brief is [brand/landing-page-brief.md](brand/landing-page-brief.md).

Requires Node.js 22.22+ and pnpm.

```sh
pnpm install
pnpm dev
```

The default address is http://localhost:4321. Use the address printed by Astro if the port is occupied. Build with `pnpm build`, then inspect the production output with `pnpm preview`.

## Implementation

- `src/pages/index.astro`: approved page copy, metadata and organisation structured data.
- `src/styles/global.css`: Tailwind theme, local font imports and shared component styles.
- `src/components/`: logo, email action and arrow.
- `public/`: favicon set, social image, manifest, sitemap and deployment header rules.

Fontsource packages supply locally served Inter and JetBrains Mono fonts under the SIL Open Font License; their licences ship in `public/fonts/`. The dotted hero terrain is SVG geometry generated at build time, with CSS motion. All animation is disabled for reduced motion. No client JavaScript is needed. The privacy disclosure is native HTML.

## Before deployment

GitHub Pages deploys automatically on pushes to `main`. See [deployment instructions and GoDaddy DNS records](docs/deployment.md). Astro is configured for the custom domain `https://prelude.build`, with production CSP and referrer-policy metadata. GitHub Pages does not apply `_headers`; the file is retained for other compatible hosts.

The DNS, mailbox, registered company details and privacy wording still need the checks listed in the approved brief.

The sharing image is an original typographic rendering of the approved brand; raster icons derive from `public/favicon.svg`. No stock or generated illustration assets are used.
