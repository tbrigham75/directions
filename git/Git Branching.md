git checkout -b fix-codereay-as - Checks out a new branch

git branch

- Do your fixes and commits

git add .
 
git commit -m "what u did"

git push -u origin nameofcheckedoutbranch or git push --set-upstream origin fix-codeready-as - Pushes branch to origin (Can use -u inplace of --set-upstream)

git push -o merge_request.create -u origin add-node-health-check  <-- Pushes to origin and does MR

git checkout master - Checks master back out

- Do a merge in Web Interface

git pull

git status

git branch -d fix-codeready-as - Deletes local branch

git branch -D

git fetch -p (retrives metadata, git pull retrieves)

git branch -a - list all


If you accidently modify a file you can (I'd copy and paste any other good changes first so you don't lose those):

git stash
git drop

git pull --prune

can mark files as .ignorefile to skip files when committing:
https://www.pluralsight.com/guides/how-to-use-gitignore-file



To Rebase:

git checkout branchurworking
git rebase master
git status (Look for file conflict info
vi and change the files
git rebase --continue
git push --force
git branch master
git pull

If I'm on a branch is there a way to git pull and update the branch while keeping my changes?
Yes git pull will do it... but if Tim deletes a branch while approving it does not work.
git branch -a 			- list all
git pull --prune		- prunes all branches master doesn't know about



