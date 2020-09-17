# Git

## Git Ignore
The problem is that .gitignore ignores just files that weren't tracked before (by git add). 
Run `git reset name_of_file` to unstage the file and keep it. 

>In case you want to also remove given file from the repository (after pushing), use `git rm --cached name_of_file`. More on this here: [ignore previously commited files](http://www.codeblocq.com/2016/01/Untrack-files-already-added-to-git-repository-based-on-gitignore/) 

## Git Revert
`git revert` acts like loading a save point in a video game. It allows us to go back (revert) to a previous commit. Best way to run a `revert` is as follows:   
`git revert <commit hash>`  
The command will create a new commit with 'Revert' as the first word of the message. To view the hash's of each commit we can run: `git log` or `git log --oneline` for a more simplistic output.  
```bash
Walker@WalkerDesktop MINGW64 ~/Documents/Projects/The Notebook/The-Notebook (master)
$ git log --oneline
9566909 added info about postgres too!
f997c53 Merge branch 'master' of https://github.com/wchesley/The-Notebook
826e83b added dotnetonHeroku
```
Git log:  
```bash
Walker@WalkerDesktop MINGW64 ~/Documents/Projects/The Notebook/The-Notebook (master)
$ git log
commit 956690974791617b89e19c8926dcbfc406b8b153
Author: Walker Chesley <chesley.walker@gmail.com>
Date:   Thu Apr 30 15:24:14 2020 -0500

    added info about postgres too!
```
Then to rollback to a previous commit we could run: `git revert f997c53` to revert to the commit with the message, "Merge branch of 'master' of https://git" 
>Sometimes this causes the branch to get into a detached state, to resolve a detached head run `git checkout <current branch>`
So to revert the last commmit run `git revert <commit hash>`; then you can push your new commit, which undid the previous commit.  

For more info:  
- [code.likeagirl.io](https://code.likeagirl.io/how-to-undo-the-last-commit-393e7db2840b)  
- [Atlassian - Undoing changes](https://www.atlassian.com/git/tutorials/undoing-changes)
- [Atlassian - Git Revert](https://www.atlassian.com/git/tutorials/undoing-changes/git-revert)


## Dual remote origins (mirroring repos across sites)

Having code hosted in two places provides challenges, why should we have to push the same commit twice to two different repos? Thankfully git has provided a solution. 

`git remote set-url origin --add https://bitbucket.org/YOU/YOUR_REPO.git`

By adding another remote (in this case bitbucket because I normally use github) with the same name `origin`, when I push, it goes to both repositories! Essentially a mirror. I had tried to use the `git --mirror` to no avail. It got the code to bitbucket but when I pushed to github again, the changes I made were not reflected in bitbucket. By adding another remote I am able to push to both repos in one go. 