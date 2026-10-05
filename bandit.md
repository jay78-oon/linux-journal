# Linux Fundamentals - OverTheWire Bandit

---

## Level 0

### Command

```bash
ssh <username>@<server> -p <port>
```

**Purpose:**
Log in to a remote server.

**Password for Level 0:**
`bandit0`

---

## Level 0

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

**Password for Level 1:**
`6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR`

---

## Level 1

### Problem

The file is named `-`.

### Command

```bash
cat ./-
```

### Why?

`-` can be interpreted as standard input.

`./` is the path to a file of the current directory.

**Password for Level 2:**
`PK8fYLZg2hnHSz83plBL1iEPKdD3QToB`

---

## Level 2

### Problem

The file is named `--spaces in this filename--`.

### Command

```bash
cat "./--spaces in this filename"
```

### Why?

With quotes `""` the shell passes it as one argument while **without** it, the shell split it into three arguments. 

**Password for Level 3:**
`7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME`

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

### What I learned 

```bash
file
```

`file` = determine a file's type.

### The challenge

Find the only human-readable file among many.

### Solution

```bash
file ./*

# Give me the file type of all files in this directory.
```

`*` is a wildcard. It roughly means `match every filename here` excluding hidden files.

Then:

```bash
cat ./<human-readable-file>
```

**Password for Level 5:**
`6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG`

---

## Level 5

### The challenge 

Find the file that follows these properties:
* human-readable
* 1033 bytes in size
* not executable

### What I learned

* `find` = searching files based on conditions 
* `-size` = check the size of the file 

### The solution 

```bash
find . -type f ! -executable -size 1033c
```

* `find .` = start searching from the current directory 
* `-type f` = only look for regular files
* `! -executable` = the file is not executable
* `-size 1033c` = exactly 1033 bytes (`c` means byte)

The output is:

```bash
./maybehere07/.file2
```

This means the matching file is `.file2` inside the `maybehere07` directory.

To read it:

```bash
cd maybehere07
cat .file2
```

The `.` at the beginning of `.file2` is part of the filename. It is a hidden file.

**Password for Level 6:** 

`pXa26xhMWaC2SvDotA4r9EgZkulOeSBW`

---

## Level 6

### The challenge 

Find the file that stored somewhere on the server that has the following properties:
* owned by user bandit7
* owned by group bandit6
* 33 bytes in size

### The solution

```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

* `find /` = start searching from the root of the filesystem
* `-user bandit7` = owned by user bandit7
* `-group bandit6` = owned by group bandit6
* `2>/dev/null` = hide permission-denied errors

The output is

```bash
/var/lib/dpkg/info/bandit7.password
```

Then

```bash
cat /var/lib/dpkg/info/bandit7.password
```

**Password for Level 7:**

`Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3`

---

## Level 7

### The challenge

Find the password stored in the file `data.txt` next to the word `millionth`.

### What I learned

* `grep` = search text for a pattern

* `base64` = encode or decode Base64
* `tr` = translate or delete characters
* `tar` = create or extract archieves
* `gzip` = compress/ decompress files using gzip
* `bzip2` = similar to `gzip2`, but uses the bzip2 compression format
* `xxd` = display files as hexadecimals

### The solution

```bash
grep "millionth" data.txt
```

**Password for Level 8:**
`VR1ljMayciFxbnUokuQmJFw6QC9VKtub`

---

## Level 8

## The challenge

Find the password in the `data.txt` file that is the only line of text that occurs only once.

### What I learned

* `sort` = sort lines of text
* `uniq` = remove consecutive duplicate files

## The solution

```bash
sort data.txt | uniq -u
```
* `uniq -u` = show only words that occur once

**Password for Level 9:**
`EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl`

---

 ## Level 9

 ### The challenge

Find the password stored in `data.txt` file in one of the few **human-readable strings**, preceded by **several `=` characters. 

 ### What I learned

 * `strings` = extract human-readable strings from binary files

 ### The solution

 ```bash
```

**Password for Level 10:**
` `

---
