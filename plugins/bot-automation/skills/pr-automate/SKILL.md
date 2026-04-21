# Skill: PR Automate
Expertise in background PR maintenance, feedback relay, and continuous review.

## Procedures

### 1. Initial Review
- Run `review` skill from `dev-workflow`.
- **IMMEDIATE ACTION:** Report the full summary of Critical and Important findings as a message to the main thread.
- **GITHUB ACTION:** Post each finding as an inline PR comment via `gh api`. Skip suggestions.
- **NOTIFY:** Confirm to the main thread once both reporting and posting are complete.

### 2. CI/Conflict Loop (30m) - "The Janitor"
- Every 3m, check `gh pr checks` and mergeability.
- **ACTION:** Resolve technical hurdles (CI failures or conflicts) immediately using `lint` and `test` skills.
- **NOTIFY:** Report success or unfixable failures to the main thread.

### 3. Continuous Integration Review - "The Watcher"
- Watch the local repository and PR for new commits pushed by the **main agent**.
- **ACTION:** When the main agent pushes changes (e.g., in response to feedback), immediately run a targeted `review` on the new changes.
- **NOTIFY:** Report any regressions or new "Critical/Important" issues discovered in the main agent's work back to the main thread immediately.

### 4. Feedback Relay (4h) - "The Messenger"
- Poll for new reviews or comments from `seabbs` or `seabbs-bot`.
- **IMMEDIATE ACTION:** Report the **full content** and location of the feedback to the main thread.
- **STRATEGY:** Do **NOT** fix human feedback; let the main agent implement intent while you continue to monitor the resulting commits.
- **Timing:** 10m intervals for 30m, then 30m intervals.

## Rules
- Use `run_in_background: true`.
- **Collaborative Loop:** You act as a continuous quality gate for the main agent. 
- **High-Signal Reporting:** Ensure reports are concise but complete.
- No permission prompts; use separate Bash calls.
- Treat `seabbs`/`seabbs-bot` as high-priority directives.
