# Mosh Hamedani's Git course.

### Configuring Git:

```bash
# Used "" below since space present between first name and last name.
git config --global user.name "Sherlock Holmes"
git config --global user.email sherlockcodes.@gmail.com

# VS code as default editor (not vim)
git config --global core.editor "code --wait"

# Handling end of lines: Configure core.autocrlf
## Windows-> \r\n , where \r is carriage return and \n is line feed.
git config --global core.autocrlf true

## Mac/Linus -> \n (only linefeed).
git config --global core.autocrlf input
```

### Initializing a Repo:

```bash
# Initialise an empty repo
mkdir awesomeRepo
cd awesomeRepo
git init

# To see hidden git subdirectory, which if deleted, removes project history.
ls -a
```

### Staging:

```bash
echo Hello > file1.txt
echo Adios >> file1.txt # appends to existing file).
# recursively adds from current directory and children.
git add .
git add file1.txt file2.txt
git add *.txt
```

### Commiting:

```bash
git commit -m "Commit heading."
# For detailed message:
git commit # PRESS ENTER. VS code opens where you can enter 1st line, then leave a line empty and then type detailed message from thrid line onwards.
```

- Commits neither be too big nor too small. Commit often.
- Commit on states you want to record.
- Logically separate commits. Bugs and typos should be commited separately.
- Meanigful commit messages. If doing too many things in 1 commit, then difficult mesaging.
- tense: Present (Fix the bug), or Past (Foxed the bug). Depends on team practices.

### Skipping the Staging Area:

```bash
# Directly adds all files to staging area and commits with message.
git commit -a -m "Message"
#or
git commit -am "Mesage"
```

### Removing files:

Even though file removed from working dir, it was still in staging area.

```bash
rm file1.txt
# to see the files in staging area
git ls-files
# to actualy delete from staging area, need to add
git add file1.txt
git commit -m "Removed File1"

# Shorter way: Removes from workig directory and staging area.
git rm file1.fxt file2.txt *.csv
git commit -m "Removed files"
```

### Renaming / Moving files:

Rename = Deleting + creating file. So needs addition and deletion changes. Instead, can use `git mv` to apply changes to both working dir and staging area.

```bash
mv file1.js file2.js
git add file1.js #removal
git add file2.js #creation (untracked file)
git commit -m "msg"

# or
git mv file1.js file2.js
git commit -m "msg"
```

### Ignoring Files:

If you haven't already committed a file in repository, you can still ignore it.

```bash
echo ignoreDir > .gitignore
echo file.txt >> .gitignore
echo *.log >> .gitignore
git add .gitignore # ignoreDir and file.txt and *.log not even tracked now.
git commit -m "Added gitignore"

# If file already committed, then need to remove from staging area (but not working dir).
git rm --cached - ignoreDir/ # only remove from index, recursively
git ls-files # directory removed from staging area.
git commit -m "Ignored accidentally commited folder."
```

Various gitignore templates: github.com/github/gitignore

### Shorter Git Status

```bash
git status -s
# status format:
# SW file1.txt -> S is staging area, W is working Dir
#  M file2.txt -> Modified in Working dir area, but not present in working dir.
# M  file2.txt -> Added in staging area.
# MM file2.txt -> Added in staging area, but modified in working dir too.
# ?? file2.txt -> Untracked.
# A  file2.txt -> Added in staging Area
```

### Viewing Staged and Unstaged Changes:

```bash
# To see Staged Changes: Staged changes going to next commit.
git diff --staged

# To see Unstaged changes: Changes in working dir, which are not staged yet.
git diff # if all changes are staged, then no output.
```

### Visual diff tools:

P4Merge, KDiff3,, WinMerge, VSCode
Configuring VSCode as difftool.

```bash
git config --global diff.tool vscode
git config --global difftool.vscode.cmd "code --wait --diff $LOCAL $REMOTE"
# Add $LOCAL and $REMOTE in config file, as they were missed.
git config --global -e
# Use difftool (with or without --staged)
git difftool --staged
```

### Viewing the History (Commit List):

```bash
git log # to go next page, press space, to quit pres q.

# oneline description
git log --oneline

# latest commit at bottom.
git log --oneline reverse
```

### Viewing the Commit:

```bash
# Using ID, see the commit details (including diff)
git show c594a45 # Just sufficient enough chars to distinguish commit id.

# Using Head pointer, see the commit details (including diff)
git show HEAD~1 # Commit previous to Head

# Skip diff details, and look for how a file looked at a commit.
git show HEAD~1:bin/app.txt

# To see all files and directories in a commit. File is represented as blob, and Directory is represented as tree.
git ls-tree HEAD~1
git show casr350 #identifier of file. Shows content of that file (whose identifier mentioned).
```

#### Git Objects:

- Commits,
- Blobs (Files)
- Trees (Directories)
- Tags

### Unstaging Files:

Undoing Add operation. Two ways:

- Reset (Hard or soft).
- Restore: Takes a copy from the next environment (for staging envt, the next environment is last commit). For untracked file which is staged, restore will make it untracked file again. If file in working directory, then restores from staging area. If file in staging area, then restores it from last commit.
  - soft : removes the commit only (working dir and stagir area intact, only commit reset).
  - mixed : Unstages files (working dir intact, but staging and commit are reset).
  - hard : discards local changes (staging, working dir and commit are all reset).

```bash
# restore files in staging area. Will transfer changes to working directory, and no staged changes exist for those files.
git restore --staged file1.txt file2.txt *.csv

# restore everything in staging area.
git restore --staged .
```
