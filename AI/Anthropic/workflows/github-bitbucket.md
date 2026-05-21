# GitHub & Bitbucket with Claude Code

Practical examples for using Claude Code with GitHub and Bitbucket.

## GitHub CLI (gh)

### Pull Requests

```
"create a PR from this branch to main"
"list open PRs"
"show PR #123"
"check the status of PR #123"
"merge PR #123"
"add a comment to PR #123"
"request review from @username on PR #123"
```

### Issues

```
"list open issues"
"create an issue titled 'Fix S3 permissions'"
"close issue #45"
"show comments on issue #45"
```

### Actions/Workflows

```
"show recent workflow runs"
"check status of the latest CI run"
"re-run failed workflow"
"show logs for workflow run 12345"
```

### Releases

```
"list releases"
"create a release v1.2.3"
"show release notes for v1.2.0"
```

### Repository

```
"clone repo owner/repo-name"
"fork this repo"
"show repo settings"
"list collaborators"
```

## Bitbucket

Claude can use Bitbucket via API or git commands:

```
"push this branch to bitbucket"
"create a pull request on bitbucket"
"list branches on the remote"
```

## Common Workflows

### Feature Branch Flow
```
1. "create branch feature/new-thing"
2. "commit my changes"
3. "push to origin"
4. "create a PR to main"
5. "check CI status"
6. "merge when ready"
```

### Hotfix Flow
```
1. "create branch hotfix/urgent-fix from main"
2. "make the fix and commit"
3. "create PR with expedited review"
4. "merge and tag release"
```

### Code Review
```
"show the diff for PR #123"
"list files changed in PR #123"
"show comments on PR #123"
"approve PR #123"
```

## Tips

- Make sure `gh` CLI is installed and authenticated for GitHub operations
- Claude can help write good PR descriptions summarizing changes
- Ask Claude to check CI status before merging
- For Bitbucket, you may need to configure API tokens
