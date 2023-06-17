## Useful Default Configs

The default branch name for git is "master". Change it to "main" with the line below:
`git config --global init.defaultBranch main`

When working in a new local branch, you pretty much always want to push it to a matching branch name on origin. By default you will need to use `git push --set-upstream <your-branch-name>`, which is verbose. Use the below to just use `git push`.
`git config --global push.default current`

## Initializing a Repo
### Starting local
Initialize a folder using the default branch name (master normally, or see above for changing the default).
`git init`

Initialize a folder with a particular branch name.
`git init -b <branch-name>`

Add all existing files to staged.
`git add .`

Commit all initial files.
`git commit -m "<your-initial-message>"`

### Initializing a local into a remote
Add a remote named "origin" at a URL.
`git remote add origin <https://remote-url.git>`

`git pull origin main --allow-unrelated-histories`