# Options, MoSCoW, metrics and validation

Read this before the synthesis step. The role here is a product manager who protects the MVP from bloat: every sub-capability has a source, and the final call on scope belongs to the user. You prepare a reasoned proposal and show the contested points.

## 1. Shaping options

Give 2-3 shapes of the same feature, ordered from smallest to fullest. They must be real alternatives, not the same thing with more polish.

- **A. Smallest viable.** Completes the primary persona's job end to end with the least new surface. Often a setting, a default, a template, a manual step made explicit, or reuse of something that already exists.
- **B. Middle.** Adds what the evidence says the primary persona will hit soon after A (the most frequent edge case, the most common complaint about competitors).
- **C. Full.** The complete shape as the user imagined it, or as the best competitor does it. Useful as a direction, rarely the first step.

For each shape write:
- **One sentence:** what it is.
- **UX sketch in words:** where the user meets it (entry point), the main steps, the result. Include the empty state (first use), the error state (what fails and what the user sees), and one edge case from the research.
- **Borrows from:** which competitor or analogue pattern, with the reference to section 2 of the report (or to `research/competitive-analysis.md` when the pattern comes from there).
- **Covers:** which persona needs; which it leaves out.
- **Effort:** S / M / L `[estimate]` and what the estimate assumes.
- **Risks:** product (nobody uses it, it confuses), technical (unknowns), business (cost, support load), legal or privacy if any.
- **Dependencies:** other features, data, third-party services, decisions.

Every sub-capability in an option comes from somewhere: the user's request, a persona need, a competitor pattern, or a complaint. Do not add features "from your head"; if you think something is missing, list it as a question.

## 2. Effort scale (always an estimate)

Relative, for design plus implementation by the team the user described. Never convert to days unless the user gave you their own velocity.

| Size | Meaning |
|---|---|
| S | Uses existing screens, components and data; one clear change; few new states |
| M | A new screen or flow, or a new data model, or one external integration; several states and edge cases |
| L | Several new flows, new infrastructure, migrations or multiple integrations; unknowns that need a spike |

Write what the estimate assumes ("assumes the settings screen already exists", "assumes the provider API supports X, unverified"). If the codebase was not read, say the estimate is from the description only.

For the balance check, count S = 1, M = 3, L = 8 points. These weights are a convention of this skill, not a measurement; say so if you show the numbers.

## 3. MoSCoW for the sub-capabilities

Break the feature into sub-capabilities (e.g. "pick a model per task", "fallback when a provider fails", "cost preview") and sort them:

- **Must have:** without it the feature does not do the primary persona's job. Shipping without it is pointless.
- **Should have:** important, but the first version can ship without it. Right after the MVP.
- **Could have:** useful, not critical. If time allows.
- **Won't have (now):** consciously postponed. Say why.

A Must needs at least one criterion, and the table states which:
1. it directly serves the primary persona's job;
2. without it the main scenario is impossible;
3. it is table stakes: nearly every competitor has it and users expect it by default (needs `[source: Sn]` links from section 2).

If a Must rests only on the user's own decision, mark the criterion "O" (owner's call) so it is visible which Musts do not pass the three criteria.

Rules:
- A sub-capability important only for a secondary persona is at most Should, unless it is table stakes.
- **Balance check:** the Must items should take no more than about 60% of the summed effort. More means the MVP is bloated: propose what to downgrade and show it.
- The user wants everything in Must: show the balance and the deadline they gave, propose a cut; the decision is theirs.
- Legal, privacy or compliance items are not ranked by design logic: mark them "owner's decision with a specialist".

## 4. MVP slice

1. One sentence: what the feature does in its first version.
2. The Must sub-capabilities only.
3. The main path of the primary persona from entry to result, in steps. It must go through Must items only; if it needs a Should, either that item is really a Must or the path is wrong.
4. The top 1-3 things deliberately left out, with why not now.

## 5. Success metrics

Pick few, and make each measurable:
- **Leading:** an early sign the feature is used as intended (adoption among the target persona, completion of the main path, repeat use within a period).
- **Lagging:** the outcome the job promises (time saved, fewer errors, retention, cost, revenue), whatever the user cares about.
- **Guardrail (optional):** what must not get worse (support tickets, performance, error rate, cost per user).

For each: how to measure it (the event to log, the query, the survey question, the manual count), the baseline, and the target.
- Baseline from the user's data (`[user: <file>]`) or a source (`[source: Sn]`) only. Otherwise `unknown`, with "measure for <period> before launch".
- Target from the user only. Otherwise "set after the baseline is known". Do not write "increase by 20%" unless someone gave you that number.
- If the product has no analytics, say what minimal instrumentation the MVP needs.

## 6. What to validate before building

Turn the riskiest assumptions (the ones the verdict rests on, usually gaps G<n>) into checks. For each: the method, the signal that it holds, the signal that it fails.

| Method | Good for | Cost |
|---|---|---|
| 5-8 problem interviews with the primary persona | whether the job and pain are real, how they cope today | low, days |
| Data pull (tickets, logs, analytics, search queries) | frequency, who is affected | low, if data exists |
| Fake door / "coming soon" entry point | demand signal before building | low-medium; be transparent with users |
| Clickable prototype test (5 users) | whether the UX shape is understood | medium |
| Concierge / manual version | whether the outcome is valuable before automating | medium |
| Small beta behind a flag | real usage of the smallest shape | higher |

Simulated interviews are not on this list: they produce the questions, real users answer them.

## 7. Verdict

- **Build:** the job and pain are supported by evidence, the smallest shape is clear, risks are known.
- **Build the smaller shape:** demand is plausible but the full shape is not justified yet.
- **Validate first:** the verdict rests on assumptions that a cheap check can confirm or kill.
- **Do not build now:** the evidence points against it, or the cost clearly outweighs the job. Say what would change the verdict.
