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

## 7. Symlink installation

The previous p3 copies and root assets moved to
`~/.agents/backup-2026-10-14/`. The installer links the fork's skill directories
and the `agents/`, `README.md`, and `LICENSE` assets. Agent briefs must be
reachable because delegated tasks and the comment review use them.

The installer passed two runs in a temporary project. It preserved an
existing plain skill copy and an unrelated skill.

## 8. Global model file

The approved model values are in [local-models.md](local-models.md).
The active file is `~/.agents/p3-models.md`. All four distinct entries replied
with `pong`. Codex uses `reasoningEffort`, Claude uses `effort`, and DeepSeek
uses `variant`, all at `high`. MiMo has no effort option and omits it.
The Gemini seat waits for the user's OpenCode privacy approval.

## 9. Old configuration cleanup

The project `p3-models.md` files in `relationship-app`, `arra`, and
`arra-videos` were deleted from their working trees. These deletions remain
uncommitted. No other status entry or staged diff changed in those repositories.

The old `~/.agents/pstack-models.md` file was deleted. The global Codex
instructions now point to `~/.agents/p3-models.md`. They retain the Codex CLI
notes for supported spawn arguments and available agent slots.
