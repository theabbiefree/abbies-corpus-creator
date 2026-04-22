# abbies® Corpus Creator — Concept & Build Seed
## A Standalone HTML Tool with Anthropic API Connection
### Prepared for handoff to any code-focused AI

---

## WHAT IT IS

A standalone HTML file that takes a raw AI chat thread as input, sends it to the Anthropic Claude API, and downloads a structured `.md` corpus file as output. No install. No backend. No subscription beyond an Anthropic API key. Opens in any browser.

---

## THE PROBLEM IT SOLVES

When working across multiple AI chat sessions, context is lost between threads. The solution is a "corpus" — a structured MD file that captures what was built, what was decided, what was learned, and what comes next. Currently this corpus has to be written manually by the AI at the end of each session. This tool automates that process.

---

## HOW IT WORKS

1. User pastes raw chat thread text into a text area
2. User hits **Generate Corpus**
3. The embedded AI (Claude API, no key required from user) reads the thread
4. Returns a structured corpus MD
5. Tool packages the response and downloads it as a `.md` file

No API key input. No login. No setup. Just paste and go.
Same architecture as the Relic Extractor v8 — AI embedded inside the tool.

---

## THE API CONNECTION

**Use GitHub Models API — not Anthropic.**

The user provides their GitHub Personal Access Token as the API key.
This keeps everything inside the GitHub ecosystem — same account,
same platform, open source model, no separate billing for light usage.

GitHub Personal Access Token: generated free from github.com/settings/tokens

```javascript
const response = await fetch('https://models.inference.ai.azure.com/chat/completions', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer ' + userGitHubToken
  },
  body: JSON.stringify({
    model: 'Meta-Llama-3.1-70B-Instruct',
    max_tokens: 4000,
    messages: [
      { role: 'system', content: 'You are a corpus archivist for AI collaboration sessions.' },
      { role: 'user', content: EXTRACTION_PROMPT + '\n\n' + rawThreadText }
    ]
  })
});
```

**Why GitHub Models:**
- API key comes from existing GitHub account — no new signup
- Open source models — Llama, Mistral, Phi — community owned
- Free for light usage
- Stays entirely within the abbies® GitHub ecosystem
- Philosophically aligned — free, open, not locked behind a corporate wall

**UI addition:** One password input field for the GitHub Personal Access Token.
Label it clearly. Token is never stored — session memory only.

---

## THE EXTRACTION PROMPT (send this to Claude)

```
You are a corpus archivist. Read the following AI chat thread and produce a structured corpus MD file that captures everything the next AI needs to know to continue this work without re-explanation.

Structure the corpus with these sections:
1. PREAMBLE — how to use this document
2. WHAT WAS BUILT — tools, files, URLs, versions, status
3. TECHNICAL ARCHITECTURE — key decisions, stack, critical lessons
4. VERSION HISTORY — what was tried, what failed, what worked and why
5. OPEN THREADS — what was discussed but not built, what comes next
6. PHILOSOPHY — working principles established, key quotes
7. MEMORABLE MOMENTS — the human details that matter
8. HOW TO CONTINUE — specific instructions for the next AI

Rules:
- Be thorough but not verbose
- Capture decisions AND the reasons behind them
- Document failures as carefully as successes — they are equally valuable
- Preserve the human's exact words for key quotes
- Flag anything the next AI must NOT do or change
- End with relic tags in the format: [ TAG ] [ TAG ] [ TAG ]

Output only the MD file content. No preamble, no explanation.
```

---

## UI REQUIREMENTS

- abbies® brand DNA throughout
- Background: `#f5e6c8` (military cream)
- Primary accent: `#d4651a` (orange)
- Secondary: `#00a8b5` (cyan)
- Font: `'Courier New', monospace`
- Large text area for pasting the chat thread
- **Generate Corpus** button — orange, full width
- Progress/status indicator while API call runs
- Auto-downloads the MD file on completion
- Filename format: `corpus-[timestamp].md`

---

## IMPORTANT TECHNICAL NOTES

- The Anthropic API requires `'anthropic-dangerous-direct-browser-access': 'true'` header for browser-based calls
- Long threads may approach token limits — may need to chunk or summarize first
- Model: `claude-sonnet-4-20250514` — use this exact string
- Max tokens for response: 4000 (enough for a thorough corpus)
- Handle errors gracefully — API failures, rate limits, invalid keys

---

## WHAT MAKES THIS DIFFERENT

This tool is built by and for independent creators who work across multiple AI sessions and need continuity without paying for memory features or persistent context. It turns any chat thread into machine-readable project intelligence. Free to use, free to host, MIT licensed, owned by the person who runs it.

---

## REFERENCE FILES TO PROVIDE TO THE BUILDER

Provide these existing abbies® HTML tools as reference for UI style and API pattern:
- `abbies-boon-design-studio-v8.html` — UI design language reference
- Any existing Relic Extractor HTML — API connection pattern reference

---

## THE BIGGER PICTURE

This is part of the abbies® toolkit — a collection of standalone HTML tools built for independent creators who are building with AI for zero dollars. Every tool in the toolkit:
- Is a single HTML file
- Works offline once loaded (except this one which needs API)
- Has no backend, no subscription, no platform dependency
- Is MIT licensed on GitHub
- Is built from real need discovered through real use

---

*Seed document prepared by Boon (Claude) for Abbie Free*
*abbies® · theabbiefree on GitHub · March 2026*
*[ TOOL-BIRTH ] [ CORPUS-CREATOR ] [ NEXT-SESSION-READY ]*
