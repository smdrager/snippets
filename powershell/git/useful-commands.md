## Basics for navigating folders
Reminder for navigating a directory structure in powershell.

- Go up a directory: `cd ..`
- Go to a specific directory: `cd C:\<directory-name>\<child-directory-name>`
- Go to a directory in this one: `cd <directory-name>`
- List files in current directory: `ls`
- Create a directory in current location: `mkdir "<directory-name>"
- Remove a file or directory: `rm "<file-or-directory>"`

# Overview

- **init** - Sets up a directory as a git repo.
- **branch** - 
- **add** / **stage** - Tracks changes for a commit. 
- **stage** - Mark changes as ready to be committed.
- **commit** - Commit staged changes to the repo.
- **push** - Push local changes to the upstream branch (usually a remote).
- **fetch** - Get latest changes from a remote.
- **merge** - Merges commits from one branch into another.
- **pull** - Shorthand for fetch + merge.

## Update Git
Make sure you are running latest git. New things are added regularly, and you want the latest and greatest.
`git update-git-for-windows`

Sometimes the above fails due to an SSL issue. If that does happen, and you have winget available, use it as an alterative:
`winget install --id Git.Git -e --source winget`

## Useful Default Configs
The default branch name for git is "master". Change it to "main" with the line below:
`git config --global init.defaultBranch main`

When working in a new local branch, you pretty much always want to push it to a matching branch name on origin. By default you will need to use `git push --set-upstream <your-branch-name>`, which is verbose. Use the below to just use `git push`.
`git config --global push.default current`

Automatically set up remote when pushing.
`git config --global --add --bool push.autoSetupRemote true`

## Initializing a Local Repo
### Starting local
Initialize a folder using the default branch name (master normally, or see above for changing the default).
`git init`

Initialize a folder with a particular branch name.
`git init -b <branch-name>`

Add all existing files to staged.
`git add .`

Commit all initial files.
`git commit -m "<your-initial-message>"`

## Initializing a Local into a Remote
Add a remote named "origin" at a URL.
`git remote add origin <https://remote-url.git>`

If the repo is empty you can just push your local committed changes to it.
`git push`

If there were already some files on the remote (such as a license file), use the following the pull them.
`git pull origin main --allow-unrelated-histories`

## Initializing a Remote into a Local
Super easy.
`git clone <https://remote-url.git>`