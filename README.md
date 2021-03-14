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
      
- ## How to reset to an old revision?
  ```
  git reset --hard <SHA-1 hash>
  ```
  Note: If `--hard` is used then all local changes after the old revision will be deleted. `<SHA-1 hash>` is the old revison's hash number (e.g. ff5297c).
    
  or
  
  ```
  git reset --mixed <SHA-1 hash>
  ```
  Note: If `--mixed` is used then all changes in the removed revisions will be kept as local changes.

- ## How to force your local repo to the remote one?
  ```
  git push -f <remote> <branch>
  ```
  (e.g. `git push -f origin main`)
  
- ## How to Add changes to an old commit with Interactive Rebase?
  ```
  git commit --fixup <the old commit's SHA-1 hash>
  ```
  ```
  git rebase -i HEAD~<number> --autosquash
  ```
  Note: The `<number>` is the position of the old commit's parents (the one before the old commit). (e.g. If the old commit's position is 2, then `<number>` should be 3, please see the image below.)
  
  ![screenshot](https://user-images.githubusercontent.com/13745974/102413262-91730c80-3fec-11eb-948c-183d11f351f7.png)
  
  In the `git` window, type the following keys to save and run the code:
 
  `Esc` `:` `w` `q`
  
  ![screenshot](https://user-images.githubusercontent.com/13745974/102413700-40174d00-3fed-11eb-865d-6f88d5530a22.png)
  
  
- ## How to push an existing repository from local to remote?
  ```
  git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
  git branch -M main
  git push -u origin main
  ```
  
- ## When you use `git branch -M main` and Terminal returns `error: refname refs/heads/HEAD not found` and `fatal: Branch rename failed` message...
  It is in a detached head state. You must `checkout` a new branch to associate it with the current commit:
  ```
  git checkout -b <new branch name>
  ```

- ## How to view current remotes?
  ```
  git remote -v
  ```
  
- ## How to remove a remote URL from your repository?
  ```
  git remote rm <remote name>
  ```
  Note: 
  1. The `<remote name>` could be `origin`, `upstream` or others. 
  2. git `remote rm` does not delete the remote repository from the server. It simply removes the remote and its references from your local repository.

- ## How to create a new branch based on the current HEAD?
  ```
  git branch <new-branch>
  ```
  
- ## How to create a new branch and switch to it at the same time?
  ```
  git checkout -b <new-branch>
  ```
