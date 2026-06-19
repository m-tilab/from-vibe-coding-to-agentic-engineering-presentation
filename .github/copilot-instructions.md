# Copilot instructions

This repository is a static reveal.js slide deck for the talk **From Vibe Coding to Agentic Engineering**. Keep changes focused on presentation content, speaker notes, and static assets.

## Project structure

- `index.html` is the English/LTR deck.
- `index-fa.html` is the Persian/RTL deck.
- `assets/theme.css` contains the shared dark GitHub-style theme.
- `assets/rtl.css` contains Persian/RTL-specific overrides.
- `SDD-Framework.md` is source/reference material for the SDD framework.

## Editing guidelines

- Preserve the static setup: do not introduce a build step, package manager, frontend framework, or generated output unless explicitly requested.
- Keep reveal.js loaded from the existing CDN links unless the task specifically asks to vendor or upgrade it.
- Maintain valid, semantic HTML and the existing slide pattern:
  - slides are `<section>` elements inside `<div class="slides">`;
  - nested `<section>` groups create vertical slide stacks;
  - speaker notes live in `<aside class="notes">`.
- When changing deck content, update the matching language surface when appropriate:
  - English presentation content in `index.html`;
  - Persian/RTL presentation content in `index-fa.html`;
  - Persian speaker-note translations embedded in `index.html` should remain in `dir="rtl"` blocks.
- Preserve code identifiers, tool names, skill names, commands, and product names in English even in Persian text.
- For Persian content, keep RTL layout intact and leave code blocks, commands, URLs, and identifiers left-to-right.
- Reuse existing CSS classes and visual patterns before adding new ones.
- Keep copy concise and presentation-friendly; prefer short slide bullets with richer detail in speaker notes.

## Validation

- For content or CSS changes, open or serve the deck locally and check both `index.html` and `index-fa.html`.
- Use the existing local server pattern when needed:

  ```bash
  python3 -m http.server 8000
  ```

- Confirm speaker notes still open with reveal.js speaker view (`S`) when making structural slide changes.
