---
name: pr-automate
description: Run as a background subagent after a PR is created or pushed. Acts as a continuous quality gate, posting review findings, watching CI and mergeability, and relaying human feedback back to the main thread. Invoke via the Agent tool with run_in_background true.
---

# PR Automate

Background PR maintenance, feedback relay, and continuous review. Runs
alongside the main agent as a quality gate.

## When to use

Spawn this skill as a background subagent after either:

- A new PR is created (`gh pr create` completes), or
- A push lands on a branch with an open PR (`git push` completes)

The main agent invokes it via the `Agent` tool with `run_in_background:
true` so it can work in parallel without blocking.

## Procedures

### 0. Tag the PR as agent-authored
- Run this step only when spawned after a PR was just created (the
  post-create path). Skip on the post-push path if the PR already
  carries the notice.
- Prepend the following line to the PR body:
  **This is entirely from an agent so do not review until I have
  pinged for review as I will do a first pass**
- Update the PR via `gh pr edit --body` (or the GraphQL equivalent).
- Confirm the notice is in place before moving on.

### 1. Initial review
- Run the `review` skill from `dev-workflow`.
- Report the full summary of Critical and Important findings back to the
  main thread.
- Post each finding as an inline PR comment via `gh api`. Skip
  suggestions.
- Confirm to the main thread once both reporting and posting are done.

### 2. CI / conflict loop — "the janitor" (30 min)
- Every 3 min, check `gh pr checks` and mergeability.
- Resolve technical hurdles (CI failures, conflicts) using the `lint`
  and `test` skills.
- Report success or unfixable failures back to the main thread.

### 3. Continuous integration review — "the watcher"
- Watch the PR for new commits pushed by the main agent.
- When new commits land, run a targeted `review` on the new changes.
- Report regressions or new Critical/Important issues back immediately.

### 4. Feedback relay — "the messenger" (up to 4 h)
- Poll for new reviews or comments from `seabbs` or `seabbs-bot`.
- Report the full content and location of the feedback to the main
  thread.
- Do not fix human feedback; let the main agent implement intent while
  this skill keeps monitoring resulting commits.
- Timing: 10 min intervals for 30 min, then 30 min intervals.

## Rules

- Run with `run_in_background: true`.
- Act as a continuous quality gate for the main agent, not a
  replacement.
- Keep reports concise but complete.
- Use separate Bash calls; do not trigger permission prompts.
- Treat `seabbs` and `seabbs-bot` feedback as high priority.
