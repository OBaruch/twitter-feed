# Code Overview

[← Back to README](../README.md)

The project has one source file: [`index.html`](../index.html) (45 lines, about 1 KB). This document explains it without changing it.

## Files

| File | Role | Original? |
|---|---|---|
| `index.html` | The whole application: markup, styles and the embed script tag | Yes (unchanged) |
| Everything else | Documentation added later | No |

## Structure of `index.html`

### 1. Document head (lines 1–26)

| Element | Purpose |
|---|---|
| `<!DOCTYPE html>` / `<html lang="en">` | HTML5 document in English. |
| `<meta charset="UTF-8">` | UTF-8 encoding. |
| `<title>Baruch's X Feed</title>` | Browser tab title. |
| `<meta name="viewport" ...>` | Scales correctly on mobile devices. |
| `<style>` block | All presentation rules (see below). |

### 2. Styles

**`body`**

| Property | Value | Effect |
|---|---|---|
| `background-color` | `#0d1117` | Dark background (same hex as GitHub's dark theme canvas). |
| `font-family` | `'Segoe UI', Tahoma, Geneva, Verdana, sans-serif` | System font stack. Mainly affects the fallback link text, because the widget renders inside its own iframe. |
| `display: flex` + `justify-content: center` + `align-items: center` | – | Centers the card horizontally and vertically. |
| `height` | `100vh` | The body fills the viewport, so vertical centering works. |
| `margin` | `0` | Removes the browser's default body margin. |

**`.twitter-feed`** (the card wrapper)

| Property | Value | Effect |
|---|---|---|
| `border` | `1px solid #30363d` | Subtle border (GitHub dark border color). |
| `border-radius` | `12px` | Rounded corners. |
| `overflow` | `hidden` | Clips the widget iframe to the rounded corners. |
| `max-width` / `width` | `500px` / `100%` | Fills the width on small screens, capped at 500 px. |
| `box-shadow` | `0 10px 30px rgba(0,0,0,0.4)` | Soft drop shadow that lifts the card. |

### 3. Body (lines 27–45)

```html
<div class="twitter-feed">
  <a class="twitter-timeline" data-theme="dark" data-width="500" data-height="600"
     data-chrome="noheader nofooter noborders transparent"
     href="https://twitter.com/OBaruchML?ref_src=twsrc%5Etfw">
    Tweets by OBaruchML
  </a>
</div>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
```

*(Reformatted above for readability only. The original file keeps its own formatting.)*

The `<a class="twitter-timeline">` anchor is X's standard embed "placeholder". Its `data-*` attributes configure the widget:

| Attribute | Value | Meaning |
|---|---|---|
| `data-theme` | `dark` | Dark widget color scheme. |
| `data-width` | `500` | Widget width in pixels. |
| `data-height` | `600` | Widget height in pixels. The timeline scrolls inside this box. |
| `data-chrome` | `noheader nofooter noborders transparent` | Hides the widget header, footer and border, and makes its background transparent so the page styling shows through. |
| `href` | `https://twitter.com/OBaruchML?ref_src=twsrc%5Etfw` | The profile whose timeline is embedded. `ref_src` is the referral tag that X's embed generator adds. |

### 4. Execution flow

1. The browser parses the HTML and applies the inline CSS.
2. Until the widget loads, the anchor shows as a plain link: **"Tweets by OBaruchML"**.
3. `widgets.js` downloads asynchronously (`async`), so it does not block rendering.
4. When it runs, the script finds every `a.twitter-timeline`, reads its `data-*` options, and replaces it with an `<iframe>` from X that shows the timeline.
5. The `.twitter-feed` wrapper clips and decorates that iframe.

## External dependencies

| Dependency | Loaded from | Version pinning |
|---|---|---|
| X for Websites widget script | `https://platform.twitter.com/widgets.js` | None. It always loads X's current version. |

## Observed characteristics (documented, not changed)

- The file has no custom JavaScript, build step or configuration.
- Two lines in the anchor tag have trailing whitespace (`<a ` and `class="twitter-timeline" `). They are kept as authored.
- It uses `twitter.com` URLs and the `twitter-*` class naming, not `x.com`. This matches the embed code X still generated at the time.

See [possible-improvements.md](possible-improvements.md) for optional suggestions. None have been applied.
