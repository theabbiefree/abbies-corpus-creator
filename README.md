# abbies® Corpus Creator

**A standalone HTML tool that turns AI chat threads into structured corpus files.**

Paste a raw chat thread. Hit Generate. Download a structured `.md` file that gives your next AI session everything it needs to continue your work — no re-explanation required.

No install. No backend. No subscription. One HTML file, opens in any browser.

---

## The Problem It Solves

Context is lost between AI chat sessions. The Corpus Creator automates what you'd otherwise have to ask your AI to write by hand at the end of every session: a structured document capturing what was built, what was decided, what failed, and what comes next.

---

## How It Works

1. Paste your raw chat thread into the text area
2. Provide your API credentials (see variant notes below)
3. Hit **Generate Corpus**
4. The tool sends the thread to an AI with a structured extraction prompt
5. The response is packaged and downloaded as `corpus-[timestamp].md`

---

## Three Variants

This tool exists in three versions with different API approaches. Use whichever fits your setup.

---

### Variant A — Claude API with User-Supplied Key
`corpus-creator-seed_Claude_AI_API_key.md`

The user provides their own Anthropic API key via a masked password field. The key is held in memory only — never stored, never logged.

**Best for:** Anyone with an Anthropic API account who wants full control and transparency over their key.

**API endpoint:** `https://api.anthropic.com/v1/messages`
**Model:** `claude-sonnet-4-20250514`
**Required header:** `anthropic-dangerous-direct-browser-access: true`

```javascript
headers: {
  'Content-Type': 'application/json',
  'x-api-key': userApiKey,
  'anthropic-version': '2023-06-01',
  'anthropic-dangerous-direct-browser-access': 'true'
}
```

---

### Variant B — Claude API, Key Handled by Platform
`corpus-creator-seed_weak_relic_extractor_AI.md`

Same Anthropic Claude backend, but no key input field — the API key is managed by the environment or platform the tool runs in (same pattern as the abbies® Relic Extractor). The user never sees or manages a key.

**Best for:** Hosted or embedded deployments where the key is injected server-side or by the platform.

**API endpoint:** `https://api.anthropic.com/v1/messages`
**Model:** `claude-sonnet-4-20250514`

---

### Variant C — GitHub Models API
`corpus-creator-seed.md`

Uses the GitHub Models inference endpoint with open-source models (Llama, Mistral, Phi). The user provides a GitHub Personal Access Token — free to generate from any GitHub account, no separate billing for light usage.

**Best for:** Users who want to stay entirely within the GitHub ecosystem and prefer open-source models. Philosophically aligned with the abbies® free-and-open ethos.

**API endpoint:** `https://models.inference.ai.azure.com/chat/completions`
**Model:** `Meta-Llama-3.1-70B-Instruct` (or other GitHub Models)
**Token source:** `github.com/settings/tokens`

```javascript
headers: {
  'Content-Type': 'application/json',
  'Authorization': 'Bearer ' + userGitHubToken
}
```

---

## The Extraction Prompt

All three variants send the same structured prompt to the AI:

The AI is instructed to produce a corpus with eight sections:

1. **PREAMBLE** — how to use the document
2. **WHAT WAS BUILT** — tools, files, URLs, versions, status
3. **TECHNICAL ARCHITECTURE** — key decisions, stack, critical lessons
4. **VERSION HISTORY** — what was tried, what failed, what worked and why
5. **OPEN THREADS** — discussed but not built; what comes next
6. **PHILOSOPHY** — working principles, key quotes
7. **MEMORABLE MOMENTS** — the human details that matter
8. **HOW TO CONTINUE** — specific instructions for the next AI

Output is raw MD only — no preamble, no explanation, no wrapper.

---

## UI Spec (All Variants)

| Element | Value |
|---|---|
| Background | `#f5e6c8` (military cream) |
| Primary accent | `#d4651a` (orange) |
| Secondary | `#00a8b5` (cyan) |
| Font | `'Courier New', monospace` |
| Main input | Large textarea for raw chat thread |
| Auth input | Password field (Variants A and C) |
| CTA button | Orange, full width — **Generate Corpus** |
| Status | Progress indicator during API call |
| Output | Auto-download on completion |
| Filename | `corpus-[timestamp].md` |

---

## Technical Notes

- Anthropic direct browser calls require the `anthropic-dangerous-direct-browser-access: true` header (Variants A and B)
- Very long threads may approach model token limits — consider chunking or summarising before pasting
- Max response tokens: 4000
- Handle errors gracefully: API failures, rate limits, expired or invalid keys

---

## Part of the abbies® Toolkit

Every tool in the abbies® toolkit is:

- A single HTML file
- Works offline once loaded (except API-dependent tools like this one)
- No backend, no subscription, no platform lock-in
- MIT licensed on GitHub
- Built from real need, discovered through real use

GitHub: [theabbiefree](https://github.com/theabbiefree)

---

*abbies® · Built by Boon (Claude) for Abbie Free · March 2026*
*[ TOOL-BIRTH ] [ CORPUS-CREATOR ] [ NEXT-SESSION-READY ]*
