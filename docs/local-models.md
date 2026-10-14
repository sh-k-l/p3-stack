# Global model file

This snapshot matches `~/.agents/p3-models.md` on 2026-10-14.
All four active models replied with `pong` through `delegate_task` in wait mode.
The Gemini seat remains blocked under the user's privacy choice.

```text
# budget: medium (high)
# OpenCode: use OpenCode Go models only.
# Option IDs: Codex reasoningEffort, Claude effort, OpenCode variant.
# MiMo exposes no effort option. Omit effort for that model.
feature, refactoring: codex/gpt-6.1-sol (high)
bug-fix: codex/gpt-6.1-sol (high)
perf-issue: codex/gpt-6.1-sol (high)
judgment and prose: claudeAgent/claude-opus-5-5 (high)
hardest tasks: claudeAgent/claude-opus-5-5 (high)
how explorer: opencode_/opencode-go/deepseek-v4.1-flash (high)
how explainer: claudeAgent/claude-opus-5-5 (high)
why investigators: opencode_/opencode-go/deepseek-v4.1-flash (high)
why synthesizer: claudeAgent/claude-opus-5-5 (high)
reflect tooling: claudeAgent/claude-opus-5-5 (high)
reflect judgment, divergent, synthesizer: claudeAgent/claude-opus-5-5 (high)
swarm workers: opencode_/opencode-go/deepseek-v4.1-flash (high)
# The intended third seat is opencode_/opencode-go/gemini-4-argon-contributor.
# It is blocked until the user allows "paid endpoints that train on request data"
# in OpenCode privacy settings. MiMo-V2.6-Pro holds that seat until then.
arena runners: codex/gpt-6.1-sol (high), claudeAgent/claude-opus-5-5 (high), opencode_/opencode-go/mimo-v2.6-pro
arena cross-judge pool: codex/gpt-6.1-sol (high), claudeAgent/claude-opus-5-5 (high), opencode_/opencode-go/mimo-v2.6-pro
architect runners: codex/gpt-6.1-sol (high), claudeAgent/claude-opus-5-5 (high), opencode_/opencode-go/mimo-v2.6-pro
interrogate reviewers: codex/gpt-6.1-sol (high), claudeAgent/claude-opus-5-5 (high), opencode_/opencode-go/mimo-v2.6-pro
```
