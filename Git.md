# Git

## Git Ignore
The problem is that .gitignore ignores just files that weren't tracked before (by git add). 
Run `git reset name_of_file` to unstage the file and keep it. 

>In case you want to also remove given file from the repository (after pushing), use `git rm --cached name_of_file`. More on this here: [ignore previously commited files](http://www.codeblocq.com/2016/01/Untrack-files-already-added-to-git-repository-based-on-gitignore/) 

## TODO: 
- add material and ref to: https://jigarius.com/blog/multiple-git-remote-repositories 
