# Twitter Feed

A single-page website that embeds the public X (formerly Twitter) timeline of the account [@OBaruchML](https://twitter.com/OBaruchML) inside a dark, centered card.

> **Original implementation notice**
> This repository preserves the original implementation of the project. The source code has intentionally not been refactored or modernized in order to retain the historical context and original development approach. The source code represents the original implementation developed as a personal project.

---

## Project Overview

The whole project is one static HTML file, [`index.html`](index.html). When it opens in a browser, it loads X's official embed script (`widgets.js`). That script turns a plain link to the `@OBaruchML` profile into an interactive timeline widget. Inline CSS centers the widget on a dark background, with a rounded border and a drop shadow.

## Project Context

| Aspect | Status | Details |
|---|---|---|
| Project origin | **Personal Project** (Inferred) | No course, assignment or institutional material exists in the repository. The page embeds the author's own social account, which points to a personal utility or portfolio piece. |
| Author | Confirmed | All commits are authored by Baruch Lopez (GitHub: `OBaruch`). |
| Development date | Confirmed | 21 June 2025 (three commits within about 11 minutes; see [version history](docs/version-history.md)). |
| Hosting | Partially confirmed | GitHub Pages is enabled for the repository. The exact published URL and source branch are not recorded in the repository. |
| Intended consumer | Unknown | It is not documented whether the page was meant to be visited directly or embedded somewhere else (for example, in an `<iframe>` on a portfolio site). |

More detail: [docs/project-context.md](docs/project-context.md).

## Problem Statement

*(Inferred)* Show the author's latest X posts on a standalone web page that is easy to host and share, and that matches a dark, GitHub-like visual style. Doing this with X's official embed widget avoids any backend, API keys or build tooling.

## Objective

Create a minimal, zero-dependency static page that:

1. embeds the `@OBaruchML` timeline with X's official widget;
2. uses a dark theme with no widget header, footer or border;
3. centers the feed in the viewport as a single card, at most 500 px wide.

## Repository Structure

```
twitter-feed/
├── index.html                 # Original implementation (unchanged, served by GitHub Pages)
├── README.md                  # This file
├── AGENTS.md                  # Contribution guardrails for humans and AI coding agents
├── .gitignore
├── docs/
│   ├── project-context.md     # Origin, scope and evidence (Confirmed / Inferred / Unknown)
│   ├── code-overview.md       # Line-by-line explanation of index.html
│   ├── version-history.md     # Reconstruction of the three original iterations
│   └── possible-improvements.md  # Suggestions that were deliberately NOT applied
└── specs/
    ├── intent.md              # Why the project exists (reverse-engineered)
    ├── spec.md                # What the project does (requirements as implemented)
    └── plan.md                # How it was built, plus how this repository was reorganized
```

`index.html` stays at the repository root on purpose. GitHub Pages serves `index.html` from the root of the publishing source, so moving it into a folder such as `src/` could break the published page.

## Original Implementation

`index.html` is byte-for-byte identical to the last commit made by the author (`abecefd`, 21 June 2025). Its markup, styles, formatting (including trailing whitespace) and embed attributes are all preserved as written. Any improvement ideas are listed separately in [docs/possible-improvements.md](docs/possible-improvements.md) and have **not** been applied.

## Technologies

| Technology | Usage |
|---|---|
| HTML5 | Page structure (`<!DOCTYPE html>`, `lang="en"`, responsive viewport meta tag) |
| CSS3 (inline `<style>`) | Flexbox centering, rounded card, shadow, dark background |
| X (Twitter) for Websites – Embedded Timeline | `https://platform.twitter.com/widgets.js`, loaded asynchronously |
| GitHub Pages | Static hosting (enabled on the repository) |

The project has no JavaScript of its own, no frameworks, no package manager and no build step.

## How It Works

```
Browser loads index.html
        │
        ├── Inline CSS paints a dark (#0d1117) full-viewport flex container
        │
        ├── <div class="twitter-feed"> renders a centered card (max 500px)
        │       └── <a class="twitter-timeline" data-*> ... fallback link to @OBaruchML
        │
        └── <script async src="platform.twitter.com/widgets.js">
                └── finds a.twitter-timeline and replaces it with an <iframe>
                    that shows the timeline (dark theme, 500×600, no chrome)
```

If the widget script cannot load (it is blocked, the user is offline, or the platform changed), the visitor still sees the plain fallback link "Tweets by OBaruchML".

See [docs/code-overview.md](docs/code-overview.md) for a full explanation.

## Inputs and Outputs

- **Input:** none at build time. At runtime the only "input" is the hard-coded profile URL `https://twitter.com/OBaruchML`.
- **Output:** a rendered web page containing the embedded timeline.

## Running the Project

There is nothing to install or build.

- **Locally:** open `index.html` in a web browser. The page needs internet access to download `widgets.js` and the timeline content.
- **Hosted:** the repository has GitHub Pages enabled. Under GitHub's default project-site URL scheme, the page would be at `https://obaruch.github.io/twitter-feed/`. *(Inferred; the Pages configuration is not stored in the repository.)*

> **Note:** How well embedded timelines render depends on X's current platform policies, which have changed several times since 2023. The original repository does not provide enough information to determine whether the embed still renders today without the visitor being signed in.

## Documentation

- [Project context](docs/project-context.md)
- [Code overview](docs/code-overview.md)
- [Version history](docs/version-history.md)
- [Possible improvements (not applied)](docs/possible-improvements.md)
- Specs: [intent](specs/intent.md) · [spec](specs/spec.md) · [plan](specs/plan.md)
- [Contribution guardrails](AGENTS.md)

## Historical Note

This repository was later reorganized and documented to improve readability and preserve the historical context of the original project. The original source code remains unchanged. Everything except `index.html` (README, `docs/`, `specs/`, `AGENTS.md`, `.gitignore`) was added afterwards as documentation.
