---
name: open-in-editor
description: Open files for the user in their running nvim, or in a new tmux split running nvim if there is none. Use when the user asks to see, open or look at a file, or when pointing them at code or text they should read or edit (a finding, a draft, a failing line).
argument-hint: FILE[:LINE] ...
---

Open files where the user is already working, instead of pasting them into the terminal.

```bash
bash ~/code/seabbs/dotfiles/scripts/open-in-nvim.sh FILE[:LINE] ...
```

- It opens in the nvim running in the current tmux session, preferring the current window, and switches to that pane.
- With no nvim running, it opens a new tmux split with `nvim +LINE FILE ...`.
- `--no-focus` opens the file without switching panes. Use it while the user is typing to you.
- `--split` always opens a new split, e.g. to show a file beside the one they are editing.
- Give a line whenever you are pointing at something specific.
- Open one or two files, not a whole directory.
- For diffs use `show-diff`. Outside tmux the script fails, so give the path instead.
