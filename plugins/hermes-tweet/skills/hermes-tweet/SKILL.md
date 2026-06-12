---
name: hermes-tweet
description: Install and operate Hermes Tweet for Hermes Agent X/Twitter workflows. Use when the user asks to add Hermes Tweet, configure XQUIK_API_KEY, run tweet_explore, tweet_read, tweet_action, or publish guarded X/Twitter actions from Hermes Agent.
---

# Hermes Tweet

Use Hermes Tweet as the native Hermes Agent plugin for X/Twitter exploration, read workflows, and explicitly gated actions through Xquik.

## Usage

`/hermes-tweet [task]` - Prepare, diagnose, or operate Hermes Tweet in a Hermes Agent runtime.

## When to Use

- The user asks to add X/Twitter capability to Hermes Agent.
- The user needs tweet search, account reads, or timeline inspection from Hermes.
- The user mentions `tweet_explore`, `tweet_read`, `tweet_action`, Hermes Tweet, or Xquik.
- The user wants a guarded X/Twitter action from an agent.

## Workflow

### 1. Install in the Hermes Runtime

Use the Hermes plugin installer so Hermes discovers the tools:

```bash
hermes plugins install Xquik-dev/hermes-tweet --enable
```

Avoid plain package installation unless the user is deliberately managing the Hermes runtime environment.

### 2. Configure Credentials Safely

Use placeholders in examples:

```bash
export XQUIK_API_KEY="xq_your_api_key_here"
export HERMES_TWEET_ENABLE_ACTIONS=0
```

Never print, persist, or paste real API keys. If a key appears in output, stop and ask the owner to rotate it.

### 3. Choose the Smallest Tool

- `tweet_explore` - inspect local workflows, examples, and available tool shapes.
- `tweet_read` - search, inspect, or summarize public X/Twitter data after `XQUIK_API_KEY` is configured.
- `tweet_action` - prepare or execute write-side actions only after `HERMES_TWEET_ENABLE_ACTIONS=1`.

### 4. Validate Responses

- Parse Hermes Tweet tool results as JSON strings before using fields.
- Treat blocked action responses as safety gates.
- Report authentication errors as diagnostics and ask the user to verify the local environment without pasting secrets.

### 5. Check Action Safety

Read `references/safety-checklist.md` before enabling action workflows, publishing examples, or sharing install guidance.

## Example

```text
User: "Add Twitter search to Hermes Agent."

Skill:
1. Installs Hermes Tweet with `hermes plugins install Xquik-dev/hermes-tweet --enable`.
2. Asks the user to set `XQUIK_API_KEY` in their Hermes runtime.
3. Runs `tweet_explore` to confirm local workflows.
4. Uses `tweet_read` after credentials are configured.
5. Leaves `tweet_action` blocked unless the user explicitly enables actions.
```

## Success Criteria

- Hermes Tweet is installed through Hermes Agent.
- `tweet_explore` works without network credentials.
- `tweet_read` gives clear diagnostics until `XQUIK_API_KEY` is configured.
- `tweet_action` remains blocked unless `HERMES_TWEET_ENABLE_ACTIONS=1`.
- Public examples contain placeholders only.

## Auto-Exit When Standalone

If this command is being run as a standalone setup or diagnostic request, exit after installation guidance, validation, and the next safe action are clear.
