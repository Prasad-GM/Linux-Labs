# ✏️ Day 06 - VIM Editor

## Objective
To learn how to use the VIM text editor for creating and editing files in Linux.

---

## What is VIM?
**VIM (Vi IMproved)** is a powerful command-line text editor.
- Enhanced version of the old `vi` editor
- Widely used by programmers and system administrators
- Has special color highlighting for configuration files
- Learn more using: `vimtutor`

---

## VIM Modes
VIM has three main modes:
1. **Command Mode** — default mode; navigate and execute commands
2. **Insert Mode** — type/edit text
3. **Extended Mode** — save, quit, search, replace

---

## Insert Mode Keys

| Key | Action |
|-----|--------|
| `i` | Insert at current cursor position |
| `I` | Insert at beginning of line |
| `a` | Append after cursor |
| `A` | Append at end of line |
| `o` | Insert new line below cursor |
| `O` | Insert new line above cursor |

---

## Navigation Keys (Command Mode)

| Key | Action |
|-----|--------|
| `h` | Move left |
| `l` | Move right |
| `j` | Move down |
| `k` | Move up |
| `$` | Move to end of line |
| `gg` | Move to first line of document |

---

## Copy, Paste, Delete (Command Mode)

| Key | Action |
|-----|--------|
| `yy` | Copy current line |
| `p` | Paste below cursor |
| `dd` | Delete current line |
| `2yy` | Copy 2 lines |
| `yw` | Copy one word |
| `u` | Undo |
| `x` | Delete character (like Delete key) |
| `X` | Delete character before cursor (like Backspace) |

---

## Save and Quit (Extended Mode)

| Command | Action |
|---------|--------|
| `:w` | Save file |
| `:q` | Quit |
| `:wq` | Save and quit |
| `:x` | Save and quit |
| `:wq!` | Force save and quit |
| `:q!` | Quit without saving |

---

## Extended Mode — Extra Features

| Command | Action |
|---------|--------|
| `:se nu` | Show line numbers |
| `:se nonu` | Hide line numbers |
| `:/word` | Search for a word |
| `:%s/old/new` | Find and replace |
| `:number` | Jump to line number |
