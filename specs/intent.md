# Intent

[← Back to README](../README.md) · Next: [spec.md](spec.md) → [plan.md](plan.md)

> These specs were **reverse-engineered** from the existing repository after the fact. They describe the project as it was built. They are not a plan for new features. Labels: **Confirmed** / **Inferred** / **Unknown** (see [project-context.md](../docs/project-context.md)).

## 1. Original project intent

### Why

*(Inferred)* Baruch Lopez wanted a simple, shareable web page that shows the latest posts from the X account [@OBaruchML](https://twitter.com/OBaruchML). The visual style is dark and minimal, consistent with GitHub's dark theme. The page should need no backend, credentials or maintenance.

### Who

| Stakeholder | Need |
|---|---|
| Author (Baruch Lopez) | Publish their X activity somewhere they control, such as a portfolio or personal page. *(Inferred)* |
| Visitors | See recent posts in a clean, readable card without leaving the page. *(Inferred)* |

### Outcome

A single static `index.html`, hosted on GitHub Pages *(Pages enabled: Confirmed)*, that renders the timeline in a centered dark card.

### Constraints the author appears to have chosen

- Zero build tooling and zero custom JavaScript. **Confirmed** by the code.
- Rely on X's official embed widget, not the X API. **Confirmed**.
- Keep everything in one file with inline CSS. **Confirmed**.

### Non-goals (Inferred from what is absent)

- Authentication, API access or server-side rendering.
- Multiple accounts, filtering or custom post rendering.
- Analytics, tests or deployment pipelines.

## 2. Intent of the repository reorganization

This covers the later documentation work, which is separate from the original project.

- **Why:** keep the project as a readable, honest portfolio artifact.
- **What:** add documentation (README, `docs/`, `specs/`, `AGENTS.md`, `.gitignore`) that explains the original implementation.
- **Hard constraint:** `index.html` must stay **byte-for-byte unchanged and at the repository root**, so the GitHub Pages deployment keeps working.
- **Principle:** modernize the repository, not the project.
