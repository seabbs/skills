# Skills

Claude Code skills marketplace for research, development, and GitHub automation.

## Plugins

| Plugin | Skills | Description |
|---|---|---|
| `research-academic` | 8 | Paper analysis, literature search, preprints, grants, minutes |
| `lang-r` | 1 | R package development (devtools, testthat, roxygen2) |
| `lang-julia` | 1 | Julia package development (SciML standards) |
| `lang-stan` | 1 | Stan probabilistic programming (cmdstanr) |
| `dev-workflow` | 10 | Commits, linting, testing, review, PRs, docs, coverage, deps, scaffolding, tasks |
| `github-ops` | 6 | Dashboard, issue management, repo analysis, issue scanning |
| `org-management` | 10 | CI health, deps, issues, maintenance, orchestration, releases, standards, monitoring |
| `bot-automation` | 3 | Bot collaborator, task processing, daily summaries |
| `productivity` | 7 | Code cleanup, Obsidian notes, tmux, UK news, weekly planning, project inventory |

**Total: 47 skills across 9 plugins**

## Installation

Add this marketplace and install plugins:

```bash
# Add marketplace
claude plugin marketplace add seabbs/skills

# Install all plugins
claude plugin install research-academic@skills
claude plugin install lang-r@skills
claude plugin install lang-julia@skills
claude plugin install lang-stan@skills
claude plugin install dev-workflow@skills
claude plugin install github-ops@skills
claude plugin install org-management@skills
claude plugin install bot-automation@skills
claude plugin install productivity@skills
```

Or install individual plugins as needed.

## All skills

### research-academic

| Skill | Description |
|---|---|
| `/academic-writing-standards` | Academic writing standards for peer-reviewed papers |
| `/analyzing-research-papers` | Systematic paper analysis and insight extraction |
| `/paper-summary` | Summarise a paper from URL, DOI, or file |
| `/preprint-search` | Search arXiv, medRxiv, bioRxiv for new preprints |
| `/literature-search` | Search bibliography files and Paperpile |
| `/grant-application-setup` | Set up grant application repositories |
| `/grant-compliance-checking` | Check work against grant requirements |
| `/minutes` | Create meeting minutes from a transcript |

### lang-r

| Skill | Description |
|---|---|
| `/r-development` | R package development (devtools, testthat, roxygen2) |

### lang-julia

| Skill | Description |
|---|---|
| `/julia-development` | Julia package development (SciML standards) |

### lang-stan

| Skill | Description |
|---|---|
| `/stan-development` | Stan probabilistic programming (cmdstanr) |

### dev-workflow

| Skill | Description |
|---|---|
| `/commit` | Create well-structured commits with conventional format |
| `/lint` | Lint, format, and optionally commit changes |
| `/test` | Run tests, fix failures iteratively, then commit |
| `/review` | Code review with linting and priority-ranked findings |
| `/docs` | Check and fix documentation gaps |
| `/pr` | End-to-end PR workflow from a GitHub issue |
| `/improve-coverage` | Identify test coverage gaps and generate tests |
| `/update-deps` | Review and update dependencies with incremental testing |
| `/project-organization` | Project scaffolding and structure patterns |
| `/taskfile-automation` | Task (taskfile.dev) automation for project workflows |

### github-ops

| Skill | Description |
|---|---|
| `/github-dashboard` | Notifications, PR status, issue triage |
| `/issue-summary` | Summarise a GitHub issue conversation |
| `/issue-reply` | Post a helpful reply to a GitHub issue |
| `/repo-summary` | Repository overview with activity metrics |
| `/repo-activity` | Recent repository activity analysis |
| `/scan-issues` | Find issues suitable for automated resolution |

### org-management

| Skill | Description |
|---|---|
| `/org-ci-health` | Scan CI status across org repos |
| `/org-deps` | Audit cross-repo dependencies |
| `/org-issues-do` | Scan for easy issues and resolve via PRs |
| `/org-issues-tidy` | Add clarity to open issues across repos |
| `/org-maintenance` | Clean up stale worktrees and unstick PRs |
| `/org-orchestrate` | Full org automation setup, scheduling, and execution |
| `/org-releases` | Check which packages are overdue for release |
| `/org-standards` | Scan for standards drift and propagate fixes |
| `/repo-watch` | Detect active repos not cloned locally |
| `/setup-scripts` | Generate helper scripts for org automation |

### bot-automation

| Skill | Description |
|---|---|
| `/add-bot` | Add bot account as repo collaborator |
| `/bot-tasks` | Process bot task requests from GitHub notifications |
| `/daily-summary` | Summarise bot activity across repos |

### productivity

| Skill | Description |
|---|---|
| `/code-cleanup` | Audit and tidy code directory structure |
| `/create-note` | Import markdown into Obsidian |
| `/format-note` | Format an Obsidian note with tags and daily link |
| `/tmux-workflow` | Tmux session management |
| `/uk-news` | UK news summary from BBC and Guardian |
| `/weekly-plan` | Review past week and suggest priorities |
| `/working-on` | Create or update project inventory |

## Environment variables

Some skills use environment variables for personalisation:

| Variable | Used by | Purpose |
|---|---|---|
| `OBSIDIAN_VAULT` | `create-note`, `format-note` | Path to Obsidian vault |
| `GITHUB_HANDLE` | `org-orchestrate` | GitHub username for org automation |

## Licence

MIT
