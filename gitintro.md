1. git clone (the link to the repository youwant to clone)
2. git remote -v
  - list things
3. git remote add upstream (the upstream link)
1. git pull upstream master
  - take the changes from the upstream

# Branching
- list branches: `git branch`
- create a new branch: `git branch <branch name>`
- go to another branch: `git branch <branch you want to go>`
- delete a branch `git branch -d <branch>`
- push to a branch: `git push origin <branch>`
- submit a pull request, "new pull request" in the main directory
  - submit it to the upstream
  - comment: Make a description that is meaningful. What's different about this version vs the previous one.
- `git checkout <branch> <file>`
  - take a file from another branch
