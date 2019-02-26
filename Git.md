# Git

## Git Ignore



The problem is that .gitignore ignores just files that weren't tracked before (by git add). 
Run git reset name_of_file to unstage the file and keep it. 
In case you want to also remove given file from the repository (after pushing), use git rm --cached name_of_file.
