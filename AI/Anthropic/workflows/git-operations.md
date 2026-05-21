# Git Operations with Claude Code

Practical examples for using Claude Code to manage git workflows.

## Common Operations

### Check status and stage changes
```
"check git status"
"stage all modified files"
"stage only the terraform files"
```

### Commits
```
"commit with message: fix lambda timeout"
"show me the last 5 commits"
"what changed in the last commit"
```

### Branches
```
"create a new branch called feature/add-s3-bucket"
"switch to main"
"list all branches"
"delete the feature/old-stuff branch"
```

### Diffs and History
```
"show diff against main"
"what files changed between main and this branch"
"who last modified outputs.tf"
"show git blame for line 45 of main.tf"
```

### Merging and Rebasing
```
"merge main into this branch"
"rebase onto main"
"resolve merge conflicts in variables.tf"
```

### Stashing
```
"stash my current changes"
"list stashes"
"apply the most recent stash"
```

## Tips

- Claude will ask for confirmation before destructive operations (force push, reset --hard)
- You can ask Claude to explain what a git command does before running it
- For complex merges, ask Claude to walk through conflicts one by one
