- `git init` - starts git for your project
- `git status` - check status of project
- `git add ./filenames` - stage files/make them ready to commit
- `git commit -m "message"` - commit changes/put changes into git history
- `git log` - see git history
- connect to github via ssh pair key always
	- ```git remote add origin git@github.com:YOUR_USERNAME/my-project.git```
	- ```git push -u origin master```
	- it is same ssh-ing to server by username `git@github.com`
- `git push` - push changes to remote repository
- `git diff` - shows code changes
- `git switch -c branch_name` - create branch/switch to the branch
- `git branch -d add-feature` - delete branch
- `git restore ./filename` - discard changes
- undo commit:
```
# Undo commit, keep changes staged
git reset --soft HEAD~1

# Undo commit, keep changes unstaged
git reset HEAD~1

# Undo commit AND discard changes
git reset --hard HEAD~1
```


Links:

202608260129

