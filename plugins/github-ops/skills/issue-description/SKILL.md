---
name: issue-description
description: Write or update a GitHub issue body as a short paragraph covering the problem, suspected cause and proposed fix, with the detail for each collapsed in details/summary blocks. Use whenever you run gh issue create or gh issue edit --body.
---

Issues follow `pr-description` (opener visible, detail collapsed). The opener covers the problem, the suspected cause and the proposed fix.
Markup, attribution and `--body-file` rules are as in that skill.

```markdown
Plots in the Julia REPL pane show as blank boxes on Linux.
We are fairly sure MuxDisplay has no imgcat to hand the image to.
Shipping a small imgcat shim with the tmux config should fix it.

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

- Write the opener as a short paragraph of about 60 words at most, in plain language. Say what goes wrong, what we think causes it and what we would do.
- Describe the problem as the symptom a person sees, not the code.
- Say how sure you are of the cause. Write "we do not know why yet" rather than guess.
- The fix can be "open, needs a decision on X".
- For a feature request, cover the need, the gap and the proposal instead.
- Give one `<details>` block each for problem, cause and fix, and drop any that would be empty. Open each block with a few lines, and nest a further `<details>` only for long logs or traces.
- `Related` links the issues or PRs a reader needs, such as the PR follow-up work came from.
- When the cause is confirmed, update the opener to say so.
- Short questions (e.g. the `repo-watch` issue) stay plain text.
