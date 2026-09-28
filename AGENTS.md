# AGENTS.md

Guidelines for anyone, human or automated coding agent, who contributes to this repository.

## What this repository is

A historical, preserved personal project: one static page, [`index.html`](index.html), that embeds the X timeline of `@OBaruchML`. It is published with GitHub Pages. See [README.md](README.md).

## Hard rules

1. **Do not modify `index.html`.** It is the original implementation and is preserved byte-for-byte. That means no reformatting, no fixes, no "modernization" and no removal of whitespace.
   - Expected SHA-256: `d9380a23166bf4cb68590cdeafbffc6baa33a69e765e180fd3dd15d5e015aac9`
2. **Do not move or rename `index.html`.** GitHub Pages serves it from the repository root.
3. **Do not add infrastructure** such as build tools, package managers, CI/CD, Docker, linters or test frameworks unless the owner explicitly asks for it.
4. **Do not invent context.** Label statements as *Confirmed*, *Inferred* or *Unknown*.
5. Improvement ideas go in [`docs/possible-improvements.md`](docs/possible-improvements.md), never into the code.

## Working flow (spec-driven)

Before making a change, update the relevant file in `specs/`:

1. [`specs/intent.md`](specs/intent.md): why the change is needed.
2. [`specs/spec.md`](specs/spec.md): what must be true afterwards (requirements and acceptance criteria).
3. [`specs/plan.md`](specs/plan.md): how the change is carried out and verified.

Then make the change on a dedicated branch and open a pull request into `main`.

## Verification before committing

```bash
sha256sum index.html   # must match the hash above
git diff main -- index.html   # must be empty
```

## Style

- Documentation is written in English, in Markdown, with relative links.
- Do not write Liquid template delimiters (a double opening curly brace, or an opening curly brace followed by a percent sign) in Markdown. GitHub Pages runs Jekyll, which would try to parse them.
