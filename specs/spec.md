# Specification

[← Back to README](../README.md) · Previous: [intent.md](intent.md) · Next: [plan.md](plan.md)

> An as-built specification, reconstructed from `index.html` at commit `abecefd`. Each requirement is traced to the code. Requirements are **Confirmed** unless marked otherwise.

## 1. Functional requirements

| ID | Requirement | Evidence in `index.html` |
|---|---|---|
| FR-1 | The page embeds the public timeline of `@OBaruchML`. | `<a class="twitter-timeline" href="https://twitter.com/OBaruchML?...">` |
| FR-2 | The timeline is rendered by X's official embed widget. | `<script async src="https://platform.twitter.com/widgets.js">` |
| FR-3 | The widget uses the dark theme. | `data-theme="dark"` |
| FR-4 | The widget hides its header, footer and borders, and uses a transparent background. | `data-chrome="noheader nofooter noborders transparent"` |
| FR-5 | The widget is sized at 500 × 600 px, and the timeline scrolls internally. | `data-width="500"`, `data-height="600"` |
| FR-6 | If the widget does not load, a fallback link "Tweets by OBaruchML" to the profile stays visible. | Anchor text content |

## 2. Presentation requirements

| ID | Requirement | Evidence |
|---|---|---|
| UI-1 | The page background is dark `#0d1117`. | `body { background-color: #0d1117; }` |
| UI-2 | The feed card is centered horizontally and vertically in the viewport. | `display:flex; justify-content:center; align-items:center; height:100vh` |
| UI-3 | The card has a `1px #30363d` border, a `12px` radius and a drop shadow, and clips its content. | `.twitter-feed { ... }` |
| UI-4 | The card is fluid up to 500 px wide. | `max-width: 500px; width: 100%` |
| UI-5 | The page is mobile-aware. | `<meta name="viewport" content="width=device-width, initial-scale=1.0">` |
| UI-6 | The browser tab title is "Baruch's X Feed". | `<title>` |

## 3. Non-functional characteristics

| ID | Characteristic | Status |
|---|---|---|
| NF-1 | Static, single-file delivery with no build step. | Confirmed |
| NF-2 | Non-blocking script load. | Confirmed (`async`) |
| NF-3 | No custom JavaScript, cookies or storage of its own. Any tracking comes from X's widget. | Confirmed for the page itself |
| NF-4 | Hosted on GitHub Pages. | Pages enabled: Confirmed. Source and URL: Inferred |
| NF-5 | Works in current browsers without the visitor being signed in to X. | **Unknown**: depends on X's current embed policy |

## 4. Interfaces

- **Inbound:** HTTP GET of `index.html` (GitHub Pages or local file).
- **Outbound:** `platform.twitter.com` (script) and X's widget iframe/content endpoints, which the script controls.
- **Configuration:** none. All values are hard-coded in the markup.

## 5. Acceptance criteria (as built)

1. Opening `index.html` shows a dark page with a centered, rounded card.
2. With network access and a working X embed, the card shows the `@OBaruchML` timeline in dark mode with no widget header or footer.
3. Without the widget, the card shows the link "Tweets by OBaruchML".

## 6. Repository documentation spec (reorganization)

| ID | Requirement |
|---|---|
| DOC-1 | `index.html` is unchanged (SHA-256 `d9380a23166bf4cb68590cdeafbffc6baa33a69e765e180fd3dd15d5e015aac9`) and stays at the root. |
| DOC-2 | The README explains the overview, context, structure, technologies, how it works, how to run it and the historical note. |
| DOC-3 | Every claim in the docs is labeled Confirmed, Inferred or Unknown where it is not self-evident from code. |
| DOC-4 | Improvement ideas live only in `docs/possible-improvements.md` and are marked as not applied. |
| DOC-5 | No build, CI, container or tooling infrastructure is added. |
