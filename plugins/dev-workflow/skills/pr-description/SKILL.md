---
name: pr-description
description: Write or update a pull request description as a short opener with the full agent-written text collapsed in a details/summary block. Use whenever you run gh pr create or gh pr edit --body, or are asked to write or refresh a PR description.
---

Agent PR text is accurate but long, so keep it all and collapse it behind a short opener.
Based on https://simonwillison.net/2026/Nov/9/details-summary/.
For issues, use `issue-description`.

```markdown
**This is entirely from an agent so do not review until I have pinged for review as I will do a first pass**

Plots in the Julia REPL pane now render on Linux.

Closes #12

<optional screenshot>

<details>
<summary>Claude Opus 5.5 (high effort)</summary>

...summary, changes, testing, decisions, other related issues...

</details>

This was opened by a bot. Please ping @seabbs for any questions.
```

## Opener

- One or two sentences, about 125 characters or fewer. It is the line you promise is worth the reader's time.
- Lead with what is different afterwards, not how it was done.
- If the PR needs something from the reader (a breaking change, a decision, a risky area), say so here.
- Prefer lifting the best sentence from the detail. Do not repeat the title, list files or describe testing.
- If you cannot make one point, the PR probably does two things.

## Rest

- **Links.** Put the issue on its own line with a closing keyword (`Closes #12`), or `Part of #12` if the PR does not finish it. Other links go in the details.
- **Screenshot.** Add one when the change is visible.
- **Summary line.** Give the model. Add the effort only if you know it from the session or `~/.claude/settings.json`.
- **Agent notice and bot footer.** Both stay outside `<details>`. Drop the notice once seabbs has rewritten the opener.
- **Markup.** `<details>` wraps `<summary>`. Leave a blank line after `</summary>` and before `</details>`, or GitHub shows raw Markdown.
- **Body.** Pass it with `--body-file` from the scratchpad.
- **Updates.** Keep the layout. Refresh the opener if scope changes, and edit the detail inside the block.
- **Hook.** A PreToolUse hook blocks `gh pr create`/`gh pr edit` bodies with no `<details>`. Fix the body and retry.
