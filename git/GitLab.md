Purpose:  Provide enough info to get started with Git.  The below instructions will talk you through cloning a remote Git repo, committing changes to a local repo, and pushing changes back to the remote repo.  This set of directions will not go into detail on installing software or configuring SSH.  That said I did a default install of the Windows Git… tweaking what text editor I wanted:  Notepad++.  

1.	Install Git for Windows:  https://git-scm.com/download/win
2.	Setup SSH
Notes:  
a.	Use RSA keys, I had issues with ED25519 Keys.
b.	Not Best Security Practice, but hint:  Either remember the password you set, or leave it blank.  Up to individual.)
3.	Open the Git Bash program.
4.	Create a folder you want to clone the repo to.  
My example:  mkdir ~/gitrepos 
(Note: ~ =’s your home directory in Bash)
5.	Change into that directory:  
cd ~/gitrepos
6.	Logon to the GitLab website, find the Repo you want copy, locate the Clone button and copy the text.  In this case it is:  git@gitlab.dev.org:TBRIGHAM/scripts.git
7.	Clone a local copy of the remote repo using the text you copied from above: 
Useful Tip:  To paste within the Git Bash shell use:  Shift Insert
git clone git@gitlab.dev.org:TBRIGHAM/scripts.git
8.	Verify it cloned successfully.  At minimal there should be a hidden .git folder, if created a README.md, and any files the Admin created in the Repo:
ls -ah
9.	You can modify all files locally without messing with the Master Repo, later during the Push to the remote Repo, if you don’t have modify rights it will not allow you to push.  Create or modify a file.  This can be done through Windows Explorer or a Text Editor.  My Example:  Create a Test.txt file in ~/gitrepos
10.	Get your status (You should see Red text if you have added new files):
git status
11.	Mark all to be committed (Adds all to be updated, the dot is a wild card):
git add . 
12.	Check status (You should see green new file ready for the Commit)
git status
13.	Commit your changes to the local repo.  The -m passes a descriptive message such as Initial Comment, Fixed Code, or some other descriptive reason for the update.  If you omit it, then a text document will open and wait for you to add a comment in.
git commit -m “Initial Commit”
14.	git status
15.	Push the Local to the Remote.  (May not be able to do this step - Must have modify rights to the Repo)
By default, all Locals are called origin.  Master is the default if you have no branches:
git push origin master
16.	Another status should show your branch up to date and nothing to commit:
git status

