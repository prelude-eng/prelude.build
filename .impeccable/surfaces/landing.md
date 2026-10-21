# Landing page

Mode: Persuade. Route: /.

Authority: brand/landing-page-brief.md, amended by the user's 21 October 2026 request for a slightly bolder hero with an animated dotted neon mountain. That request supersedes the type-only/no-landscape and logo-only-motion decisions. Other brief constraints remain in effect.

THESIS: Architectural clarity expressed through precise typography and disciplined space.
OWN-WORLD: Ink and cloud, sparse cyan signals, Inter editorial headings, JetBrains Mono signature and indexing. Thin structural rules and flat surfaces. A cyan dotted terrain is a specific hero exception requested by the user.
STORY: What Prelude does → when to bring us in → expertise → approach → principles → email invitation.
FIRST VIEWPORT: A compact masthead and oversized two-line headline with a narrow supporting paragraph and paired actions. A cyan dotted mountain occupies the right field on desktop; on smaller viewports it follows the introduction. A thin ruled discipline line grounds the hero. Text stays clear of the terrain.
FORM: A shared numbered gutter anchors the sections. Situations read across three columns; expertise is a two-by-two ruled grid; approach connects four steps; principles read as a compact list beside their heading. All collapse in reading order on mobile.

Signature interaction: the navigation logo suffix types on once in about 400ms. Build-time SVG terrain rows ripple gently in a seven-second CSS cycle. The user explicitly requested no pause control; reduced-motion users always receive a static landscape and complete signature. No client JavaScript is needed.
Risk: With no client proof available, the typography and clarity of the page bear the credibility burden. Avoid adding fabricated evidence to compensate.
Build: Code-first, explicitly chosen by the user. Astro static output, deployed to GitHub Pages using the custom domain prelude.build.
