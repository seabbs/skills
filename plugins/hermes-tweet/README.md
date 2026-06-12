# Hermes Tweet

Hermes Agent X/Twitter setup, read workflows, and guarded action operation.

## Skills

| Skill | Description |
|---|---|
| `/hermes-tweet` | Install and operate Hermes Tweet for Hermes Agent X/Twitter workflows |

## Installation

```bash
claude plugin marketplace add seabbs/skills
claude plugin install hermes-tweet@skills
```

Install Hermes Tweet in Hermes Agent:

```bash
hermes plugins install Xquik-dev/hermes-tweet --enable
```

Configure the runtime with user-managed values:

```bash
export XQUIK_API_KEY="xq_your_api_key_here"
export HERMES_TWEET_ENABLE_ACTIONS=0
```

## Notes

- Start with `tweet_explore` for local workflow discovery.
- Use `tweet_read` only after `XQUIK_API_KEY` is configured.
- Keep `tweet_action` blocked until `HERMES_TWEET_ENABLE_ACTIONS=1`.
- Keep real credentials out of prompts, files, issues, and logs.
