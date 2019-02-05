# Mercurial (hg)

A condensed **cheatsheet** for Mercurial

## Cheatsheet

Command | Description
-------- | -----------
hg pull | get latest changes
hg add | adds new files
hg commit -m "Message" | add changes to commit with -m for message
hg commit --interactive | select which changes you want to include in the commit
hg addremove | adds new files and removes file not in your file system
hg merge | like a ```git merge``` http://hgbook.red-bean.com/read/a-tour-of-mercurial-merging-work.html
hg log -r tip | tip changelog
hg log -l 5 | last 5 changelog statuses
hg status -m | show modified files only
hg status -r | show removed files only
hg status -a | show added files only
