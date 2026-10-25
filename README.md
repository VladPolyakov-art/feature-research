# feature-research

A Claude Code skill that turns a feature idea into one decision-ready report: should we build this, in what shape, and what first. It looks at the problem behind the feature, how competitors and analogues solve it, what each type of user needs, two or three solution shapes from smallest to full, and ends with a verdict, a MoSCoW split, an MVP slice, success metrics and what to validate with real users before building.

Its core is honesty: facts come only from the user or from cited sources. Assumptions, effort estimates and simulated user quotes are tagged as such, and no numbers, quotes or competitor features are invented.

## How it works

- **Reads what you already have** (README, brief, PRD, persona files, feedback, the code around the feature) and asks 3-5 questions only if the idea or the product context is too thin.
- **Shows a plan in chat:** the feature as a job story, research questions, a competitor shortlist, which tools are available.
- **Researches** competitors and analogues with links (and screenshots, if a browser is available) and the users: it reuses your persona files, or builds lightweight proto-personas marked as assumptions, plus optional short simulated interview snippets labelled synthetic. Big tasks run in parallel sub-agents with role prompts from `references/`.
- **Synthesizes** in the main agent: 2-3 options with a UX sketch in words, effort S/M/L (an estimate), risks and dependencies; then MoSCoW with a criterion for every Must and an effort balance check.
- **Writes one report** and an 8-line summary in chat.

## Output

`research/feature-<slug>.md` in your project (you can name another path):

0. Verdict: build / build the smaller shape / validate first / do not build now
1. Problem and job, with an evidence list and gaps
2. How others solve it: 3-6 competitors and analogues, patterns to borrow, anti-patterns
3. Users: needs and pains per persona, optional synthetic interview snippets
4. Options from smallest viable to full
5. Recommendation: MoSCoW, MVP slice, success metrics and how to measure them, open questions, what to validate first
6. Sources

The file starts with a header block (skill, date, product, inputs, tags) and ends with a Sources list and the tag legend. Every claim carries a shared tag: `[user]`, `[source: Sn]`, `[snippet: Sn]`, `[unverified]`, `[assumption]`, `[estimate]`, `[synthetic]`. The skill also adds a row to `research/INDEX.md`.

## Contents

| Path | What |
|---|---|
| `SKILL.md` | instructions for the agent |
| `references/output-template.md` | the report structure, header block, Sources and tag legend |
| `references/kit-protocol.md` | shared rules of the research kit: file names, tags, reuse, index |
| `references/competitor-scout.md` | role prompt for competitor research |
| `references/user-researcher.md` | role prompt for user research, proto-personas and synthetic snippets |
| `references/options-and-prioritization.md` | options, S/M/L scale, MoSCoW rules, metrics, validation methods |
| `evals/` | scenarios for checking the skill's behavior |

## Works with

This skill is one of six research skills that work alone and together:

| Skill | Writes | Repo |
|---|---|---|
| competitive-research | `research/competitive-analysis.md` | https://github.com/VladPolyakov-art/competitive-research |
| deep-research | `research/deep-research.md` | https://github.com/VladPolyakov-art/deep-research |
| ux-audit | `research/ux-audit/<product>/audit_report.md` (+ `summary.md`) | https://github.com/VladPolyakov-art/ux-audit |
| proto-personas | `research/personas.md` | https://github.com/VladPolyakov-art/proto-personas |
| simulated-interview | `research/interview-<persona-slug>.md` | https://github.com/VladPolyakov-art/simulated-interview |
| feature-research | `research/feature-<slug>.md` | https://github.com/VladPolyakov-art/feature-research |

Each skill works alone; when a sibling's output is in `research/`, it is reused instead of redone. This one is the integrator: it summarizes and links competitors, personas, interviews, UX audits and market research when they exist.

## Installation

```bash
git clone https://github.com/VladPolyakov-art/feature-research ~/.claude/skills/feature-research
```

Then ask Claude Code something like "should we build X?" or "research this feature: ...".

## Optional tools

- **Web research:** WebSearch / WebFetch or a Firecrawl connection. Without them the skill says so and offers a fallback: you paste links or exports, or it works from model knowledge with every competitor claim tagged `[unverified]`, or it gives you a prompt to run in an external deep research tool.
- **A browser** (e.g. Claude in Chrome) for screenshots of public competitor pages.
- **Sibling skills** (see Works with): if their output is in `research/`, it is reused; if the skills are installed, the final summary may suggest one for a deeper pass. None is required.

The skill does not ask for API keys or log into any service.

## License

[MIT](LICENSE)
