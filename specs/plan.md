# Plan

[← Back to README](../README.md) · Previous: [spec.md](spec.md)

> Part 1 reconstructs how the original project was built, using git history. Part 2 is the plan used to reorganize and document the repository. It was carried out without touching the original code.

## Part 1: Original implementation (reconstructed)

All steps are **Confirmed** by commits on 2025-06-21 (UTC-6). Details are in [version-history.md](../docs/version-history.md).

| Step | Commit | Work | Requirements introduced |
|---|---|---|---|
| 1. Scaffold the embed | `7b87f9d` (20:45) | Paste X's default embed snippet into a bare HTML page. | FR-1, FR-2, FR-6 |
| 2. First styling pass | `9e4a580` (20:55) | Add a viewport meta tag, a light theme, an `<h1>`, a wrapper card, and a 500×500 widget with `data-lang="en"`. | UI-5 (plus later-removed items) |
| 3. Final dark card | `abecefd` (20:56) | Switch to a dark GitHub-style palette, center the card in the viewport, remove the heading, and set the widget to dark, chrome-less, 500×600. | FR-3–FR-5, UI-1–UI-4, UI-6 |
| 4. Publish | n/a | Enable GitHub Pages on the repository. | NF-4 (enabled: Confirmed; exact timing and config: Unknown) |

## Part 2: Repository reorganization

### Guardrails

- Do not modify, move, rename or reformat `index.html`. Check its SHA-256 before and after.
- Do not add build, CI, container, lint or test infrastructure.
- Do not invent context. Label claims as Confirmed, Inferred or Unknown.
- Write all documentation in English.

### Tasks

| # | Task | Output | Status |
|---|---|---|---|
| 1 | Inventory every file and every commit. Read repository metadata (Pages flag, description, dates). | Findings in `docs/project-context.md` | Done |
| 2 | Classify the project origin from evidence. | Personal Project (Inferred) | Done |
| 3 | Decide the structure. Keep `index.html` at the root because of GitHub Pages. Add only the folders that are needed (`docs/`, `specs/`). No `src/`, `data/` or `assets/`, since there is no such content. | Structure in the README | Done |
| 4 | Write the README. | `README.md` | Done |
| 5 | Explain the code without changing it. | `docs/code-overview.md` | Done |
| 6 | Reconstruct the iteration history. | `docs/version-history.md` | Done |
| 7 | List improvement ideas separately, marked as not applied. | `docs/possible-improvements.md` | Done |
| 8 | Write the reverse-engineered intent, spec and plan. | `specs/` | Done |
| 9 | Add contributor and agent guardrails and a minimal `.gitignore`. | `AGENTS.md`, `.gitignore` | Done |
| 10 | Verify: `index.html` hash unchanged, relative links resolve, no Liquid-breaking syntax for the GitHub Pages Jekyll build. | Checks run before commit | Done |
| 11 | Open a pull request from a dedicated branch into `main`. | PR | Done |

### Verification

```bash
sha256sum index.html
# expected: d9380a23166bf4cb68590cdeafbffc6baa33a69e765e180fd3dd15d5e015aac9

git diff main -- index.html   # expected: empty
```

### Deliberately not done

Everything listed in [possible-improvements.md](../docs/possible-improvements.md).
