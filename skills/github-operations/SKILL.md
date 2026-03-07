---
name: github-operations
description: GitHub operations - issues, PRs, releases, repo management
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: version-control
---

## What I do

- Create and manage GitHub issues
- Create pull requests
- Manage releases
- Search repositories
- Manage repo settings

## When to use me

Use GitHub MCP tools when:
- Creating issues or PRs
- Checking repo status
- Managing releases
- Searching code on GitHub

## MCP Tools Available

- `github_get_issue` - Get issue details
- `github_create_issue` - Create new issue
- `github_list_issues` - List repository issues
- `github_search_repositories` - Search for repos
- `github_create_pull_request` - Create PR
- `github_list_pulls` - List PRs
- `github_create_release` - Create release

## CLI Commands

```bash
# Create issue
gh issue create --title "Bug" --body "Description"

# Create PR
gh pr create --title "Feature" --body "Description"

# List issues
gh issue list

# Create release
gh release create v1.0.0 --notes "Release notes"
```
