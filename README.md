# StoryBlue — Storyline Blueprint

> **AI-powered pre-authoring pipeline for Articulate Storyline 360 developers**

StoryBlue turns a rough storyboard into a production-ready blueprint — before you open Storyline. It runs entirely in the browser as a single HTML file. No install, no server, no account.

---

## What it does

Paste your storyboard text, choose a learning theory, and StoryBlue runs a 5-stage AI pipeline that produces:

| Stage | Output |
|-------|--------|
| 1 — Ingest | Quality analysis of your storyboard — gaps, confidence, interaction types detected |
| 2 — Slide Plan | Scene/slide map with interaction types, layer counts, branch flags, and theory tags |
| 3 — Variables & Triggers | Named variable register + full trigger architecture per slide |
| 4 — Branching Validator | Structural validation of all branch paths — dead ends, missing feedback, theory violations |
| 5 — Export Blueprint | Copyable, downloadable blueprint document with build checklist |

Everything is editable at each stage before proceeding. The pipeline adapts to your chosen learning theory.

---

## Quick start

1. **Download** [`storyline-blueprint.html`](./storyline-blueprint.html)
2. **Open** it in Chrome or Edge (local file, no server needed)
3. Click **Settings** → paste your API key (Claude, OpenAI, or Gemini)
4. Paste your storyboard → select a theory → click **Analyse Storyboard**

> ⚠️ Do not open the file inside the Claude artifact preview — API calls are blocked there. Always open the downloaded file directly in your browser.

---

## Supported AI providers

| Provider | Model | Key format |
|----------|-------|-----------|
| **Anthropic Claude** (recommended) | claude-sonnet-4-5 | `sk-ant-...` |
| OpenAI | gpt-4o | `sk-...` |
| Google Gemini | gemini-2.0-flash | `AI...` |

API keys are stored in browser session memory only — never persisted to disk or sent anywhere except the AI provider.

---

## Learning theories included

60 theories across 8 categories, in 3 integration tiers:

- 🔵 **Tier 1 — Full pipeline integration**: theory rules applied across all 5 stages
- 🟡 **Tier 2 — Stage 2 tagging**: theory used for slide tagging and coverage mapping
- ⚪ **Tier 3 — Context only**: theory informs the AI's overall framing

**Categories**: ID Models · Evaluation · Motivation · Constructivist · Experiential · Cognitive · Multimedia · Adult Learning

Flagship Tier 1 theory: **Gagné's Nine Events of Instruction** — includes event coverage chart, event-specific variable and trigger rules, and branching validation checks.

---

## Files in this repo

| File | Description |
|------|-------------|
| `storyline-blueprint.html` | The tool — open this in your browser |
| `sample-storyboard.txt` | 18-slide test storyboard (*Data Privacy at Work*) — paste into Stage 1 to test the full pipeline |
| `testing-guide.txt` | Step-by-step test guide — what to enter at each stage and what to look for |

---

## Testing the pipeline

Use the included sample storyboard for an end-to-end test:

1. Open `storyline-blueprint.html` in Chrome
2. Add your API key in Settings
3. Copy the contents of `sample-storyboard.txt` and paste into Stage 1
4. Select **Gagné's Nine Events** as primary theory, **Cognitive Load Theory** as secondary
5. Follow the `testing-guide.txt` for expected outputs at each stage

The sample course covers: branching scenario (3 paths + retry loop), scored quiz (5 questions), 8+ named variables, merge paths, and all 9 Gagné events.

---

## Stage 4 — Branch path form

Stage 4 asks you to confirm branch destinations before the AI validates. This is intentional — you know your course structure. For the sample storyboard, enter:

**Branch node S2.2:**
- Path 1: `S2.3` — Forward without checking (risky)
- Path 2: `S2.5` — Verify vendor first (correct)
- Path 3: `S2.7` — Escalate to manager (partial)

**Branch node S3.7:**
- Path 1: `completion` — Pass (≥80%)
- Path 2: `S3.1` — Fail, retry

---

## Storyline variable naming convention

StoryBlue enforces Storyline best-practice naming throughout:

```
n prefix → Number     e.g. nQuizScore, nAttempts_Q1
b prefix → True/False e.g. bScenarioPassed, bVisited_S3
s prefix → Text       e.g. sUserChoice, sLastAnswer
camelCase · no spaces · underscore for grouping
```

---

## Known limitations

- **Download button**: blocked inside the Claude artifact preview. Works when the file is opened directly in a browser tab.
- **Large storyboards**: very long storyboards (>5,000 words) may approach token limits. Split into scenes if needed.
- **No persistence**: the pipeline state lives in memory. Refreshing resets everything — by design.
- **CORS on Claude API**: requires the `anthropic-dangerous-direct-browser-access: true` header, which is already set in the tool.

---

## Built with

- Vanilla HTML/CSS/JS — zero dependencies, single file
- Articulate Storyline 360 conventions throughout
- Prompt architecture designed for structured JSON output contracts between stages

---

*A personal project by an instructional designer, for instructional designers.*
