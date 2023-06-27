# **Prework Terminal Reading Notes:**

---
---
---

## Why are these reading important?

```markdown
Software developers rely on the terminal to... manage files, software, and their own projects. Don't underestimate the utility in understanding the terminal.
```

---

## [**The Command Line:**](https://ryanstutorials.net/linuxtutorial/commandline.php)

* Prompt:How to print a system variable?

* Solution:

```bash
echo $SHELL
/bin/zsh
```

* Prompt: How to access command history inside the terminal

* Solution: Use the up and down arrows.

---

## [**Basic Navigation:**](https://ryanstutorials.net/linuxtutorial/navigation.php)

* Prompt: How to print working directory?

* Solution:

```bash
pwd
/Users/jacobbassett/projects/courses/code-102/reading-notes
```

* Prompt: How to print long list of give directories contents?

* Solution:

```bash
#ls [options][location]
ls -l /etc
#persmissions n owner        group  size date-modified name
-rw-r--r--   1 jacobbassett  staff  3718 Jun 26 12:43 README.md
...
#note can chain short options like this '$ls -alh'
```

* Prompt: Move to parent directory, parent directory and given directory.

* Solution:

```bash
cd ~
cd ..
cd ~/Documents
```

---

## [**More About Files:**](https://ryanstutorials.net/linuxtutorial/aboutfiles.php)

* Prompt: How to reference a file/directory with a space?

* Solution: Use quotes or backslash.

```bash
cd 'file name'
#OR
cd file\ name
```

* Prompt: How to view all files in directory, including hidden ones?

* Solution: Use -a option

```bash
ls -a
.                   .git                README.md
```

* Prompt: How to find the type of a given file?

* Solution:

```bash
file README.md
README.md: Unicode text, UTF-8 text, with very long lines (339)
```

---

## [**Manual Pages:**](https://ryanstutorials.net/linuxtutorial/manual.php)

* Prompt: Find details about command within system. 

* Solution: Use manual command (man).

```bash
#man <command to look up>
man brew
#type 'q' to exit
```

---

## [**File Manipulation:**](https://ryanstutorials.net/linuxtutorial/filemanipulation.php)

* Prompt: Make a new directory two directories down.

* Solution: 

```bash
#mkdir [options] <path/directoryName>
mkdir -pv ./dirName/firstChildDirName/secondChildDirName
#(-p) will make parent directors as needed
#(-v) provide print out
```

* Prompt: Delete directory

* Solution:

```bash
#rmdir [options] <path/dirName>
rmdir -pv ./dirName/firstChildDirName/secondChildDirName
#must be empty
```

* Prompt: Create a new file

* Solution:

```bash
#touch [options] <fileName>
touch file1 file2 file3
```

* Prompt: Make a copy of a file. Then make copy of directory.

* Solution:

```bash
#cp [options] <source> <destination>
cp file1 file1copy
cp -r dir1 dir1copy
```

* Prompt: Move a file then directory.

* Solution:

```bash
#mv [options] <source> <destination>
mv path1/file1 path2/
mv path1/dir1 path2/
#can also use to rename files or directories
```

* Prompt: Remove non empty directory.

* Solution: 

```bash
rm -ri dirName
#(-r) stands for recursive and is needed to delete directories
#(-i) stands for interactive and prompts what to do with each child file or directory
```

---

## [**Cheat Sheet:**](https://ryanstutorials.net/linuxtutorial/cheatsheet.php)

---
---
---