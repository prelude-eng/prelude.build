---
name: Prelude
description: Architectural clarity through precise typography and disciplined space.
colors:
  ink: "#0b0f14"
  surface: "#111b27"
  graphite: "#1f2937"
  cloud: "#f8fafc"
  slate: "#94a3b8"
  cyan: "#00d1ff"
typography:
  display:
    fontFamily: "Inter Variable, sans-serif"
    fontSize: "clamp(3.3rem, 7.4vw, 6rem)"
    fontWeight: 600
    lineHeight: 1.04
    letterSpacing: "-0.04em"
  headline:
    fontFamily: "Inter Variable, sans-serif"
    fontSize: "clamp(2rem, 3.4vw, 2.75rem)"
    fontWeight: 600
    lineHeight: 1.16
    letterSpacing: "-0.035em"
  title:
    fontFamily: "Inter Variable, sans-serif"
    fontSize: "21px"
    fontWeight: 550
    lineHeight: 1.4
    letterSpacing: "-0.02em"
  body:
    fontFamily: "Inter Variable, sans-serif"
    fontSize: "17px"
    fontWeight: 400
    lineHeight: 1.65
  supporting:
    fontFamily: "Inter Variable, sans-serif"
    fontSize: "16px"
    fontWeight: 400
    lineHeight: 1.75
  label:
    fontFamily: "JetBrains Mono, monospace"
    fontSize: "11px"
    fontWeight: 500
    lineHeight: 1.5
    letterSpacing: "0.08em"
  signature:
    fontFamily: "JetBrains Mono, monospace"
    fontSize: "23px"
    fontWeight: 600
    lineHeight: 1
    letterSpacing: "-0.055em"
  action:
    fontFamily: "Inter Variable, sans-serif"
    fontSize: "14px"
    fontWeight: 600
    lineHeight: 1.4
rounded:
  button: "3px"
spacing:
  label-gap: "12px"
  copy-gap: "16px"
  action-gap: "24px"
  panel-inset: "32px"
  heading-gap: "44px"
  section-top: "80px"
  section-bottom: "88px"
components:
  button-primary:
    backgroundColor: "{colors.cyan}"
    textColor: "{colors.ink}"
    typography: "{typography.action}"
    rounded: "{rounded.button}"
    padding: "12px 22px"
  button-primary-hover:
    backgroundColor: "{colors.cloud}"
  button-primary-active:
    backgroundColor: "{colors.slate}"
  button-compact:
    backgroundColor: "{colors.cyan}"
    textColor: "{colors.ink}"
    rounded: "{rounded.button}"
    padding: "10px 17px"
  button-secondary:
    backgroundColor: "transparent"
    textColor: "{colors.cloud}"
    typography: "{typography.action}"
    rounded: "{rounded.button}"
    padding: "12px 22px"
  button-secondary-hover:
    backgroundColor: "{colors.surface}"
  section-label:
    textColor: "{colors.slate}"
    typography: "{typography.label}"
  expertise-item:
    textColor: "{colors.cloud}"
    padding: "32px 32px 36px 0"
---

# Design System: Prelude

## Overview

**Creative North Star: "Architectural clarity"**

Architectural clarity expressed through precise typography and disciplined space. Ink and cloud establish a dark, flat reading environment; sparse cyan signals mark actions and orientation. Inter carries the editorial hierarchy, while JetBrains Mono gives the signature and indexing their technical character.

Thin structural rules and generous space organise content. The user-approved dotted cyan mountain adds an abstract point field to the hero; numbered labels remain a deliberate brand commitment. The navigation signature reveals once, and terrain rows ripple slowly. Both are static under reduced-motion preferences.

**Key Characteristics:**

- Dark ink canvas with cloud text and slate supporting copy.
- Sparse cyan for actions, signature, links, focus and section numbers.
- Editorial Inter paired with concise JetBrains Mono indexing.
- Flat, ruled structures with generous responsive spacing.

## Colors

A dark neutral palette gives sparse cyan signals their clarity. The frontmatter preserves the implemented CSS token values.

### Primary

- **Cyan:** Signature suffix, primary actions, section and step numbers, email links, selection, focus outlines and the user-approved hero terrain.

### Neutral

- **Ink:** Continuous page canvas and primary-action text.
- **Surface:** Secondary-action hover background; not a default card fill.
- **Graphite:** Section boundaries, expertise rules and step connectors.
- **Cloud:** Headings, signature prefix and primary-action hover fill.
- **Slate:** Supporting copy, indexing words and metadata; primary-action pressed fill.

**The Cyan Signal Rule.** Reserve cyan for the signature, primary actions, section and step numbers, links, selection, focus and the hero point field. Never use it as a large fill or gradient.

## Typography

Inter Variable is self-hosted for headings, body and actions. Self-hosted JetBrains Mono supplies the signature and labels. The pairing is editorial and precise, with tight heading tracking and open body leading.

### Hierarchy

- **Display:** Two-line hero; the frontmatter describes the desktop role. Below 640px, use the implemented mobile clamp (`clamp(2.75rem, 13.5vw, 3.3rem)`).
- **Headline:** Section headings; the closing invitation uses the larger observed clamp (`clamp(2.2rem, 4.2vw, 3.5rem)`) and line-height (1.15).
- **Title:** Item headings. Situation titles shift to (19px) at 900px and (20px) below 640px. Principles use (17px).
- **Body:** Page and closing copy; below 640px the base becomes (16px). Hero supporting text is (17px), rising to (18px) at 640px, with line-height (1.75) and maximum width (600px).
- **Supporting:** Item descriptions, with generous leading; principle descriptions use (15px).
- **Label:** Lowercase section words and two-digit numbers. Step indexing is (12px) with the same mono family and weight.
- **Signature:** Lowercase `prelude::*`, with cloud prefix and cyan suffix. Below 640px it becomes (21px).
- **Action:** Primary and secondary links. Compact navigation action is (12px), becoming (11px) below 640px.

**The Two Voices Rule.** Inter carries headings and prose. JetBrains Mono carries the lowercase signature and concise indexing.

## Layout

The shared container has maximum width (1200px), with combined horizontal inset (112px). At 900px this becomes (64px); below 640px it becomes (40px). Sections use a numbered gutter (160px), narrowing to (112px) at 900px and stacking above content below 640px. Section padding is (80px 0 88px), then (64px 0), then (46px 0 52px).

Situations use three columns from 768px; expertise uses two from 640px. Approach steps progress from one to two columns at 640px and four at 1024px. Principles place their heading beside the list from 1100px. All collapse in document order. Headings and copy stay left aligned; the hero terrain occupies the right field at 1024px and above, then follows the introduction on smaller screens. Actions wrap with their labels intact.

## Elevation & Depth

The system uses no shadows. The continuous ink canvas, graphite hairlines and whitespace establish structure. Surface appears as an interaction state rather than simulated elevation.

**The Flat Structure Rule.** Use spacing and thin graphite rules to separate content; depth does not rely on shadows.

## Shapes

Buttons have subtly eased corners, defined by the button radius token. Content blocks remain square and open. Borders and connectors are thin (1px); no enclosing card shells are present. Directional arrow icons use a thin stroke (1.5px) and inherit action text colour.

## Components

### Actions

Solid cyan primary links pair ink labels with an inline right arrow. Their minimum height is (52px), with horizontal gap (24px). Hover becomes cloud; pressed becomes slate. The compact masthead version has minimum height (42px), gap (20px), and hides its arrow below 640px. Secondary links are transparent with graphite borders and cloud text; hover adds surface fill and a slate border. Every keyboard target uses a cyan outline (2px) offset by (6px). States change immediately without transition animation.

### Navigation and signature

A single row balances the live-text logo against the compact contact action. Only the masthead suffix types in, once over (400ms) using three steps. Reduced-motion users receive the complete suffix immediately. The footer signature is static. Preserve the literal asterisk.

### Hero terrain

A deterministic build-time SVG point field creates a cyan mountain peak and shoulder, with small slate registration marks. Rows ripple vertically by (5px) in a (7s) ease-in-out CSS cycle. At the user’s request there is no pause control; `prefers-reduced-motion: reduce` disables the animation completely. No JavaScript is used. The desktop landscape occupies (54%) of the hero width with a right offset (-30px), and stacks below the copy below 1024px. It is decorative and hidden from assistive technology. A ruled mono discipline line completes the hero.

### Numbered section labels

A two-digit cyan number, slate separator and lowercase slate word form the orientation device. The label uses the mono role and the label-gap token. It is a confirmed part of the identity.

### Expertise blocks

Open, flat articles use a top graphite rule. On the two-column grid, right-hand blocks add a left divider and left inset (32px). Below 640px they lose that divider and use vertical padding (26px). Supporting text is limited to (43ch).

### Approach steps

Two-digit cyan mono numbers lead into graphite horizontal connectors; titles and supporting text follow. The connector is CSS geometry, not an illustrative image. Steps keep their reading order across the responsive grid.

### Principle rows

A slate two-digit index sits beside a title and supporting sentence. Rows use top graphite rules, vertical padding (23px), index column (24px), and gap (18px), reducing to (10px) on mobile.

### Text links and privacy disclosure

Email links are cyan and reveal an underline on hover. The native Privacy disclosure is slate, turns cloud on hover, and expands into the footer flow; its copy is capped at (72ch) while open. The skip link appears on keyboard focus. No fields, chips, dialogs or form controls are implemented.

## Do's and Don'ts

### Do:

- Do keep the approved dark palette and editorial typography; the dotted hero terrain is a user-approved exception to the original type-only brief.
- Do use numbered mono labels as orientation, with cyan numbers and slate words.
- Do preserve visible cyan focus outlines and immediate signature rendering under reduced motion.
- Do keep content in reading order as grids collapse.

### Don't:

- Don’t add fake terminals, invented code, neon gradients or unapproved decorative imagery outside the dotted hero terrain.
- Don’t use cyan as a large surface fill or replace the asterisk with a star or spark.
- Don’t add blinking cursors, scroll reveals or parallax. Keep motion limited to the logo reveal and slow hero ripple, with reduced-motion support.
- Don’t add shadows or rounded card shells to the existing flat, ruled structures.
