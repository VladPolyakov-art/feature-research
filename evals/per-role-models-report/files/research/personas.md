# Relay personas

> Skill: proto-personas · Date: 2026-10-12 · Product: Relay, an open-source CLI that runs a team of AI coding agents on a git repository
> Inputs: README.md, docs/user-feedback.md
> Tags: [user] · [source: Sn] · [snippet: Sn] · [unverified] · [assumption] · [estimate] · [synthetic] (legend at the bottom)

Written from GitHub discussions; not validated with interviews. Share of persona attributes tagged [assumption]: 4 of 9.

## Solo maintainer (primary)

- Maintains one or two open-source libraries alone, runs Relay on their own laptop with personal API keys. [user: docs/user-feedback.md]
- Job: when a small issue comes in, I want Relay to draft the fix and tests, so I can review and merge in minutes instead of an evening. [assumption] (G1)
- Pays for API usage out of pocket; watches the provider bill. [assumption] (G1)
- Pain: long runs on a strong model get expensive. [user: docs/user-feedback.md, item 1]
- Pain: a run that dies halfway wastes money and time. [user: docs/user-feedback.md, item 2]

## Platform team lead (secondary)

- Leads a 6-10 person platform team; wants to run Relay in CI on internal repositories. [assumption] (G2)
- Job: when the team adopts an AI tool, I want it configured once for everyone, so results are predictable and costs are controlled. [assumption] (G2)
- Company has approved only some providers and models; needs to restrict which models can be used. [user: docs/user-feedback.md, item 3]
- Pain: configuration differs between developers' machines. [user: docs/user-feedback.md, item 4]

## Gaps

- G1 · how often solo maintainers run Relay and what a run costs them · unknown
- G2 · who the platform team lead really is and how they deploy Relay · unknown

## Sources

No web sources. Project files only.

## Changes

- 2026-10-12 · first version.

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
