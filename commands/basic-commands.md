# Linux Basic Commands

## 1. pwd

**Purpose:** Displays the current working directory.

```bash
pwd
```

## 2. ls

**Purpose:** Lists files and directories.

```bash
ls
ls -lah
```

`ls -lah` displays a detailed listing, including hidden entries, with human-readable file sizes.

## 3. cd

**Purpose:** Changes the current directory.

```bash
cd /etc
cd ..
cd ~
```

- `cd /etc` — opens the `/etc` directory.
- `cd ..` — moves to the parent directory.
- `cd ~` — moves to the current user's home directory.

## 4. mkdir

**Purpose:** Creates a directory.

```bash
mkdir practice
```

## 5. touch

**Purpose:** Creates an empty file if it does not exist.

```bash
touch notes.txt
```

## 6. cat

**Purpose:** Displays file contents.

```bash
cat notes.txt
```

## 7. cp

**Purpose:** Copies a file.

```bash
cp notes.txt notes-backup.txt
```

## 8. mv

**Purpose:** Moves or renames a file.

```bash
mv notes.txt important-notes.txt
```

## 9. grep

**Purpose:** Searches text for a matching pattern.

```bash
grep "ERROR" server.log
grep -i "error" server.log
```

The `-i` option makes the search case-insensitive.

## 10. less

**Purpose:** Opens a file for scrolling and reading.

```bash
less server.log
```

Press `q` to quit.

---

## Learning Notes

.## Learning Notes

This repository documents my Linux learning journey through practical examples and command references.