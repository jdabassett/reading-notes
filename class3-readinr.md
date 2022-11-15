# Flash Cards: GitHub
___
___
___

## Why is this important?
We will be using GitHub to organize the files we create while we are web developing. Being ambitous students, we will be making lots of mistakes. Like the late great David Rakoff said, "You really need to pay attention to each step, or you will end up in the soup."

GitHub will help us manage and restore files as we try to keep our projects 'out of the soup'.
___
___
## Flashcards

**What is version control?**
```
A system that keeps previous versions of file recorded and accessible for restoration. 

"When you done f&^%ed-up do you have anything to fall back on?"
```
___
**What is the difference between a CVC and DVC version control system?**
```
A Centralized Version Control System(CVS) is centralized at one location.
A Distributed Version Control System(DVCS) is decentralized into local nodes that comprise the whole.
DVCS is more resiliant to failure than CVC. GitHub is a DVCS.

"Although being so cork-fork special, you might be the exception to the rule."
```
___
**What are the three locations a file/file-version can reside?**
```
1)Local Working Directory
2)Staging Area
3)Repository

"Don't get lost on your way to Grandma's house now, this isn't that hard to remember."
```
___
**With these three locations in mind what is the terminal command to move files between them?**
```
#1->2
>git add file.txt
#called adding files to stagine area

#2->3
>git commit -m "comment about changes"
#commiting changes to repository
>git push origin main
 
#3->1
>git clone "repository-address" newNameIfYouWant
#to make clone of whole respository
>git restore --stored=id file.txt
#restore deleted file from repository

#2->1
>git restore--staged file.txt
#retore deleted file from staging
```
___
**Check your config settings?**
```
>git config --list
#user.name=John Doe
#user.email=example@email.com
#core.editor=code--wait
#init.defaultbranch=main
```
___
**Get help with git terminal command?**
```
>git log --help
#will return documentation about log command.
```
---
**Check the git status?**
```
>git status
#On branch main
#Your branch is up to date with 'origin/main'.
#nothing to commit, working tree clean
```
**Check address of respository?**
```
>git remote -v
#origin	https://github.com/jdabassett/102d45-second-website.git (fetch)
#origin	https://github.com/jdabassett/102d45-second-website.git (push)
```
___
___
___
## Things I want to know more about.
1. What GitHub branches enable?
