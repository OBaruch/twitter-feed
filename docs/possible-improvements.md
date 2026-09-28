# Possible Improvements

[← Back to README](../README.md)

> **None of the items below have been applied.** They are listed only for reference. To preserve the original implementation, `index.html` has deliberately not been refactored, corrected or modernized.

## Robustness

| Observation | Possible improvement |
|---|---|
| The page depends entirely on X's embed platform. Since 2023, embedded timelines have been restricted and may require the visitor to be signed in, or may not render at all. | Add a visible fallback message or a link to the profile when the widget fails. If a reliable feed matters, consider a server-side or static alternative. |
| `widgets.js` is loaded without a pinned version or Subresource Integrity (SRI). | Accept this as inherent to X's widget (X does not publish versioned builds), or self-host a static snapshot of the posts. |
| `height: 100vh` on `body` with a fixed 600 px widget can clip content or misbehave on short or mobile viewports (for example, with dynamic browser toolbars). | Use `min-height: 100vh` (or `100dvh`) and add vertical padding. |

## Modernization

| Observation | Possible improvement |
|---|---|
| It uses `twitter.com` URLs and "Tweets" wording. | Switch to `x.com` URLs and "Posts" wording, if X's embed code supports them. |
| `data-width="500"` duplicates the CSS `max-width: 500px`. | Keep a single source of truth for the width. |
| `data-lang` was removed in v3. | Add `data-lang="en"` back so the widget language does not depend on the visitor's locale. |
| The visible heading from v2 was removed. | For accessibility, add a visually hidden `<h1>` or an `aria-label` to the feed region. |

## Repository / hosting

| Observation | Possible improvement |
|---|---|
| The GitHub repository description is just `.`. | Set a meaningful description and the homepage URL in the repository settings. |
| The GitHub Pages configuration is not documented in code. | Confirm the Pages source (branch and folder) in the repository settings and record the published URL in the README. |
