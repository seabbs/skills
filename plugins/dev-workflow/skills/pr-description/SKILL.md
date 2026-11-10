---
name: pr-description
description: Write or update a pull request description as a short opener with the full agent-written text collapsed in a details/summary block. Use whenever you run gh pr create or gh pr edit --body, or are asked to write or refresh a PR description.
---

Agent PR text is accurate but long, so keep it all and collapse it behind a short opener.
Based on https://simonwillison.net/2026/Nov/9/details-summary/.
For issues, use `issue-description`.

```markdown
**This is entirely from an agent so do not review until I have pinged for review as I will do a first pass**

This PR closes #12, where plots in the Julia REPL pane showed as blank boxes on Linux.
MuxDisplay had nothing to hand the image to, so here we bundle a small imgcat shim and point it there.

<optional screenshot>

<details>
<summary>Claude Opus 5.5 (high effort)</summary>

- **Display.** MuxDisplay hands plots to a bundled imgcat shim.
- **Tests.** A new script checks plots render in a headless pane.

<details>
<summary>Display: how and why</summary>

...design, edge cases, alternatives...

</details>

<details>
<summary>Testing</summary>

...what ran and what it covers...

</details>

</details>

This was opened by a bot. Please ping @seabbs for any questions.
```

## Inside the block

- Start with a scan layer, one line per change. A reader should be able to stop there.
- Then give one nested `<details>` per topic, in the same order, for the deep detail. This covers design, edge cases, test detail, limits, follow-ups and other links.
- Use two levels at most. A small PR skips the nested blocks.

## Opener

- Write a short paragraph in plain language. Make it as short as it can be while still getting the reader up to speed, which is often a few sentences. It is the text you promise is worth the reader's time.
- Say what was wrong or missing, linking the issue (`This PR closes #12, where...`). Then say what this PR does about it.
- If the PR needs something from the reader (a breaking change, a decision, a risky area), say so here.
- Do not list files or describe testing. Those belong in the details.
- If it needs much more than a paragraph, the PR probably does two things.

## Rest

- **Links.** Use a closing keyword for the issue in the opener (`closes #12`), or `is part of #12` if the PR does not finish it. Other links go in the details.
- **Decisions.** If seabbs has to decide anything, add a visible `Needs your decision:` line under the opener. Remove each item once it is settled.
- **Screenshot.** Add one when the change is visible.
- **Summary line.** Give the model. Add the effort only if you know it from the session or `~/.claude/settings.json`.
- **Agent notice and bot footer.** Both stay outside `<details>`. Drop the notice once seabbs has rewritten the opener.
- **Markup.** `<details>` wraps `<summary>`. Leave a blank line after `</summary>` and before `</details>`, or GitHub shows raw Markdown.
- **Body.** Pass it with `--body-file` from the scratchpad.
- **Updates.** Update the description whenever a push changes what the PR does. Rewrite it from `git diff origin/main...HEAD` so it describes the PR as it now stands against main. Do not narrate how it got there ("initially", "then", "now also", "in response to review"). That history lives in the commits and review threads. Keep the layout.
- **Hook.** A PreToolUse hook blocks `gh pr create`/`gh pr edit` bodies with no `<details>`. Fix the body and retry.
