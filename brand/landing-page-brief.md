# Prelude — Landing Page Brief

**Version:** 1.0
**Date:** 21 October 2026
**Source:** `prelude-brand-identity.md` (v0.2), refined through a decision interview.
**Scope:** a single-page site at `https://prelude.build`.

> **Implementation amendment — 21 October 2026:** The user subsequently requested a slightly bolder hero with an animated dotted neon mountain abstraction based on the moodboard. This overrides the original type-only hero, rejected dotted landscape and logo-only motion decisions below. Preserve the approved copy, palette, fonts and other sections. The user then explicitly requested no pause button: animation remains static whenever reduced motion is preferred. Hosting is GitHub Pages at prelude.build. The original decisions remain below as history.

Where `brand-identity.png` (the moodboard) and the written guide disagree, **the written guide wins**. Treat the moodboard as mood only: dark surfaces, sparing cyan, mono labels, numbered sections.

---

## 1. Locked decisions

| Topic | Decision |
|---|---|
| Voice | "We" throughout. Present a company, not individuals. |
| People | No founder names, photos, or bios. |
| Proof | None yet. No testimonials, client logos, metrics, case studies, or placeholders that imply them. |
| Services | The four areas from the guide, described briefly, with no depth or capacity claims. |
| Audience | CTOs, VPs of Engineering, and technical founders at growing companies. |
| Primary CTA | "Start a conversation" → `mailto:hello@prelude.build?subject=Project%20enquiry` |
| Secondary CTA | "Explore our expertise" → scrolls to `#expertise` |
| Email | `hello@prelude.build` (alias to the founder's mailbox). |
| Location | Not mentioned on the page. Remote-first is a working preference, not page copy. |
| Spelling | Irish/British English (organisations, modernisation, optimisation). |
| Theme | Dark only. No light mode in v1. |
| Hero visual | Type only. No illustration, photo, or abstract graphic. |
| Motion | One moment: `::*` types in after `prelude` in the nav logo on load (~400ms, once). Disabled under `prefers-reduced-motion`. |
| Analytics | None in v1. No cookies, no cookie banner. |

### Moodboard elements explicitly rejected

- `prelude.engineering` domain → use `prelude.build`
- US spelling and San Francisco address → Irish entity, British English
- "Complex systems build a brighter future." → hype; violates the writing rules
- Dotted-wave landscape imagery → decorative, unrelated to content
- `let what's_next = together();` → invalid code; no invented code as decoration
- Geometric-sans hero logotype → the logotype is monospace
- Palette names/values from the image → use the token table below

### Decision log

Each decision, the options considered, and why. "Confirmed" means you chose it explicitly. "Default" means Claude proposed it and you didn't object; revisit those first if anything feels off.

| # | Topic | Decision | Alternatives considered | Rationale | Status |
|---|---|---|---|---|---|
| D1 | Moodboard vs guide | The written guide wins on every conflict; the image is mood only | Follow the image | The image contradicts the guide's own rules (domain, spelling, hype copy, invalid code, decorative imagery) | Default |
| D2 | Who Prelude is | In practice a solo founder plus occasional trusted freelancers | — | — | Confirmed |
| D3 | Voice | "We", presented as a company | "I"; named founder up front | Gives a stronger company impression, and the business may grow | Confirmed |
| D4 | People on the page | No founder names, photos or bios | Named founder with a bio and public work as proof | Keep the focus on the company | Confirmed |
| D5 | Proof | None for now; keep it general. No placeholders that imply proof | Testimonials, logos, metrics | No verified evidence exists yet | Confirmed |
| D6 | Services | General, based on the four areas in the brand guide | Detailed offers with depth or capacity claims | Avoids overpromising capacity | Confirmed |
| D7 | Primary audience | CTOs, VPs of Engineering and technical founders at growing companies | Platform teams, business leaders, all four audiences equally | They buy architecture advice and delivery help | Confirmed |
| D8 | Client triggers | Three situations with equal weight, in this order: hard-to-change system, consequential decision, stalled delivery | Lead with a single trigger | You didn't pick one to lead | Default |
| D9 | Conversion mechanism | `mailto:hello@prelude.build` with a prefilled subject `Project enquiry` | Booking link (Cal.com/Calendly); contact form | Simplest to run for now | Confirmed (subject prefill: Default) |
| D10 | Email | `hello@prelude.build`, an alias forwarding to `luciano@prelude.build` | `contact@` | — | Confirmed |
| D11 | Target market | Teams across Europe and beyond | — | — | Confirmed |
| D12 | Location on page | Not mentioned anywhere in the copy | A quiet "based in Ireland" line | Your preference | Confirmed |
| D13 | Working model | Remote-first, raised in conversation and not stated on the page | On-site / hybrid | — | Confirmed |
| D14 | Footer legal details | Prelude Engineering Limited · no. 828717 · 90 Leinster Road, Rathmines, Dublin 6, D06 F3P4, Ireland | — | Irish company law disclosure requirement (confirm with your accountant) | Confirmed (address formatting: Default) |
| D15 | Page outline | Nav, hero, when, what, how, why, closing CTA, footer | Fewer sections | Covers positioning, situations, services, method and beliefs | Confirmed |
| D16 | Approach vs Principles | Keep both as separate sections | Merge them into one | Your preference | Confirmed |
| D17 | "How we engage" section | Left out of v1 | Engagement models / pricing section | Reads as padding without pricing or proof; add once you know which engagement shapes sell | Confirmed |
| D18 | Headline | "Systems for what's next." | — | The primary brand line | Confirmed |
| D19 | Hero subline | Option A, the guide's version tightened | B: buyer-facing "independent… engineers who still build"; C: shortest | Your preference | Confirmed |
| D20 | Logotype rendering | JetBrains Mono SemiBold as live text or SVG until custom artwork exists | The geometric-sans version from the moodboard | The guide specifies a monospace logotype | Default |
| D21 | Theme | Dark only | Dark + light following the system setting | Keeps v1 simple; one palette to tune | Confirmed |
| D22 | Hero visual | Type only | Big cropped `::*` mark; abstract architecture diagram | Most restrained; the copy and typography do the work | Confirmed |
| D23 | Motion | One moment: `::*` types in on the nav logo, once, respecting reduced motion | None; scroll reveals | Brand moment with no noise | Confirmed |
| D24 | Approach illustration | Thin four-step line (understand → decide → build → hand over) | No visual; full diagram | Shows the content honestly; not decoration | Confirmed |
| D25 | Section copy | Approved as drafted (section 3) | — | — | Confirmed |
| D26 | Reply-time promise | "We'll reply within two working days" stays | Different timeframe; no promise | Approved as is; this is a commitment to keep | Confirmed |
| D27 | Analytics | None in v1, so no cookie banner | Cookieless (Plausible, EU-hosted); Google Analytics with consent | Your preference | Confirmed |
| D28 | Headline font | Inter 600–700; mono reserved for the logo and labels | All-mono headlines | Long mono headlines are harder to read; matches the guide's "bold editorial headlines, concise mono labels" | Default |
| D29 | Font hosting | Self-host JetBrains Mono and Inter | Google Fonts CDN | Keeps the "no tracking" privacy statement true | Default |
| D30 | SEO title and description | As in section 5 | — | Reuses the approved hero copy | Default |
| D31 | Page language | `en-IE` | `en`, `en-GB` | Irish company, Irish/British spelling | Default |
| D32 | Privacy note | A short footer-linked note (section 3) | No note | Emails contain personal data | Default (needs review by someone qualified) |

### Notes for later

- **Light mode:** if added, `cyan` `#00D1FF` on white is only about 1.8:1, so it needs a darker accent for text and links (around `#0077A3`), checked for contrast.
- **Analytics:** if added later, the preferred option is cookieless and EU-hosted (Plausible or similar) with one custom event on the `mailto:` CTA, which still means no cookie banner. Update the privacy note to match.
- **Proof:** once verified client outcomes exist, revisit D4 and D5. A named senior person and real case studies are the strongest trust signals for advisory work.
- **Booking link:** revisit D9 if email back-and-forth becomes a bottleneck.

---

## 2. Page structure

```
nav        prelude::*                                [Start a conversation]
01 hero    Systems for what's next. + subline + CTAs
02 when    When teams bring us in — 3 situations
03 what    What we do — 4 expertise areas          (id="expertise")
04 how     How we work — 4 steps with a thin connecting line
05 why     Principles — 5 decision principles
06 cta     Closing invitation + email
footer     legal details · privacy · © 2026 · ::*
```

Section labels are small mono labels in the form `02 / when`, number in `cyan`, word in `slate`.

---

## 3. Copy (approved)

### Nav

- Logo: `prelude::*` (links to top)
- Button: **Start a conversation**

No other nav links. The page is short enough to scroll.

### 01 — Hero

> # Systems for what's next.
>
> Technology strategy and architecture advisory, backed by hands-on engineering. We help you make sound technical decisions and turn them into dependable systems.
>
> **[Start a conversation]**  [Explore our expertise]

### 02 / when — When teams bring us in

**Your system has become hard to change.**
Costs creep up, releases slow down, and every change touches more than it should. We find where the complexity lives and plan a realistic path to improve it.

**A consequential technical decision is on the table.**
A platform choice, a migration, a build-or-buy call. We pressure-test the options, make the trade-offs explicit and give you a recommendation you can defend.

**The plan exists, but delivery has stalled.**
You know where you want to go but lack the time or specialist capacity to get there. We work alongside your team to put the approach into practice.

### 03 / what — What we do

**Technology strategy & advisory**
Architecture reviews, technology selection, modernisation roadmaps and technical due diligence, with the reasoning written down.

**Software & systems architecture**
Distributed systems, APIs and service boundaries designed for reliability, performance and future change.

**Cloud & platform engineering**
Cloud-native and serverless design, infrastructure as code, observability and cost control for production platforms.

**Hands-on delivery**
Prototypes, targeted implementation and engineering alongside your team, with documentation and knowledge transfer built in.

### 04 / how — How we work

Rendered as four steps joined by a thin `graphite` rule, with step numbers in `cyan` mono.

1. **Understand.** Your goals, your constraints, and the system as it actually runs.
2. **Decide.** The options and their trade-offs, a clear recommendation, and a record of why.
3. **Build.** Implementation alongside your engineers, adjusting as evidence comes in.
4. **Hand over.** Documented decisions and a team that can run and evolve what was built.

### 05 / why — Principles

1. **Understand before prescribing.** Constraints and outcomes come first.
2. **Keep the essentials in scope.** Attention goes where it changes a decision.
3. **Choose the simplest adequate architecture.** Complexity has to earn its place.
4. **Make expertise transferable.** We explain our reasoning and document our decisions.
5. **Build for the next change.** Design for how the system will be operated and evolved.

### 06 — Closing CTA

> ## Have a decision to make or a system to untangle?
>
> Tell us what you're working on. We'll reply within two working days.
>
> **[Start a conversation]** · or email hello@prelude.build

### Footer

```
prelude::*                                          Privacy

Prelude Engineering Limited · Registered in Ireland, no. 828717
Registered office: 90 Leinster Road, Rathmines, Dublin 6, D06 F3P4, Ireland
© 2026 Prelude Engineering Limited
```

### Privacy note

A short section or page linked from the footer. Suggested text:

> **Privacy.** This site sets no cookies and uses no analytics or tracking. If you email us, we use your name, address and message only to reply and to discuss potential work, and we keep them only as long as needed for that purpose. Data controller: Prelude Engineering Limited, 90 Leinster Road, Rathmines, Dublin 6, D06 F3P4, Ireland. Contact: hello@prelude.build.

Have this reviewed by someone qualified before relying on it.

---

## 4. Visual system

### Colour tokens (dark only)

| Token | Hex | Use |
|---|---|---|
| `ink` | `#0B0F14` | Page background |
| `surface` | `#111B27` | Cards, raised panels |
| `graphite` | `#1F2937` | Borders, rule lines, dividers |
| `cloud` | `#F8FAFC` | Headings, body text |
| `slate` | `#94A3B8` | Secondary text, mono labels, metadata |
| `cyan` | `#00D1FF` | `::*`, primary button fill, focus rings, section numbers, links |

Rules:
- Cyan is a signal. Use it on `::*`, the primary button, focus states, section numbers and links only. Never use it as a large fill or gradient.
- Primary button: `cyan` background, `ink` text. Secondary button: transparent, `graphite` border, `cloud` text.
- Check every real text/background pair against WCAG 2.2 AA before launch. Approximate ratios: `cloud`/`ink` ≈ 18:1, `slate`/`ink` ≈ 7.5:1, `cyan`/`ink` ≈ 11:1, `ink`/`cyan` (button) ≈ 11:1.

### Typography

| Role | Font | Notes |
|---|---|---|
| Logotype | JetBrains Mono SemiBold | `prelude` in `cloud`, `::*` in `cyan`, lowercase, no space before `::*` |
| Headlines | Inter, weight 600–700 | Tight tracking (≈ -0.02em), editorial scale |
| Body | Inter, weight 400 | 17–18px base, line-height ≈ 1.6, max ≈ 68ch |
| Labels / section numbers | JetBrains Mono, weight 500 | Small, uppercase or lowercase consistently, letter-spacing ≈ 0.08–0.12em |

Both fonts are SIL OFL. **Self-host them** (no Google Fonts CDN), so no visitor data goes to a third party and the no-tracking privacy statement holds.

### Logo usage on the page

- Nav: `prelude::*` as live text or inline SVG, ≈ 20–22px.
- Footer: `prelude::*` smaller, plus the standalone `::*` if desired.
- The asterisk stays an asterisk. No star, spark or compass substitutes.
- `prelude::*` is a graphic signature only. In running copy, write **Prelude**.

### Layout and supporting visuals

- Generous whitespace and a disciplined grid that feels like good technical documentation.
- Thin `graphite` rule lines between sections.
- Expertise and situation items as simple blocks or `surface` cards. Icons are optional; if used, use thin-line icons in `slate`, never cyan-filled.
- No fake terminals, code screenshots, circuit boards, binary, neon gradients or stock photography.

### Motion

- The only animation: `::*` appears after `prelude` in the nav logo on first load (~400ms, once).
- Under `prefers-reduced-motion: reduce` it renders immediately.
- No blinking cursor, no scroll-triggered reveals, no parallax.

---

## 5. Metadata and assets

### SEO / sharing

```html
<html lang="en-IE">
<title>Prelude — Technology strategy and architecture advisory</title>
<meta name="description" content="Technology strategy and architecture advisory, backed by hands-on engineering. Sound technical decisions, turned into dependable systems.">
<link rel="canonical" href="https://prelude.build/">
<meta property="og:title" content="Prelude — Systems for what's next.">
<meta property="og:description" content="Technology strategy and architecture advisory, backed by hands-on engineering.">
<meta property="og:url" content="https://prelude.build/">
<meta property="og:type" content="website">
<meta property="og:image" content="https://prelude.build/og.png">
<meta name="twitter:card" content="summary_large_image">
<meta name="theme-color" content="#0B0F14">
```

Add `Organization` JSON-LD with legal name `Prelude Engineering Limited`, brand name `Prelude`, URL, email, and address.

### OG image (1200 × 630)

`ink` background, `prelude::*` logotype centred-left, "Systems for what's next." beneath in `slate` or `cloud`. Nothing else.

### Favicon set (`::*` mark)

- `favicon.svg`: `::*` in `cyan` on transparent (or on an `ink` rounded square if it reads poorly on light browser tabs).
- `favicon.ico` (16 + 32), `apple-touch-icon.png` (180, on `ink`), `icon-192.png` / `icon-512.png` for the manifest.
- Keep the structure: four dots (two colons) and one asterisk. Test at 16, 24, 32, 64 and 128px.

---

## 6. Quality bar

The site's quality is itself evidence of engineering standards.

- WCAG 2.2 AA: contrast, visible `cyan` focus rings, keyboard navigation, semantic landmarks, a skip link, a sensible heading order.
- Fast: static HTML/CSS, minimal or no JS, subsetted self-hosted fonts, Lighthouse ≥ 95 in every category.
- Secure headers (CSP, HSTS, Referrer-Policy) and HTTPS only.
- Responsive from 320px up, no horizontal scroll.

---

## 7. Out of scope for v1

- Light mode
- Analytics and cookie banner
- Contact form or booking link
- Case studies, testimonials, client logos, founder/team section
- "How we engage" / engagement models and pricing
- Insights/blog, additional pages

## 8. Before launch

- [ ] `prelude.build` registered, DNS and HTTPS configured
- [ ] `hello@prelude.build` alias receiving mail
- [ ] Footer company details checked against the CRO record
- [ ] Privacy note reviewed
- [ ] Contrast checked on the built page, not just swatches
- [ ] Favicon tested at real sizes
- [ ] OG image previewed on LinkedIn and Slack
