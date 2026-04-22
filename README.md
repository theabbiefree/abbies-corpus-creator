# abbies® Corpus Creator

> A zero-backend, browser-based tool for transforming raw AI chat threads into structured, reusable corpus documents — so your next AI session picks up exactly where the last one left off.

---

## What It Does

When you're deep into a long AI collaboration session, context gets lost the moment the conversation ends. **abbies® Corpus Creator** solves this by taking your raw, messy chat thread and using an LLM to distill it into a clean, structured Markdown corpus file covering everything the next AI needs to know: what was built, key decisions, what failed, open threads, working philosophy, and explicit continuation instructions.

The output is a portable `.md` file you can drop into any future session as a starting document.

---

## Features

- **No backend, no server, no subscription** — runs entirely in the browser
- **Together AI powered** — uses the Together AI API with your own key
- **Multiple model options** — choose between speed, quality, or balance
- **Configurable output length** — 2,000 / 4,000 / 6,000 max tokens
- **Smart thread truncation** — automatically handles threads over 80,000 characters with a clear warning
- **Live filename preview** — updates dynamically as you type your project name
- **Character counter** — shows live count with a warning for very long threads
- **One-click download** — saves output as `<project>-YYYY-MM-DD-corpus.md`
- **Copy to clipboard** — instant copy with visual confirmation

---

## Getting Started

### Prerequisites

- A modern web browser (Chrome, Firefox, Safari, Edge)
- A [Together AI](https://www.together.ai/) account and API key

### Usage

1. **Open `index.html`** in your browser — no server or install needed.
2. **Enter your Together AI API key** in the API key field. Click **Show** to reveal it if needed.
3. **Select a model** based on your speed/quality needs (see [Model Options](#model-options) below).
4. **Set max output tokens** — 4,000 is standard for most threads.
5. **Enter a project name** (optional) — used to build the output filename.
6. **Paste your full chat thread** into the text area — the longer and messier, the better.
7. **Click Generate Corpus** and wait 20–40 seconds for the model to process.
8. **Preview, copy, or download** the generated `.md` file.

---

## Model Options

| Model | Best For |
|---|---|
| **Llama 3.1 70B** *(default)* | Balanced speed and quality — good for most threads |
| **Llama 3.1 405B** | Maximum quality, slower — use for complex or long threads |
| **Mistral Large** | Strong reasoning, balanced performance |
| **Nous Hermes 2 Mixtral** | Fast alternative for quick iterations |

---

## Corpus Output Structure

The generated `.md` file follows a consistent 8-section structure:

1. **PREAMBLE** — How to use the document
2. **WHAT WAS BUILT** — Tools, files, URLs, versions, current status
3. **TECHNICAL ARCHITECTURE** — Key decisions, stack choices, critical lessons learned
4. **VERSION HISTORY** — What was tried, what failed, what worked and why
5. **OPEN THREADS** — Discussed but unbuilt ideas, what comes next
6. **PHILOSOPHY** — Working principles established during the session
7. **MEMORABLE MOMENTS** — The human details and context that matter
8. **HOW TO CONTINUE** — Explicit instructions for the next AI session

---

## API Key & Privacy

- Your API key is entered directly in the browser and sent only to `api.together.xyz` — it is never stored, logged, or transmitted anywhere else.
- No data leaves your browser except the API call to Together AI.
- The tool has no backend, no analytics, and no cookies.

---

## Limitations

- **Thread length:** Threads over 80,000 characters (~20,000 tokens) are automatically truncated. A warning is shown in the output when this occurs.
- **API dependency:** Requires an active Together AI API key with available credits.
- **Rate limits:** If you hit Together AI's rate limit, wait a moment before retrying.

---

## File Naming

Output files are named automatically using the pattern:

```
<project-slug>-YYYY-MM-DD-corpus.md
```

If no project name is entered, the filename defaults to `project-YYYY-MM-DD-corpus.md`. The slug is lowercased and special characters are replaced with hyphens.

---

## License

MIT — free to use, modify, and distribute.

---

## Author

**theabbiefree** on GitHub  
abbies® Corpus Creator · no backend · no subscription · just paste and go
