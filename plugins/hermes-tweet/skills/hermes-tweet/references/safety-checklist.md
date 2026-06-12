# Hermes Tweet Safety Checklist

Use this checklist before action workflows or public examples.

## Credentials

- Use `XQUIK_API_KEY` placeholders only.
- Never paste real keys into chat, issues, logs, commits, or screenshots.
- If a real key appears in output, stop and ask the owner to rotate it.

## Tool Order

- Start with `tweet_explore` for local workflow discovery.
- Use `tweet_read` only after `XQUIK_API_KEY` is configured.
- Use `tweet_action` only for explicit user-requested actions.

## Action Gate

- Keep `HERMES_TWEET_ENABLE_ACTIONS=0` by default.
- Require `HERMES_TWEET_ENABLE_ACTIONS=1` before action workflows.
- Confirm the target account, text, and intended effect before proceeding.

## Public Communication

- Describe access as using Xquik through Hermes Tweet.
- Do not include private infrastructure details, internal routing, or cost information.
- Keep examples focused on setup, tool order, diagnostics, and safety.
