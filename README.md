# My git note

- ## How do I keep my Git fork up to date?
  ### `Situation A`: When you don't have the repository in your local machine.

  1. Clone your fork:
      ```
      git clone git@github.com:YOUR-USERNAME/YOUR-FORKED-REPOSITORY.git
      ```

  2. Add remote from original repository in your forked repository:
      ```
      cd into/cloned/fork-repo
      git remote add upstream git://github.com/ORIGINAL-DEV-USERNAME/REPOSITORY-YOU-FORKED-FROM.git
      git fetch upstream
      ```
  
  3. Updating your fork from original repo to keep up with their changes:
      ```
      git pull upstream main
      ```
      Note: You can pull any other branch from the original repo, just change the `main` to the `branch name`. Sometimes, the main branch is called `master`.
  
  ### `Situation B`: When you already have the repository in your local machine.
  > `Important`: If you have any local changes, they will be lost. With or without --hard option, any local commits that haven't been pushed will be lost.
  1. Run a fetch to update all `origin/<branch>` refs to latest:
      ```
      git fetch --all
      ```
  
  2. Backup your current branch:
      ```
      git checkout -b backup-main
      ```
      
  3. Reset your local master branch to what you just fetched. 
      ```
      git reset --hard upstream/main
      ```
      
      **Explanation:**
      
      - `git fetch` downloads the latest from remote without trying to merge or rebase anything.

      - Then the `git reset` resets the local main branch to what you just fetched. 

      - The `--hard` option changes all the files in your working tree to match the files in upstream/main
      
      
- ## How to force your local repo to the remote one?
  ```
  git push -f <remote> <branch>
  ```
  (eg. `git push -f origin main`)
