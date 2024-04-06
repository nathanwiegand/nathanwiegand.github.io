## Git tricks

### update
```bash
alias update='git fetch origin && git merge orgin/main'
```

### Don't commit to main
Important for working with a team where everyone works on the same repo and has dev branches.
```bash
#!/bin/sh

branch="$(git rev-parse --abbrev-ref HEAD)"

if [ "$branch" = "main" ]; then
  echo "You are on branch $branch. Commits directly to this branch are not allowed."
  exit 1
fi
```
