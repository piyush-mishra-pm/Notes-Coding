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


