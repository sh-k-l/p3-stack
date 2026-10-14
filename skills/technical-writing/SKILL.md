---
name: technical-writing
description: "Use ASD-STE100 Simplified Technical English for replies and prose artifacts. Use for /technical-writing and for docs, RFCs, readmes, PR descriptions, or commit messages."
disable-model-invocation: true
---

# Technical writing

Use ASD-STE100 Simplified Technical English as the single writing style.
Apply it to replies, documentation, product copy, comments, PR text, and commit messages.
Keep technical names, paths, flags, and commands exact.
Use the codebase as the source for technical terms.

## Choose the document type

Choose the structure by the reader's task. The structure does not change the writing style.

- A tutorial teaches through actions. State what the reader will build. Give a visible result for each step.
- A how-to gives steps for a goal. Assume the reader knows the basics. Put background in a linked document.
- A reference states facts, options, limits, and errors. Match the structure of the system it describes.
- An explanation answers a question about reasons. Include the relevant context, decisions, constraints, and alternatives.

Keep each document focused on one type. Split other material into linked documents.
For PR descriptions and commit messages, use the repository's required structure.

## Write clear sentences

- Use one idea per sentence. Use one instruction per sentence.
- Keep instructions to 20 words or fewer. Keep descriptive sentences to 25 words or fewer.
- Use active voice. Name the actor when the actor matters.
- Write instructions as direct commands. Put a condition or warning before the instruction it controls.
- Use plain words. Remove words that add no meaning.
- Use one term for each thing. Use one meaning for each word.
- Keep articles such as "the" and "a". Keep the words that make the sentence clear.
- Use the present tense for current behavior. Use future tense only for a future event.
- Put the common case before exceptions.
- Use a technical noun when an approved general word cannot name the thing accurately.
- Avoid figurative language, idioms, filler, and Latin abbreviations.
- Avoid an "-ing" form when a direct verb is clearer.
- Put "only" and "not" next to the words they modify.
- Split long strings of nouns. State the relation between the nouns.
- Make each pronoun refer to one clear noun. Repeat the noun if needed.
- State which items "and" or "or" joins when the grouping is unclear.
- Use periods instead of semicolons or em dashes.
- Keep a sentence complete. Do not omit its verb to save words.

## Format for the reader

- Use sentence-case headings. Use a verb phrase for a task heading and a noun phrase for a concept heading.
- Use numbered lists for steps. Use bullets for parallel items.
- Introduce a list with a complete sentence. Keep the list items parallel.
- Use code font for code, symbols, commands, and paths. Use bold for UI controls when it helps the reader find them.
- Use link text that names the target. Never use "click here".
- Avoid slashes in prose alternatives. Write "a, b, or both". Keep slashes in technical names and paths.

## Check the artifact

Apply the **unslop** skill before delivery. It lists patterns to remove within the ASD-STE100 style.
Check the meaning after each rewrite. Preserve required content and the intended tone.
Check each technical name, count, command, and link against the source.
For a count or tree claim, include the command that produces it when the reader needs to repeat the check.

A PR body must explain the problem, change, scope, and verification in under a minute.
Link detailed logs, commit lists, and metric tables instead of copying them into the PR body.
Keep the document structure required by the repository.

## Example

`budget.mjs` reads the budget from `budget.json` and counts the files that import protos.
If the count exceeds the budget, CI fails.
Run `budget.mjs --write` only to lower the budget.
