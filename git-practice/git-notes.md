# GIT

*Git is a popular version control system that helps teams track and manage code changes, collaborate seamlesslyand work on projects of any size. It keeps a history of every change, allowing you to revisit or restore previous versions and makes it easy to fix mistakes without losing progres.

It was created by Linus Torvalds in 2005, and has been maintained by Junio Hamano since then.


### Key Git Concepts

Repository      =>  A folder where Git tracks your project and its history.

Clone           =>  Make a copy of a remote repository on your computer.

Stage           =>  Tell Git which changes you want to save next.

Commit          =>  Save a snapshot of your staged changes.

Branch          =>  Work on different versions or features at the same time.

Merge           =>  Combine changes from different branches.

Pull            =>  Get the latest changes from a remote repository.

Push            =>  Send your changes to a remote repository.

### GIT Config

*Configuration Levels - There are three levels of configuration:

System (all users): git config --system

Global (current user): git config --global

Local (current repo): git config --local

The order of precedence is:

*Local (current repo)

*Global (current user)

*System (all users)

The reason to use the different levels is that you can set different values for different users or repositories.

This can be used for example to set different default branches for different repositories and users.


Example: Set a Local Config 
  
git config user.name "Project Name" => Local settings only apply to the current repository.

Example: Set a Global Config

git config --global user.name "Global Name" => Global settings apply to all repositories for the current user.

Example: Set a System Config

git config --system user.name "System Name" => System settings apply to all repositories for all users.

### GIT Staging

The staging environment (or staging area) is like a waiting room for your changes. You use it to tell Git exactly which files you want to include in your next commit.

### Git Workflow

<img width="800" height="533" alt="git-workflow-overview" src="https://github.com/user-attachments/assets/2c1a54b9-f0cd-43c5-9093-c4753d7b5d1f" />


-------------------------------------------------------------------------------------------------------------

Git

- History of Git (done)
- File System vs VCS (done)
- git commands (git init, git status, git add, git config, git commit, git rm)
- Tracking a file to git (done)
- Branching (git branch, git checkout -b , git checkout -b , git switch -c)
GitHub

- Clone  vs Fork (done)
- Push / Pull to GitHub (done) [ssh / pat]
- Rebase (do branches ki commit history ko ek sequence me laane ka command hota hai) vs Merge (ek branch ki commit history ko doosre ke branch me add karne ke liye use hota hai)
- Stash & stash pop (done)
- Cherry Picking (done)
- Squash commit(ye wala tareeka multiple commits ko ek commit banake merge kar deta hai) vs Merge Commit (ye special type ka commit message hota hai, jab aap ek branch ki PR doosre me merge karte ho)
- Reset vs Revert (done)
- Branching Strategies (done)
- GitHub CLI (done)
- Conflict resolution (done)

