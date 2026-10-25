# Competitive analysis: AI coding agent tools

> Skill: competitive-research · Date: 2026-10-10 · Product: Relay, an open-source CLI that runs a team of AI coding agents on a git repository
> Inputs: README.md, user brief in chat, 3 web sources
> Tags: [user] · [source: Sn] · [snippet: Sn] · [unverified] · [assumption] · [estimate] · [synthetic] (legend at the bottom)

## Products compared

| Product | Type | Model choice | Evidence |
|---|---|---|---|
| Aider | direct, open-source CLI | Separate settings for the main model and for a second model used in architect-style editing | [source: S1] |
| Continue | adjacent, IDE extension | Different models can be assigned to different roles such as chat, edit and autocomplete | [source: S2] |
| Cline | adjacent, IDE extension | Planning and acting can use different models | [snippet: S3] |

## Findings

- Choosing a model per role or mode is common among tools in this category. [source: S1+S2]
- None of the three pages describes a fallback when a provider is down. unknown (searched the three pages above only; G1)
- Cost control is mostly left to the user's provider dashboard. [assumption] (G2)

## Gaps

- G1 · fallback model when a provider fails · not found on the opened pages
- G2 · built-in cost caps · not checked

## Sources

S1 · Aider documentation · https://aider.chat/docs/ · accessed 2026-10-10 · official
S2 · Continue documentation · https://docs.continue.dev/ · accessed 2026-10-10 · official
S3 · Cline documentation (search excerpt) · https://docs.cline.bot/ · accessed 2026-10-10 · official

## Changes

- 2026-10-10 · first version.

## Tag legend

| Tag | Meaning |
|---|---|
| `[user]` | said by the user in chat or written in their own files; name the file when there is one |
| `[source: Sn]` | from a page or document that was actually opened; `Sn` is its row in Sources |
| `[snippet: Sn]` | seen only in a search-result excerpt, page not opened |
| `[unverified]` | known from model memory, not checked against a source |
| `[assumption]` | reasoning or inference, not checked; points to a gap `G<n>` |
| `[estimate]` | a size, effort or quantity guess, with what it assumes |
| `[synthetic]` | said by a simulated persona; a hypothesis, never evidence |
