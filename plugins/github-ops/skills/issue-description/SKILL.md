---
name: issue-description
description: Write or update a GitHub issue body as a short problem, suspected cause and proposed fix, with the detail for each collapsed in details/summary blocks. Use whenever you run gh issue create or gh issue edit --body.
---

Issues follow `pr-description` (opener visible, detail collapsed), but lead with three lines.
Markup, attribution and `--body-file` rules are as in that skill.

```markdown
**Problem.** Plots in the Julia REPL pane render as blank boxes on Linux.
**Suspected cause.** MuxDisplay has no imgcat to hand the image to (fairly sure).
**Proposed fix.** Ship a small imgcat shim with the tmux config.

Related: #88

<details>
<summary>Problem: reproduction and evidence</summary>

...

</details>

<details>
<summary>Cause: what was checked</summary>

...

</details>

<details>
<summary>Fix: plan and options</summary>

...

</details>

Details drafted by Claude Opus 5.5.

This was opened by a bot. Please ping @seabbs for any questions.
```

- Each line is one sentence of about 125 characters or fewer.
- **Problem** is the symptom a person sees, not the code.
- **Suspected cause** says how sure you are. Write "Not known yet" rather than guess.
- **Proposed fix** can be "Open, needs a decision on X".
- For feature requests use **Need**, **Gap** and **Proposal** instead.
- Give one `<details>` block per line, and drop a block that would be empty. Open each block with a few lines, and nest a further `<details>` only for long logs or traces.
- `Related` links the issues or PRs a reader needs, such as the PR follow-up work came from.
- When the cause is confirmed, rename the line to **Cause**.
- Short questions (e.g. the `repo-watch` issue) stay plain text.
