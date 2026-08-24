# cam-coming-soon — the holding page for CAM

The **coming-soon page** for *Computationally Assisted Metacognition* (CAM) — CIS 7000-008, University of Pennsylvania, Fall 2026, taught by Jérémie Lumbroso, Practice Assistant Professor of Computer and Information Science.

A single `index.html`, no build step, official Penn Engineering branding served from [`penn-engineering-web-assets`](https://jlumbroso.github.io/penn-engineering-web-assets/). Adapted from [`jlumbroso/penn-engineering-coming-soon`](https://github.com/jlumbroso/penn-engineering-coming-soon).

## How this repo relates to `cam-website`

Two repos, one domain, and **the `CNAME` file is the switch** — Jérémie's established pattern across prior courses:

| Repo | Holds | `CNAME` |
|---|---|---|
| **this one** (`cam-coming-soon`) | the holding page | ✅ currently owns `metacognition.computer` |
| [`cam-website`](https://github.com/jlumbroso/cam-website) | the real Hugo course site | ⏳ takes the domain at cutover |

**To cut over** (listing day): delete `CNAME` here and push, then add `CNAME` in `cam-website` and push. GitHub refuses to serve one custom domain from two repositories, so the order matters — release before claim.

**To roll back**: reverse it. That is the point of the split — if the full site goes wrong on the day it matters, the fallback is a DNS-level flip, not a debugging session.

## Editing

Everything is a CSS variable at the top of `index.html`, under `CUSTOMIZATION SECTION`:

```css
--course-name:      "Computationally Assisted Metacognition";
--course-code:      "CIS 7000-008 · Fall 2026";
--timeline:         "Details announced when the course is listed";
--contact-email:    "lumbroso@seas.upenn.edu";
--show-tagline:     none;   /* deliberate — see below */
--show-description: none;   /* deliberate — see below */
```

GitHub Pages redeploys on push to `main`.

### What is deliberately not on this page

The course description, the learning outcomes, and the course's tagline exist, but they are not here. They live in the course's private deliberation repo and have not been approved to cross to a public surface; they arrive with the full site. This is a standing rule for this repo, not an oversight.

### One thing to watch

The section number `CIS 7000-008` is the department's stated intent as of 2026-08-24 ("I think we would be listing the course at CIS 7000-008"), not a confirmed registrar record. If it changes, it is a one-line edit here.

## Provenance

Built by **Portico 5** (Claude Opus 5), the rendering-layer seat of the CAM crew, 2026-08-24. Reasoning recorded as ADR-0002 in the course's deliberation repo.

Carries one upstream fix: the coming-soon template's mailto script tested the wrong element (`.contact-email` *is* the `<a>`, not its parent), so every page built from it shipped a dead `href="mailto:"`. Fixed here with an explanatory comment, plus a hard-coded `mailto:` in the markup so the link survives with JavaScript off. Worth porting back to [`penn-engineering-coming-soon`](https://github.com/jlumbroso/penn-engineering-coming-soon).
