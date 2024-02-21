Refer to this website:  https://bytescout.com/blog/setup-and-use-git-repositories-for-one-project.html

If you are working on a big project, then it is inevitable that you need to work with multiple repositories.

That’s why you need to sync your local code base with multiple Git remote repositories.

For example, if your source code is:
On Github for issues tracking
On Heroku for production
On Some Other Git repo
Here is the step-by-step instruction on setting up a project to sync with multiple git repositories. For example, we will take multiple repositories: one on Github and another on Heroku.

But before we go forward and discuss how to set up and use multiple Git repositories, let’s quickly go through the reasons why we need to do so.

You may need to use multiple Git repositories where the codebase is too big and hence cannot be maintained from one single repository. When we say big, it can reach a size of petabytes! That’s why it is necessary to use multiple Git repositories.

Another big benefit that comes with using multiple repositories is that it can make teamwork efficient without the need to depend on each other. This means that they can work independently and work faster than ever.

However, there are obvious challenges that come with managing multiple repositories for a single project. These challenges include the following:

Managing dependencies across repos;
Understanding and finding reliable truth sources;
Managing and enforcing workflows;
Reviewing changes that are made via Git pull requests;
Resolving conflicts;
Making rollbacks and changes using repos sync;
Finding a source of truth that is reliable;
Identifying repos that have uncommitted changes;
Enforcing workflows can be a challenge as well.
What we have for this tutorial:
Git repository on Github: /my-company/my-project
Git repository on Heroku, where the project is also named “my-project“
The need to work with both repositories at the same time
Important: before you make any changes, please make a backup of the local folder with your project.
1. First clone your project from one of these repositories like this:

2. Clone the repository from Github:

git clone git@github.com:my-company/my-project.git

3. Open the folder with the cloned project:

cd my-project
4. Now we will manually edit Git repository‘s configuration file where we will add the second repository as a new remote source.
Open .git/config file. If you can’t find .git subfolder then make sure you have enabled the showing of hidden subfolders on your system.
This file (.git/config) will look like this in your editor. This is the content of the config file automatically generated once you’ve cloned it from Github.
[core]
repositoryformatversion = 0
filemode = true
bare = false
logallrefupdates = true
[remote "origin"]
url = git@github.com:my-company/my-project.git
fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
remote = origin
merge = refs/heads/master

5. As you see, when you have one single repository, it is called “origin” by default. If we have two or more remote repositories then we should name each of them using unique(!) names. Also, do not hesitate to add empty lines for more readable code, empty lines will be ignored by git so no worries.
So, now rename “origin” into “github” and  config will look like this:
[core]
repositoryformatversion = 0
filemode = true
bare = false
logallrefupdates = true
[remote “github“]
url = git@github.com:my-company/my-project.git
fetch = +refs/heads/*:refs/remotes/github/*
[branch “master”]
remote = github
merge = refs/heads/master
From now on if you want to push to this repository you will have to write “git push GitHub master” instead of just “git push“. To pull you should type “git pull GitHub master” as well.
6. Now it is time to add the second repository into the config. Duplicate the code starting from [remote.. and up to the end so you will get this code:
[core]
repositoryformatversion = 0
filemode = true
bare = false
logallrefupdates = true
[remote “github”]
url = git@github.com:my-company/my-project.git
fetch = +refs/heads/*:refs/remotes/github/*
[branch “master”]
remote = github
merge = refs/heads/master
[remote “github”]
url = git@github.com:my-company/my-project.git
fetch = +refs/heads/*:refs/remotes/github/*
[branch “master”]
remote = github
merge = refs/heads/master
7. Now rename “github” into “heroku” in the copied section so you will get this:
[core]
repositoryformatversion = 0
filemode = true
bare = false
logallrefupdates = true
[remote “github”]
url = git@github.com:my-company/my-project.git
fetch = +refs/heads/*:refs/remotes/github/*
[branch “master”]
remote = github
merge = refs/heads/master
[remote “heroku“]
url = git@github.com:my-company/my-project.git
fetch = +refs/heads/*:refs/remotes/heroku/*
[branch “master”]
remote = heroku
merge = refs/heads/master
8. Also now change “url” in the “heroku” section to the URL for Heroku’s git repository accordingly:
[core]
repositoryformatversion = 0
filemode = true
bare = false
logallrefupdates = true
[remote “github”]
url = git@github.com:my-company/my-project.git
fetch = +refs/heads/*:refs/remotes/github/*
[branch “master”]
remote = github
merge = refs/heads/master
[remote “heroku“]
url = https://git.heroku.com/my-project.git
fetch = +refs/heads/*:refs/remotes/heroku/*
[branch “master”]
remote = heroku
merge = refs/heads/master
9. Congratulations! Now you may pull from and push to both git repositories like this:
To push:
git push heroku master
git push github master
To pull:
git pull heroku master
git pull github master
The usual workflow when working with the code synced to two or more repositories looks like this:
make changes in the code of the project;
use git add command to add changed/updated files as usual;
make a commit using git commit command as usual;
push code changes to the first repository: git push github master ;
then push code changes to the second repository: git push heroku master.
Other ways to manage and work with multiple Git Repository
The above method works, but you can also opt for other ways to work with multiple Git Repositories. These methods include the following:

Using Git Submodules
Multiple Git Repositories With Repo
Using Gita
Using Perforce to manage multiple Git repositories within one project

Using Git Submodules
One of the easiest ways to manage multiple repositories is to use Git Submodule. But what is a submodule?

Submodule helps you to embed a foreign git repository content to yours. This way, you can work on a big project and also ensure that versions work as intended. Submodules easies the process by ensuring that a submodule only works on locked versions. So in case you need to work on a new version, you simply need to update the module and then do commit to the outer repository.

There are obviously pros and cons of the approach. The pros include the ability to do atomic commits. You can also take advantage of tools that come with the default Git install.

But what about the cons? Well, one big risk is a security risk. In this approach, it is possible to change configurations and execute code remotely. For now, the vulnerabilities have been fixed, but it does showcase. Other cons include a learning curve and additional setup.

Multiple Git Repositories With Repo
Repo is another useful utility that you can use to manage multiple repositories. It is used for one of the most popular codebase repo: Android. The repo helps you to work on modules or functionalities that you can think are worth your time.

The advantage of Repo is that it is well documented, and it works with Gerrit. The downside is that it works for one workflow and hence is not an ideal pick for alternate workflow designs.

Using Gita
What if you could have a convenient command-line tool that you can use to check and track the status of multiple git repos and make necessary changes.

Gita is a command-line tool that is made to manage git repos.

There are two primary features:

You can display the status of multiple git repos. You can view branches, modifications, commit messages, etc. side by side.
You can delegate git commands or aliases and shell commands on repos from any working directory in a batch.
Some basic commands that you can use in Gita are:

`gita add <repo-paths>` – used to add repos
`gita ll` – display information about the repos
`gita <cmd> <repo-name>` – delegate commands
To kick it up a notch, you can use the following intermediate commands:

`gita group` – to group multiple repos together
`gita context` – used to view context
<group-name>
Auto
`gita add -a <folder-name>` – used to make groups automatically
`gita super` – can be used for any git command
`gita shell` – used to execute any shell command

Using Perforce to manage multiple Git repositories within one project
The last alternative method that you can use is Perforce. It is a combination of two Git tools that you can use to manage multiple repositories within one project.

The two tools are HelixTeamHub and Helix4Git Do. Here, HelixTeamHub lets you work with multiple repositories, whereas the developers can use Helix4Git to contribute to the sub-projects or repositories.

Perforce works great with projects as it offers benefits such as a single source of truth, global scale, faster builds, IP protection, and replication. The only cons that it has included is admin expertise.