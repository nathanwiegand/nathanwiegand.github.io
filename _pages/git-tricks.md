---
layout: post
title: "Git Tricks"
date: 2024-04-03 14:07:00
categories: pages
---

## Git tricks

### update
```bash
alias update='git fetch origin && git merge orgin/main'
```

### don't commit to main
Important for working with a team where everyone works on the same repo and has dev branches.

Add a new pre-commit hook in your repo.
```bash
# .git/hooks/pre-commit
#!/bin/sh

branch="$(git rev-parse --abbrev-ref HEAD)"

if [ "$branch" = "main" ]; then
  echo "You are on branch $branch. Commits directly to this branch are not allowed."
  exit 1
fi
```
