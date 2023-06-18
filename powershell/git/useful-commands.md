# Basics for navigating folders
Reminder for navigating a directory structure in powershell.

- Go up a directory: `cd ..`
- Go to a specific directory: `cd C:\<directory-name>\<child-directory-name>`
- Go to a directory in this one: `cd <directory-name>`
- List files in current directory: `ls`
- Create a directory in current location: `mkdir "<directory-name>"
- Remove a file or directory: `rm "<file-or-directory>"`

# Terminology Overview

- **init** - Sets up a directory as a git repo.
- **branch** - Logical tracking split, enabling changes to be managed and tracked against it, independent of other branches.
- **add** / **stage** - Tracks changes for a commit. 
- **stage** - Mark changes as ready to be committed.
- **commit** - Commit staged changes to the repo.
- **push** - Push local changes to the upstream branch (usually a remote).
- **fetch** - Get latest changes from a remote.
- **merge** - Merges commits from one branch into another.
- **pull** - Shorthand for fetch + merge.
- **switch** / **checkout** - Switch branches.

# Update Git
Make sure you are running latest git. New things are added regularly, and you want the latest and greatest.
`git update-git-for-windows`

Sometimes the above fails due to an SSL issue. If that does happen, and you have winget available, use it as an alterative:
`winget install --id Git.Git -e --source winget`

# Useful Default Configs
The default branch name for git is "master". Change it to "main" with the line below:
`git config --global init.defaultBranch main`

When working in a new local branch, you pretty much always want to push it to a matching branch name on origin. By default you will need to use `git push --set-upstream <your-branch-name>`, which is verbose. Use the below to just use `git push`.
`git config --global push.default current`

Automatically set up remote when pushing.
`git config --global --add --bool push.autoSetupRemote true`

# Initializing

## Initializing a Local Repo
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
Initialize a local repo from a remote.
`git clone <https://remote-url/some-repo>`

# Branching
## List branches
List local branches.
`git branch`

List remote branches.
`git branch -r`

List both local and remote branches.
`git branch -a`

## Creating a branch
Create a new branch from your existing branch, with the name specified.
`git checkout -b <new-branch-name>`

Or, you can create the branch and then switch to it.
`git branch <new-branch-name>`
`git switch <new-branch-name>`

## Switching branches
`git switch <target-branch>`

## Remove a branch
Remove local branch.
`git branch -d <branch-name>`
Additionally, if you have commits which have not been merged (and therefore will be lost entirely when you delete), you can use:
`git branch -D <branch-name>` or
`git branch -d -f <branch-name>` to force the delete.

Remove remote branch.
`git push origin -d <branch-name>`
or, since `-d` is short for `--delete`, you can use:
`git push origin --delete <branch-name>`

After the branch is removed from both local and remote, you must prune the obsolete tracking branch or else it will continue to appear in `git brnach -a`.
`git fetch --all --prune`

# Reset local changes to match remote
You may want to `git fetch --all` first. The below will revert all local changes so that your local repo matches the target branch.
`git reset --hard origin/<branch-name>`