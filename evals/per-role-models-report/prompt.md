---
tags: [feature-research]
max_turns: 60
timeout_seconds: 1500
allowed_tools: [Read, Glob, Grep, Skill, Write, Edit, Bash, WebSearch, WebFetch, Agent]
---

Should we build this? Feature idea for Relay: let people assign a different AI model to each agent role or task. Right now every agent in a run uses the one model from relay.toml. I'd like a cheap fast model for search and test writing and a strong model for planning and review, and maybe a fallback model when a provider is down. Research it and tell me what to build first. The project is the current folder.

Input files: README.md, research/personas.md, research/competitive-analysis.md, docs/user-feedback.md
