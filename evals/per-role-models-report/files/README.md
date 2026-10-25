# Relay

Relay is an open-source command-line tool that runs a small team of AI coding agents on a git repository. One run goes through four roles in order:

1. **planner** reads the issue and writes a step-by-step plan;
2. **coder** makes the changes;
3. **test-writer** adds or updates tests;
4. **reviewer** reviews the diff and either approves it or sends it back to the coder.

Users bring their own API keys for model providers.

## Configuration

Everything lives in `relay.toml` at the repository root:

```toml
[model]
provider = "anthropic"
name = "some-model-id"
max_tokens = 8000

[run]
max_review_rounds = 3
```

Today every role in a run uses the single `[model]` block. There is no per-role setting and no fallback: if the provider returns an error, the run stops.

## Status

Version 0.6. Maintained by two people in their spare time. No telemetry is collected; the only usage signals are GitHub issues and discussions.
