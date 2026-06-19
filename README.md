# From Vibe Coding to Agentic Engineering

A browser-based slide deck (reveal.js) presenting the **Spec-Driven Development (SDD)
framework for GitHub Copilot** — how developers move from "vibe coding" to disciplined
agentic engineering. Designed for a **90-minute** hands-on session for developers.

**Live deck:** https://m-tilab.github.io/from-vibe-coding-to-agentic-engineering-presentation/

## Languages

| File | Language | Direction |
| --- | --- | --- |
| `index.html` | English | LTR |
| `index-fa.html` | فارسی (Persian) | RTL |

The Persian deck keeps technical terms and skill names in English (code identifiers),
with key concepts noted in parentheses, e.g. «کدنویسی شهودی (Vibe Coding)». It uses the
Vazirmatn web font and reveal.js RTL mode; code blocks remain left-to-right.

## Run it

Open `index.html` (English) or `index-fa.html` (Persian) in a browser, or serve locally
(recommended, avoids any CDN/CORS quirks):

```bash
python3 -m http.server 8000
# English: http://localhost:8000/index.html
# Persian: http://localhost:8000/index-fa.html
```

> The deck loads reveal.js from a CDN, so an internet connection is required.

## Presenting

| Key | Action |
| --- | --- |
| `→` / `Space` | Next slide |
| `←` | Previous slide |
| `S` | Open **speaker view** (notes + timer) |
| `F` | Fullscreen |
| `O` | Slide overview |
| `B` | Pause / black screen |

Every slide includes **speaker notes** (talking points) sized to fill the 90 minutes —
view them with `S`.

## Structure

1. The problem — what vibe coding costs
2. The shift — agentic engineering & SDD (with comparison tables)
3. The method — SDD principles & lifecycle
4. The four core skills — `brainstorm → write-spec → implement-epic → verify-epic`
5. Verification & Playwright integration
6. Project knowledge files + advisory agents
7. Documentation system — `init-docs`
8. Live-demo walkthrough
9. Anti-patterns, adoption roadmap, Q&A

## Files

```
index.html        # the deck (English / LTR)
index-fa.html     # the deck (Persian / RTL)
assets/theme.css  # dark GitHub-style theme
assets/rtl.css    # RTL + Persian overrides
```
