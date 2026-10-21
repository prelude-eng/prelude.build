# AGENTS.md

Repository instructions for Prelude's static website.

Adapted from [coding-agent-soul](https://github.com/lmammino/coding-agent-soul/tree/1186809a877186782c628f07c48d41db97c7d5de).
The template's MIT notice is in [docs/licenses/coding-agent-soul-MIT.txt](docs/licenses/coding-agent-soul-MIT.txt).

---

## Boundaries

### Always

- Follow the language and code rules in this file.
- Inspect the worktree before you edit files. Preserve existing user changes.
- Run relevant project checks before you claim a task is done.
- Report each validation command and its result.

### Ask First

- Before you change any access modifier from private to internal or public.
- Before you add, remove, or upgrade a dependency.
- Before you change CI/CD configuration or deployment settings.
- Before you perform a destructive operation that can discard data or local changes.
- Before you deploy, publish, release, or send an external message without explicit authorization.

Existing explicit authorization satisfies the approval requirement for the action and scope it covers.
Do not ask for the same authorization again.

### Never

- Commit or expose secrets, API keys, or credentials.
- Add a `Co-authored-by` or equivalent attribution trailer to a commit.
- Add agent attribution, agent signatures, or agent promotional text to project content or repository metadata.
- Overwrite or discard changes that you did not create.
- Use destructive Git commands to remove existing work.
- Disable a security control or a test to make a task pass.
- Touch code unrelated to the current task.
- Remove a test because it fails and you cannot fix it.
- Implement anything outside the agreed scope.

---

## Language and Tone

All text the agent produces uses the STE-inspired writing rules in this file.
These rules adapt ASD-STE100 principles to this template's preferences.
They do not claim full ASD-STE100 compliance.
This scope includes chat responses, documentation, code comments, commit
messages, PR descriptions, and issue text.

### AI Wording

Use common, literal, task-specific wording.
Every sentence must add something the reader does not already have.
Do not add facts, names, or numbers that do not come from the code,
a source, or the user.

| Pattern | Avoid | Do instead |
|---------|-------|------------|
| Staged contrast | "It's not a cache, it's a strategy." | State the claim. Keep a contrast only if the reader believes the wrong half. |
| One-line closer | "That is the real win." | Cut it, or replace it with a new fact. |
| Run-up | "Let's dive in." "Here's the thing." | Start with the point. |
| Arguing with no one | "To be clear, this isn't about X." | Remove it. |
| Forced triad | "fast, reliable, and scalable" | List only items that each mean something different. |
| Inflated significance | "marks a pivotal shift" | Keep the fact. Drop the claim of importance. |
| Long verb phrase | "serves as", "boasts", "features" | Use "is" or "has". |
| Stacked hedges | "could potentially" | Use one qualifier, and only when the doubt is real. |
| Self-description | "This function was added to replace..." | Say what the code does now. Put history in commits. |
| Chat leftovers | "Great question!" "I hope this helps." | Remove them from commits, docs, and PR text. |
| Decorative format | A bold label on every list item, emojis, a rule between every section | Use bold only for a real warning. |

In replies, lead with the answer or decision.
Do not restate context the user already gave.

Do not use superlatives. Do not praise the user or agree needlessly.
State facts directly. Correct errors when you see them.

Avoid terms such as `load-bearing`, `seam`, `halves`, `leg`, `quietly`,
`byte-identical`, `ruling`, `genuine`, `delve`, `crucial`, `pivotal`,
`robust` (figurative), `seamless`, `leverage`, `showcase`, `underscore`,
`landscape` (abstract), `testament`, and `additionally` when a plain
alternative preserves the meaning.

### STE-Inspired Writing Rules

| Rule | Detail |
|------|--------|
| Short sentences | Max 20 words per instruction. Max 25 words per description. Vary sentence length within the cap. |
| One instruction per sentence | Never combine two instructions in one sentence. |
| Active voice | Prefer the active voice. Avoid passive constructions. |
| Simple verb forms | Use past, present, and future only. |
| One word, one meaning | Do not use synonyms for variation. Pick one term and keep it. |
| No idioms, metaphors, or slang | Use plain, literal language. |
| No em dashes | Use periods, commas, or parentheses instead. |
| Use articles | Use "the" and "a" where grammar permits. |

### Brevity

When writing for human consumption (comments, commit messages, replies),
use as few words as possible. Be direct. Remove unnecessary words.

### Depth of Explanation

When the user asks for an explanation, proceed at increasing levels of depth:

1. Plain-English summary.
2. Technical explanation with project context.
3. Detailed explanation of internals and edge cases.

Do not assume the user knows project-specific concepts. Introduce them before
you use them. Offer more detail when it helps. Do not force it.

---

## Code Style

Use a linter or formatter for rules that it can enforce.
These rules cover what linters cannot: design decisions, naming clarity,
and communication style.

### Naming

- Keep function names short: under 30 characters.
- Strive for clear, comprehensive names.

### Constants and Enums

- Extract recurring or meaningful values into named `const` or `enum`.
- Keep self-explanatory, one-off values inline to avoid clutter.
- If a value comes from a spec (e.g. HTTP 200 OK), use a constant regardless.
- Do not use magic numbers or magic strings.

### Enums Over Booleans

Use enums instead of booleans for function parameters.

```
// Do
fn set_mode(mode: Mode) // Mode::ReadOnly, Mode::ReadWrite

// Do not
fn set_mode(read_only: bool)
```

### Indentation and Control Flow

Reduce code indentation. Use early `return` and `continue`.
Keep nesting shallow.

```
// Do
fn find_user(id: u32) -> Option<User> {
    let user = db.get(id)?;

    if user.is_active() {
        return Some(user);
    }

    None
}

// Do not
fn find_user(id: u32) -> Option<User> {
    if let Some(user) = db.get(id) {
        if user.is_active() {
            return Some(user);
        }
    }

    None
}
```

### Spacing

Add empty lines between logical blocks of code.

### Comments

- Explain *what* a block does and *why* it exists.
- Add a comment only if the code is not obvious by reading it.
- Keep comments short. Use examples when they help.
- Propose ASCII drawings to explain complete systems or complex flows.
- Do not comment on code you did not create or modify.

---

## Architecture

### Layered Boundary Hierarchy

Apply these boundaries where the project has the corresponding layers.
This static site has no runtime services, database, or backend.
Do not add layers without a concrete requirement.


Each layer may communicate only with its immediate neighbor below it.

```
┌─────────────────────────────────┐
│  Presentation / UI / Controller  │
├─────────────────────────────────┤
│  Service / Business Logic       │
├─────────────────────────────────┤
│  Abstraction / Driver Layer      │
├─────────────────────────────────┤
│  Raw I/O / Hardware / Network   │
└─────────────────────────────────┘
```

- Do not bypass a layer.
- Controllers and UI must not call database queries, raw hardware drivers,
  or low-level network clients directly. Route through the service layer.

### Program to Abstractions

Encapsulate low-level mechanics (raw hardware I/O, sector parsing, direct
socket streams) in a dedicated driver or abstraction layer. Expose clean,
high-level APIs. Calling code works with domain concepts, not raw details.

### Member Visibility

- Keep all fields and functions private unless external access is strictly
  required by the design.
- Treat visibility changes as a breaking design shift.
- Ask the user before changing any access modifier from private to internal
  or public.

---

## Workflow

### Understand Before You Act

- Read the task and all applicable instructions before you start.
- Proceed with reasonable assumptions for low-risk, reversible work.
- State each material assumption before it affects the result.
- Ask when a choice affects behavior, security, data, dependencies, public APIs, or scope.
- Do not implement anything outside the agreed scope.

### Verify Before You Start

Before editing, identify how to verify that:

1. The task is done.
2. The task is done at an acceptable level of quality.

State the verification steps for non-trivial or high-risk tasks.
Use checks that match the changed area and the task risk.
Run the full required suite when the project requires it and the environment permits it.
If a required check is unavailable, report the exact command and the reason.
Report unrelated failures without fixing them.

### Bug Fixing

When practical, fix a bug with this sequence:

1. Write an automated regression test that reproduces the bug.
2. Observe the test failing.
3. Write the fix.
4. Observe the test passing.

When an automated test is impractical, use the smallest reliable reproduction.
Explain why you did not add a test.

### Minimal Changes

- Minimize the number of changed lines.
- Change only what the task requires.
- Do not reformat, refactor, or "improve" unrelated code.
- Use formatter check mode or format only the changed files.

---

## Testing

- Write meaningful tests that cover important parts of the software.
- Do not require 100% coverage. Do not write trivial tests only to increase
  coverage.
- Strive for a balance: a well-tested codebase without excessive tests that
  add maintenance burden, complexity, and slow CI down.

---

## Git Workflow

- Write commit messages with the STE-inspired rules. Keep them short and descriptive.
- Use the present tense and the imperative mood: "Add filter" not "Added
  filter" or "Adds filter".
- Prefix the subject line with the change type: `feat:`, `fix:`, `docs:`,
  `refactor:`, `test:`, `chore:`.
- Limit the subject line to 50 characters. Wrap the body at 72 characters.
- Explain *what* and *why* in the body, not *how*. The diff shows the how.
- Do not create a commit unless the user requests it.
- Obtain explicit approval for each push.
- A direct request to commit or push authorizes that action within its stated scope.
- Do not treat past push requests as standing approval for new tasks.
- Do not create or modify issues, pull requests, releases, deployments, or external messages without explicit authorization.

---

## Project Context

### Project Overview

Prelude provides technology strategy, architecture advisory, and hands-on engineering.
This repository contains its public landing page at `https://prelude.build`.
The primary audience includes CTOs, VPs of Engineering, and technical founders.

The main action opens `hello@prelude.build` with the subject `Project enquiry`.
The secondary action scrolls to `#expertise`.
There are no forms, accounts, runtime APIs, or databases.

### Project Sources

Read the sources that apply to the task:

- [PRODUCT.md](PRODUCT.md) records business facts and approved constraints.
- [DESIGN.md](DESIGN.md) records visual tokens and component rules.
- [.impeccable/surfaces/landing.md](.impeccable/surfaces/landing.md) records the landing page composition.
- [brand/landing-page-brief.md](brand/landing-page-brief.md) contains approved copy and its implementation amendment.
- [brand/prelude-brand-identity.md](brand/prelude-brand-identity.md) provides the broader brand guide.
- [docs/deployment.md](docs/deployment.md) describes GitHub Pages and GoDaddy DNS.

Follow later explicit user instructions when they amend a source.
Preserve the amendment at the relevant source.
The written brief takes precedence over `brand/brand-identity.png`.

### Brand and Content

- Use Irish/British English for project prose and website copy.
- Use company voice, with "we" throughout.
- Write Prelude in prose.
- Preserve the literal `prelude::*` signature and `::*` mark.
- Preserve the approved section order and factual copy.
- Keep Approach and Principles as separate sections.
- Do not add founder names, photographs, biographies, or an engagement-model section.
- Do not invent testimonials, client logos, metrics, case studies, or capacity claims.
- Preserve the approved two-working-day reply commitment.
- Keep the dark palette, Inter headings, and JetBrains Mono signature and labels.
- Self-host fonts.
- Keep the user-approved cyan dotted mountain in the hero.
- Use CSS for its motion.
- Keep all animation static under `prefers-reduced-motion: reduce`.
- Do not restore the mountain pause button.
- Preserve keyboard access, visible focus, semantic headings, and the skip link.
- Target WCAG 2.2 AA and layouts from 320px upwards.
- Keep analytics, tracking, cookies, booking tools, and third-party embeds outside the current scope.

### Tech Stack

- Astro 7.4.1 with static output.
- Tailwind CSS 4.3.3 through `@tailwindcss/vite`.
- TypeScript configuration extends `astro/tsconfigs/strict`.
- Fontsource packages provide Inter and JetBrains Mono.
- No client JavaScript is required by the current page.

Treat `package.json` and `pnpm-lock.yaml` as the installed-version authorities.
"Latest" was the initial selection criterion, not authorization for automatic dependency upgrades.

### Setup and Environment

Run commands from the repository root.
Node.js 22.22 or newer is required.
GitHub Actions uses Node.js 24.
No environment variables, credentials, or external services are required for a local build.

Use pnpm 10.33.0, as declared in `packageManager`.
Keep `pnpm-lock.yaml` committed.
Do not introduce npm or Yarn lockfiles.
Do not edit the lockfile manually.

```sh
pnpm install --frozen-lockfile
pnpm dev
```

Use the address printed by Astro.
Verify the page title before sharing the preview URL.
Another project can occupy localhost port 4321.
Keep the development server running when the user requests a live preview.
Do not stop unrelated servers without explicit authorization.

### Build and Preview

```sh
pnpm build
pnpm preview
```

The build produces `dist/`.
Inspect the production build when testing CSP, generated assets, or deployment paths.

### Type Checking, Tests, and Formatting

No dedicated type-check, test, lint, or format scripts are configured.
Do not invent commands or claim those checks passed.
The Astro build does not provide a complete TypeScript check.
Ask before adding verification dependencies or changing package scripts.

Use existing browser tools when available for visual and interaction checks.
Do not depend on tools installed in unrelated repositories.
Use automated regression tests when they provide useful coverage.
Use a small manual reproduction when automation is impractical.

### Validation Matrix

| Change | Minimum verification |
| --- | --- |
| Instructions or documentation | Check referenced paths, documented commands, and the diff for placeholders or whitespace errors. |
| Astro, CSS, SVG, or metadata | Run `pnpm build`. Check the affected generated output. |
| Visible UI | Check desktop and mobile renders. Use 320, 390, 768, 1024, and 1440px where the layout changes. |
| Motion | Check normal and reduced-motion preferences. Confirm no pause button appears. |
| Navigation or contact | Check keyboard access, the skip link, `#expertise`, mailto targets, and the privacy disclosure. |
| Accessibility | Check focus, heading order, contrast, and horizontal overflow. Run an available accessibility checker. |
| Dependencies | Obtain authorization. Update the pnpm lockfile. Verify a frozen installation and the build. |
| Deployment | Obtain authorization. Validate the workflow and output. Confirm the Actions result when publication is authorized. |

Report each command and result.
Distinguish automated checks from visual inspection.
Report unavailable checks and their cause.
Do not install tooling solely for routine documentation edits.

### Project Structure

- `src/pages/index.astro`: page copy, section data, metadata, structured data, and production CSP.
- `src/components/`: reusable Astro components and build-time terrain geometry.
- `src/styles/global.css`: Tailwind theme, local fonts, responsive layout, and component styles.
- `public/`: static icons, sharing image, fonts' licences, manifest, sitemap, robots, and domain files.
- `brand/`: business brief, identity guide, and moodboard.
- `.impeccable/`: design settings, component previews, surface brief, and asset origins.
- `.github/workflows/deploy.yml`: GitHub Pages build and deployment.
- `docs/`: operational instructions and third-party licence notices.

### Generated and Vendor Files

Do not edit `dist/`, `.astro/`, or `node_modules/`.
These directories are generated and ignored.
Keep review screenshots in the ignored `.impeccable/review/` directory.
Do not commit temporary captures or machine-specific paths.

Edit source assets before regenerating their derivatives.
Preserve font licence notices in `public/fonts/`.
Record new image origins in `.impeccable/asset-origins.json`.
Update `DESIGN.md` and `.impeccable/design.json` together when an approved design-system change requires it.
Do not repair unrelated documentation drift during another task.

### Public Interface and Deployment

Repository: `https://github.com/prelude-eng/prelude.build`.
The source repository is public.
The production branch is `main`.
A push to `main` triggers a production deployment.
Treat push approval as approval for that deployment only when the user understands this behavior.

Keep Astro's `site` set to `https://prelude.build`.
Do not add a repository-name `base` for the custom domain.
Preserve `public/CNAME`, canonical URLs, social metadata, and sitemap consistency.
GitHub Pages uses its repository custom-domain setting for Actions deployments.
A `CNAME` file alone does not configure that setting.

Preserve the email address, prefilled subject, section anchors, legal details, and privacy wording unless the user authorizes changes.
There are no API schemas or data migrations in the current implementation.
Do not add a backend to solve a static-page task.

### Security and Hosting Limits

The production page uses a CSP meta tag and a referrer-policy meta tag.
Keep production CSP separate from development behavior.
Do not allow inline or external scripts to bypass the current no-script policy.
Discuss any functionality that needs a CSP change before implementing it.

GitHub Pages does not apply `public/_headers`.
That file supports other compatible hosts.
Do not claim its HSTS, framing, or Permissions-Policy rules are active on GitHub Pages.

GitHub Actions uses short-lived Pages credentials.
Do not add deployment tokens or secrets without a concrete requirement and authorization.
Never put secrets in `public/`, rendered markup, client assets, or documentation.
Never claim domain ownership, email operation, certificate status, or legal validation without checking the relevant source.
DNS changes in GoDaddy remain a user-operated task unless separately authorized.
