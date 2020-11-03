# Git

## Body with commit message
You can add a body to the commit message via `git commit -m 'initial message' -m 'body of message`  
[This stackoverflow post](https://stackoverflow.com/questions/16122234/how-to-commit-a-change-with-both-message-and-description-from-the-command-li) also shows a good way to send a commit message using vscode as the editor with a gif example, the command to do so is: `git config --global core.editor "code --wait"`

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

### Caveats: 
Due to the nature of Git, you cannot fetch from two different remotes under the same name. So while the above solution allows you to mirror your code to another place. If the code is altered in the added origin, you will not be able to fetch it, or push back to that origin due to the changes.  
For example, when I added a second origin to a project, my git remotes looked as follows:  
```bash
$ git remote -v
origin  https://github.com/wchesley/CIDM-Fall2020-4390.git (fetch)
origin  https://github.com/wchesley/CIDM-Fall2020-4390.git (push)
origin  https://Walker-Chesley@bitbucket.org/Walker-Chesley/cidm-4390-fall2020.git (push)
```

So my code is mirrored to bitbucket on push, but if someone was to push to bitbucket alone, I wouldn't be able to  
1. See the changes
2. Push to the repo

##### Ref: https://jigarius.com/blog/multiple-git-remote-repositories

## Git in WSL
Just attempted to open and run a project in WSL (Ubuntu) however git was showing every single file in the repo as modified, even though they were not. The error comes from the different line endings used in Windows vs. Unix.  
The resolution is as follows:   
`git config core.autocrlf true`  
`git config core.autocrlf true`   
Some people opted to use the `--global` flag with this, I however kept it as per repository considering there's only two projects I'm working on in WSL, the rest will live in windows.  
>Note: the project lives in the windows file system, I just used WSL and VSCode to open it.  
Another note: I usually use [fork](https://fork.dev/) as a git GUI client. As of 11/3/2020 I was not able to get it to commit changes made through WSL received an error `fatal: Unable to write new index file`  
However commiting the changes via VSCode or CLI works as expected. 