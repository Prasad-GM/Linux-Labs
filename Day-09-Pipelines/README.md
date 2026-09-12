# 🔀 Day 09 - Pipelines and Command Integration

## Objective
To understand how to use the pipe operator to connect commands and process data efficiently in Linux.

---

## What is a Pipeline?
A **pipe** (`|`) connects the **standard output** of one command to the **standard input** of the next command.

- Sends data from one program to another
- Allows output to be manipulated before reaching the terminal
- Multiple commands can be chained together

### Syntax
```bash
command1 | command2 | command3
```

---

## Pipeline Examples

```bash
# Count number of user accounts
cat /etc/passwd | wc -l

# Convert lowercase to uppercase
cat /etc/passwd | tr a-z A-Z

# Sort file contents alphabetically
cat filename | sort

# Display unique sorted lines
cat filename | sort | uniq

# Create directory and files together
mkdir -p jetking && touch jetking/file{1..7}
```

---

## Useful Commands with Pipes

| Command | Purpose |
|---------|---------|
| `wc -l` | Count number of lines |
| `tr a-z A-Z` | Convert lowercase to uppercase |
| `sort` | Sort output alphabetically/numerically |
| `uniq` | Show only unique lines (use after sort) |
| `grep pattern` | Filter lines matching a pattern |
| `head -n` | Show first n lines |
| `tail -n` | Show last n lines |

---

## Practical Examples

```bash
# Find all users with /bin/bash shell
cat /etc/passwd | grep /bin/bash

# Count how many users have bash shell
cat /etc/passwd | grep /bin/bash | wc -l

# Sort and show unique lines from a file
cat myfile.txt | sort | uniq

# Search and display with line numbers
cat /etc/passwd | grep root | nl
```

---

## Tips
- Pipes work **left to right** — output of left becomes input of right
- You can chain **as many pipes** as needed
- Use `|` with `grep`, `sort`, `wc`, `uniq`, `awk`, `sed` for powerful text processing
