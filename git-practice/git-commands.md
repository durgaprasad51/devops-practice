
# GIT Initial Setup and commands

### Install Git on ubuntu

sudo apt-get update -y
sudo apt-get install git

git --version           =>  verify the installtion of GIT

sudo apt-get upgrade git    => to upgrade the already installed version of GIT

### Config GIT

mkdir (project directory)

git init =>  run command inside proj dir ti initialize the git 

*Git uses your name and email to label your commits*

git config --global user.name "Your Name"
git config --global user.email "you@example.com" 

### view git configuration

git config --list

git config user.name    =>  view a specific settings

### Git Show

### Git Restore

### Git Clean

### Git Remote Add

### Git Tag 

### Tracking a file

### Branching 

### Push/Pull {ssh / pat}

### Rebash 

### Merge

### Stash / Stash pop

### Cherry Picking

### Squash commit 

### Merge Commit

### Reset

### Revert

### Branching Stratigies

### GitHub CLI

### Confilict Resolution

### Git Ignore


Command	                Purpose


git init        =>      Initialize a new Git repository

git clone       =>      Create a local copy of a remote repository

git status      =>      Show the current status of files

git add         =>      Stage files for commit

git commit      =>      Save staged changes to repository history

git branch      =>      List or create branches

git checkout    =>      Switch branches

git merge       =>      Merge changes from another branch

git fetch       =>      Download changes from remote repository

git pull	    =>      Fetch and merge remote changes

git push	    =>      Upload commits to remote repository

git reset	    =>      Undo commits or staging changes

git revert	    =>      Create a commit that reverses previous changes
