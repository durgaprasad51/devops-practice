# Git Commands 

Create & Clone Repositories

# Create new repository
git init
git init <directory>

# Clone existing repository
git clone <url>
git clone <url> <directory>

# Detailed Explanation#
# Shallow clone (faster for large repos)
git clone --depth 1 <url>

# Clone with submodules
git clone --recursive <url>

# Clone only specific branch
git clone --single-branch -b develop <url>

# Clone private repo (will prompt for credentials)
git clone https://username@github.com/user/repo.git

# Clone specific branch
git clone -b <branch> <url>
# Set user info (required for commits)
git config --global user.name "Your Name"
git config --global user.email "email@example.com"

# Set default branch name
git config --global init.defaultBranch main

# Check settings
git config --list
- History of Git 
   Git has been developed by Linus Torwald
