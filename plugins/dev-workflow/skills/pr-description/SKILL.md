---
name: pr-description
description: Write or update a pull request description as a short opener with the full agent-written text collapsed in a details/summary block. Use whenever you run gh pr create or gh pr edit --body, or are asked to write or refresh a PR description.
---

Agent-written PR descriptions are accurate but long, and the length puts readers off.
Keep all of the detail, but hide it behind `<details><summary>` so a reader sees only a short opener first.
Based on https://simonwillison.net/2026/Nov/9/details-summary/.

## Layout

```markdown
**This is entirely from an agent so do not review until I have pinged for review as I will do a first pass**

<opener>

<optional screenshot>

<details>
<summary>Claude Opus 5.5 (high effort)</summary>

## Summary
...the full description: problem, changes, testing, decisions, related issues...

</details>

This was opened by a bot. Please ping @seabbs for any questions.
```

- **Agent notice.** Keep it at the top for agent-opened PRs (see `mark-pr-agent`).
  Drop it once seabbs has rewritten the opener.
- **Opener.** One or two sentences, about 125 characters or fewer.
  It is the shortest text that tells a reader what the PR is for and whether it needs their attention.
  Say what changes for the user or the codebase, not how.
  No headings, lists or "This PR..." preamble.
- **Screenshot.** Add one when the change is visible (UI, plots, rendered docs, CLI output).
- **`<details>` block.** Holds everything an agent would normally write.
  Nothing is removed, only collapsed.
- **Summary line.** Name the model that wrote the text, and the effort level if you know it.
  Take the model name from your environment.
  Take effort from the session, or from `effortLevel` or `modelSettings` in `~/.claude/settings.json`.
  If you do not know the effort, give the model alone. Never guess.
- **Bot footer.** Goes after `</details>` so it stays visible.

## Markup rules

- `<details>` wraps everything, and `<summary>` is the first child ("details, then summary").
- Leave a blank line after `</summary>` and before `</details>`.
  Without them GitHub renders the Markdown inside as plain text.
- Write the body to a file in the scratchpad and pass it with `--body-file`.
  Inline `--body` strings break on quotes and backticks.

## Examples of openers

- "The row page showed its single row as a one-row table."
- "Table pages that span more than one page now show where you are, with navigation at the top as well as the bottom."
- "Repos missing from a hub now clone there on demand instead of failing."

## Updating a description

When scope changes (see `pr-automate` step 7), keep this layout.
Rewrite the opener if what the PR does has changed.
Edit the detail inside `<details>`.
Never move detail back out of the block.

## Enforcement

A PreToolUse hook in the `seabbs/claude` settings blocks `gh pr create` and `gh pr edit` when it can read the body and the body has no `<details>` block.
If it blocks you, rewrite the body in this layout and retry.
Do not try to get round it.
