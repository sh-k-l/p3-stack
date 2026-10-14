---
name: setup-p3
description: Configure which models p3-stack uses per role and at what reasoning budget. Detects your available models and writes p3-models.md, which overrides the skill defaults. Use for /setup-p3, "configure p3 models", "p3 budget", or changing p3-stack's model choices.
disable-model-invocation: true
---

# Setup p3

Write `p3-models.md`, a file that sets p3-stack's model per role. Use `~/.agents/p3-models.md` by default. Write a project file only when the user requests an override. Read the global file first. A project role line overrides the same global role. A missing project role keeps the global value.

## Steps

### 1. Detect available models

Call `orchestrator_capabilities`. It lists the providers and models you can pass to `delegate_task` in this session, custom models included, with each one's provider instance ID and any reasoning options. Use that catalog to resolve exact IDs and option IDs. The catalog can be stale. A catalog entry is not proof that a model works. If it returns nothing, stop and report the gap. Every selected entry must pass the live ping in step 4. Resolve `inherit-parent` to the current parent for that ping.

### 2. Load current state

The roles are the labels shown in step 5. If `p3-models.md` already exists at the chosen location, read it and treat its `# budget` line and its role values as the current choices. Otherwise start from the defaults in step 3(b). A line whose role is not in step 5, such as `how critics`, is from a retired role. Drop it.

### 3. Budget, map, and confirm

**(a) Set the budget.** Use the user's approved choices when the session already has them. Otherwise ask for a budget and state the current value. Offer these options.

- `unlimited, keep max`
- `large, xhigh reasoning`
- `medium, high reasoning`
- `small, medium reasoning`

**(b) Apply it.** Build the working table. On a fresh run, give code roles (`feature, refactoring`, `bug-fix`, `perf-issue`) and the explorer, investigator, and swarm roles the fastest strong coding model detected. Give `judgment and prose`, `hardest tasks`, the explainer, the synthesizers, and `reflect tooling` the most capable model detected. Fill each panel role with one entry per distinct provider detected, up to three. On a re-run, keep any role the user changed.

When the catalog exposes reasoning options for a model, set each real entry's effort option from the budget: `unlimited` takes the highest option, and `large`, `medium`, and `small` take `xhigh`, `high`, or `medium`. The ladder is `max` > `xhigh` > `high` > `medium` > `low`. If the model does not expose the target, use the highest option at or below it. If none exists, mark the role as needing a choice. Use the exact option ID from the catalog. Codex uses `reasoningEffort`. OpenCode uses `variant`. Check Claude's catalog option instead of assuming an ID. `inherit-parent` does not change. When the catalog exposes no reasoning options, map roles only and drop effort tokens; the budget label is still recorded.

**(c) Show the roles and confirm.** Show every role with its model, marking any entry not in the detected set as needing a choice. Also list each line step 2 dropped. If the choices are not already approved, ask whether to accept them or change specific roles, offering the detected models plus `inherit-parent` (the role runs on the parent thread's model, so omit the model in `delegate_task`) as the options. For panel roles (arena runners, architect runners, interrogate reviewers) the value is a list, and one `delegate_task` runs per entry, `inherit-parent` entries included, so the list length sets the count. `arena cross-judge pool` is also a list, but Arena selects one value from it whose provider differs from the parent's when possible. `swarm workers` is the default model for every worker unless a race or comparison assigns another model per arm.

### 4. Ping every distinct entry

Check each provider, model, and effort value against the catalog.
Then call `delegate_task` for every distinct provider, model, and option combination.
Use `mode: "wait"` and the prompt "Reply with the single word pong. Do not use tools or change files."
Pass the selected option under its exact catalog ID in `target.options`.
For a model with no effort option, omit effort and ping the model without it.
For `inherit-parent`, omit `target` and ping the parent model once.

Keep each task ID and a stable `clientRequestId` for that ping.
A wait timeout does not cancel the child. Read that task with `task_status` before any retry.
Only a completed task with the expected word proves that the entry answered.
A failed task, a timeout without a later answer, or an empty response is not a pass.

Write only entries that answered. Report every other entry and its affected roles as needing a choice.
Do not substitute an untested model. If a failed entry was the only value for a role, ask for a replacement.
Complete the replacement ping before writing that role. Do not turn a failed role into an untested default.

### 5. Write the file

Write `p3-models.md` with a `# budget` line with the chosen label and its target effort, and one line per role, using the same labels p3-mode uses. Write each entry as `<providerInstanceId>/<model>`, followed by its effort option in parentheses when step 3(b) set one. Overwrite the selected file so re-runs produce the same result. Keep one line per panel role.

For a project override, add `p3-models.md` to that project's `.prettierignore`.
Prettier can rewrite `_` in `opencode_/` to `*` and break the provider ID.
A global file does not need a project ignore entry.

Shape:

```
# p3 model configuration. One line per role. Delete a line to fall back to the skill default.
# Use `inherit-parent` to run on the parent model. Omit the delegate_task target.
# Each panel entry counts as one seat.
# budget: unlimited (max)
feature, refactoring: <providerInstanceId>/<model> (<effort>)
bug-fix: <providerInstanceId>/<model> (<effort>)
perf-issue: <providerInstanceId>/<model> (<effort>)
judgment and prose: <providerInstanceId>/<model> (<effort>)
hardest tasks: <providerInstanceId>/<model> (<effort>)
how explorer: <providerInstanceId>/<model> (<effort>)
how explainer: <providerInstanceId>/<model> (<effort>)
why investigators: <providerInstanceId>/<model> (<effort>)
why synthesizer: <providerInstanceId>/<model> (<effort>)
reflect tooling: <providerInstanceId>/<model> (<effort>)
reflect judgment, divergent, synthesizer: <providerInstanceId>/<model> (<effort>)
arena runners: <entry>, <entry>, <entry>
arena cross-judge pool: <entry>, <entry>, <entry>
swarm workers: <providerInstanceId>/<model> (<effort>)
architect runners: <entry>, <entry>, <entry>
interrogate reviewers: <entry>, <entry>, <entry>
```

### 6. Confirm

Report the file path, each ping result, and each unresolved choice. The file applies to new sessions. Re-run this skill to update it.

### 7. Offer a verification skill (optional)

Check whether the project has a way to drive the real app for proof (a `verify-*` skill, or an existing harness). If not, offer once: "want a project-local verification skill, so agents can drive the app the way a user does and prove changes work? I can generate one with /create-verification-skill." On yes, invoke `/create-verification-skill`. On no, move on without pushing.
