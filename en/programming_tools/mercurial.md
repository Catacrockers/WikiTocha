[Back](https://github.com/Catacrockers/WikiTocha/blob/master/en/programming_tools/programming_tools.md)

# Mercurial (hg)

A condensed **cheatsheet** for Mercurial

## Cheatsheet

Command | Description
-------- | -----------
hg init  | Inits control version for current folder
hg clone [url] | clones remote repository
hg pull | get latest changes
hg push | pushes changes to remote
hg add | adds new files
hg remove | removes specified files
hg commit -m "Message" | add changes to commit with -m for message
hg commit --interactive | select which changes you want to include in the commit
hg addremove | adds new files and removes file not in your file system
hg merge | like a ```git merge``` http://hgbook.red-bean.com/read/a-tour-of-mercurial-merging-work.html
hg log -r tip | tip changelog
hg log -l 5 | last 5 changelog statuses
hg status -m | show modified files only
hg status -r | show removed files only
hg status -a | show added files only
