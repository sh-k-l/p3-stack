# Local installation

## 1. Fork and source check

The fork is `sh-k-l/p3-stack`. The local clone is `~/repos/p3-stack`.
Keep `upstream` for manual merges. Do not schedule upstream updates.

On 2026-10-14, the installed p3 skill files and agent briefs matched the
upstream files. No local changes needed a separate import commit.
The installed `tdd` and `teach` copies belong to Matt Pocock.

## 2. Retained workflows

Use the playbooks in the mode router. The performance measurement checklist
lives in the Perf issue playbook. The stack workflow contains its own owner,
audit, and verification steps. Larger programs use `figure-it-out`.

## 3. Publication approval

Local, reversible work proceeds without a question. Publication requires an
exact request or approval. The always-pause list still applies.

## 4. Reply style

Use ASD-STE100 Simplified Technical English for replies and prose artifacts.
Keep the mode's reply rules and evidence labels. Name relevant principles only
in the final summary of a non-trivial task.

## 5. Model setup

The global model file is the default. Project role lines can override it.
Setup resolves option IDs from the catalog and pings each distinct entry.
Only a completed reply proves access. Add project overrides to `.prettierignore`
to prevent changes to provider IDs.

## 6. Skill name collisions

The 2026-10-14 transcript scan covered 835 JSONL files. It counted direct
slash commands, Claude command tags, and Skill tool calls. It excluded
mere mentions, code blocks, duplicate message IDs, and inherited messages.

`code-review` had two Skill calls and stays in place. These skills had zero
invocations and moved to `~/.agents/skills-archive/` without deletion.

- `tdd`
- `teach`
- `prototype`
- `diagnose`
- `handoff`
- `to-prd`
- `to-spec`
- `to-tickets`

`diagnosing-bugs` had zero invocations and was already absent.
No skill needed an `mp-` name. The fork supplies p3's `tdd` and `teach`.
The skill lock file stays unchanged. It still names Matt's versions, so a
future `npx skills update` can restore the old copies and name collisions.
