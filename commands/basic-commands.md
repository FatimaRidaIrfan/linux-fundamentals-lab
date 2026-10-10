# Linux Basic Commands

A quick reference to common Linux commands for navigation, file management, and text searching.

## 1. Navigation

| Command | Purpose |
|---|---|
| `pwd` | Displays the current working directory. |
| `ls` | Lists files and directories. |
| `ls -lah` | Shows detailed file information, including hidden files and human-readable sizes. |
| `cd /etc` | Changes to the `/etc` directory. |
| `cd ..` | Moves to the parent directory. |
| `cd ~` | Moves to the current user's home directory. |

## 2. File and Directory Management

| Command | Purpose |
|---|---|
| `mkdir practice` | Creates a directory named `practice`. |
| `touch notes.txt` | Creates an empty file if it doesn't exist. |
| `cat notes.txt` | Displays the contents of a file. |
| `cp notes.txt notes-backup.txt` | Copies a file to a new file. |
| `mv notes.txt important-notes.txt` | Renames or moves a file. |
| `rm notes.txt` | Deletes a file. Use carefully. |

## 3. Searching Text

| Command | Purpose |
|---|---|
| `grep "ERROR" server.log` | Searches for the word `ERROR` in a file. |
| `grep -i "error" server.log` | Searches without distinguishing uppercase and lowercase letters. |

## 4. Reading Files

| Command | Purpose |
|---|---|
| `head server.log` | Displays the first 10 lines by default. |
| `tail server.log` | Displays the last 10 lines by default. |
| `less server.log` | Opens a file for scrolling and reading. Press `q` to quit. |

## Important Notes

- Linux commands are case-sensitive.
- Be careful when using `rm`, because deleted files may not be recoverable.
- Practice commands in a test directory before using them on important files.

## Learning Notes

This repository documents my Linux learning journey through practical examples and command references.