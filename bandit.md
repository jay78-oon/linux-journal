# Linux Fundamentals - OverTheWire Bandit

---

## Level 0

### Command

```bash
ssh <username>@<server> -p <port>
```

**Purpose:**
Log in to a remote server.

**Password for Level 1:**
`bandit0`

---

## Level 1

### Commands

```bash
ls
cd
cat
```

* `ls` = list files/directories
* `cd` = change directory
* `cat` = display file contents

### Useful `cd` commands

```bash
cd ..    # parent directory
cd /     # root directory
cd ~     # home directory
```

**Password for Level 2:**
`6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR`

---

## Level 2

### Problem

The file is named `-`.

### Command

```bash
cat ./-
```

### Why?

`-` can be interpreted as standard input.

`./-` explicitly tells the command to read the file named `-` from the current directory.

**Password for Level 3:**
`PK8fYLZg2hnHSz83plBL1iEPKdD3QToB`

---

## Level 3

### What I learned

Hidden files start with `.`.

### Command

```bash
ls -a
```

### Why?

`-a` means **all**, so `ls` also displays hidden files.

**Password for Level 4:**
`xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq`

---

## Level 4

### Commands learned

```bash
file
```

`file` = determine a file's type.

```bash
reset
```

`reset` = reset the terminal and fix a messed-up display.

### The challenge

Find the only human-readable file among many.

### Solution

```bash
cd inhere
file ./*
```

`file ./*` checks the type of every file in the directory.

Then:

```bash
cat ./<human-readable-file>
```

**Password for Level 5:**
`6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG`
