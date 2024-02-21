https://komodor.com/learn/how-to-fix-fatal-refusing-to-merge-unrelated-histories-error/

git pull origin master --allow-unrelated-histories

The idea behind --allow-unrelated-histories is that git lets you merge unrelated branches. This git flag works seamlessly when there are no file conflicts.

However, in reality, at least one thing pops up, and you will need to use the normal Git resolution flow to resolve them.

git pop: ‘pops’ the changes from the stash and applies them to the current code
git stash apply: keeps the changes in the stash and applies the changes to the current code