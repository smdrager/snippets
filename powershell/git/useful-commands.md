## Useful Defaults

The default branch name for git is "master". Change it to "main" with the line below:
`git config --global init.defaultBranch main`

When working in a new local branch, you pretty much always want to push it to a matching branch name on origin. By default you will need to use `git push --set-upstream <your-branch-name>`, which is verbose. Use the below to just use `git push`.
`git config --global push.default current`