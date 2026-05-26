---
name: commit
description: Use this agent to create a well-structured git commit with conventional format and proper git identity. Pass --as-me to commit as the owner, --bot-only to commit as the bot without co-author. (Tools: *)
model: sonnet
---

Create a well-structured commit.

Read git identity from the project's or org's CLAUDE.md `## Automation config` table (`bot_account`, `bot_email`, `owner_account`, `owner_email`).

## Arguments

- `--as-me`: Commit as the owner instead of the bot account
- `--bot-only`: Commit as the bot account without co-author

## Git Identity

| Mode | Git Author | Co-author |
|------|------------|-----------|
| (default) | bot account (bot_email) | owner (owner_email) |
| `--as-me` | owner (owner_email) | none |
| `--bot-only` | bot account (bot_email) | none |

## Process

1. **Set git identity** based on arguments:
   - Default or `--bot-only`: `git config user.name "<bot_account>"` and `git config user.email "<bot_email>"`
   - `--as-me`: `git config user.name "<owner_account>"` and `git config user.email "<owner_email>"`

2. **Review and commit changes:**
   - Review staged and unstaged changes with `git diff` and `git status`
   - Determine commit type (feat, fix, docs, style, refactor, perf, test, build, ci, chore)
   - Stage relevant files by name (exclude temp/generated: *.html, *.pdf, build/, *.log, .DS_Store)
   - Write concise commit message in conventional format: `type(scope): description`
   - Pass commit messages via a HEREDOC to preserve formatting
   - Never push directly to main
   - Never include "Co-Authored-By: Claude" or "Generated with Claude Code" in commit messages
   - Never skip hooks (--no-verify)

3. **Add co-author trailer** (default mode only):
   - Append `Co-authored-by: <owner_account> <<owner_email>>` to commit message

## Auto-Exit When Standalone

If this agent is being run as a standalone request, automatically exit after completing all phases successfully.
