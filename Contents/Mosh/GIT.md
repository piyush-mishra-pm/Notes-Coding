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
- Logically separate  commits. Bugs and typos should be commited separately.
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