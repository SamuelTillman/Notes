# Claude Code Agents and Skills

Advanced features for automating complex workflows.

## Agents

Agents are specialized sub-processes Claude can spawn to handle specific tasks in parallel or isolation.

### When to Use Agents

- Complex multi-step research across a codebase
- Tasks that benefit from parallel execution
- Work that needs isolation (separate git worktree)
- Long-running background tasks

### Agent Types

| Type | Use Case |
|------|----------|
| `Explore` | Fast codebase exploration, finding files, searching code |
| `Plan` | Designing implementation strategies, architectural decisions |
| `general-purpose` | Multi-step tasks, research, code changes |

### Examples

```
"explore this codebase and summarize the architecture"
"plan how to refactor the authentication module"
"research how error handling works across the project"
```

## Skills

Skills are pre-defined workflows invoked with slash commands.

### Built-in Skills

| Skill | Description |
|-------|-------------|
| `/init` | Initialize a CLAUDE.md file for a project |
| `/review` | Review a pull request |
| `/security-review` | Security review of pending changes |
| `/simplify` | Review code for quality and efficiency |

### Using Skills

```
/init - set up Claude for this repo
/review - review the current PR
/security-review - check for vulnerabilities
```

## CLAUDE.md Files

Project-specific instructions that Claude reads automatically.

### What to Include

- Project structure overview
- Build/test commands
- Coding conventions
- Environment setup
- Common workflows

### Example CLAUDE.md

```markdown
# Project Name

## Build
npm install && npm run build

## Test
npm test

## Deploy
terraform apply -var-file=prod.tfvars

## Conventions
- Use TypeScript strict mode
- All PRs require tests
- Follow conventional commits
```

## Hooks

Automate actions in response to Claude events.

### Use Cases

- Run linters after file edits
- Auto-format code
- Trigger builds
- Send notifications

### Configuration

Hooks are configured in `.claude/settings.json`:

```json
{
  "hooks": {
    "afterEdit": ["npm run lint --fix"],
    "afterCommit": ["npm test"]
  }
}
```

## Tips

- Use agents for tasks that would pollute your main context
- Skills are great for repetitive workflows
- Keep CLAUDE.md concise - Claude reads it every session
- Hooks run automatically, so keep them fast
