# Skill: Show Diff
Expertise in opening a tmux split with `diffview.nvim` to review changes.

## Overview
Open a new tmux pane that displays recent changes using `diffview.nvim`. This is useful for self-review or for showing the user what has changed.

## Usage
Run the following command:
`bash ~/code/seabbs/dotfiles/scripts/show-diff.sh $ARGUMENTS`

### Arguments
- No argument → working tree vs HEAD (uncommitted changes only).
- `main...HEAD` → branch diff vs main (for committed changes on a feature branch).
- Any valid rev range (e.g., `HEAD~3..HEAD`) → passed through verbatim.

## Requirements
- Must be in an active tmux session.
- Must be in a Git repository.

## Execution Rules
- Pick the argument based on where the changes live (uncommitted vs branch).
- After opening, notify the user that the pane is available for review.
- Do not attempt to interact with the nvim pane from the agent side.
