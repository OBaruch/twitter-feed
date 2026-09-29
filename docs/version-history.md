# Version History

[← Back to README](../README.md)

The project evolved over three commits on 21 June 2025 (UTC-6), all by Baruch Lopez. This page reconstructs each iteration from git history. It is useful for seeing the design decisions, since the final file keeps only the last version.

| # | Commit | Time | Message | Summary |
|---|---|---|---|---|
| 1 | `7b87f9d` | 20:45 | Create index.html | Bare embed |
| 2 | `9e4a580` | 20:55 | Update index.html | Light theme with a heading |
| 3 | `abecefd` | 20:56 | Update index.html | Dark, chrome-less card (**current**) |

## v1: Bare embed (`7b87f9d`)

- Title: "Twitter Feed".
- No styles. It contains only the default embed snippet from X's publish tool: an `<a class="twitter-timeline">` link to `@OBaruchML` plus `widgets.js`.
- Establishes the core mechanism that every later version keeps.

## v2: Light, headed layout (`9e4a580`)

- Title: "Tweets by @OBaruchML". Adds a viewport meta tag.
- Light page (`#f9f9f9`) with a `system-ui` font and `2rem` padding. The content is stacked in a column.
- Visible `<h1>` "Tweets by @OBaruchML" in Twitter blue (`#1DA1F2`).
- Wraps the widget in `.feed-container` with a light shadow and 12 px rounded corners.
- Widget options: `data-lang="en"`, 500 × 500.

## v3: Dark, chrome-less card (`abecefd`, current)

- Title: "Baruch's X Feed". This reflects the Twitter → X rebrand.
- Dark GitHub-style palette (`#0d1117` background, `#30363d` border). The card is centered in the full viewport (`height: 100vh`).
- The `<h1>` is removed. The wrapper is renamed `.feed-container` → `.twitter-feed`, with a stronger shadow and a 500 px max width.
- Widget options: `data-theme="dark"`, 500 × 600, `data-chrome="noheader nofooter noborders transparent"`. `data-lang` is dropped.

## Design trajectory (Inferred)

The changes point in one direction: from a default embed to a **minimal, dark, self-contained card with no header**. That kind of card fits well inside another page (for example, through an `<iframe>`) or matches a dark portfolio aesthetic. The repository does not state which of these was the goal.
