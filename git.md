# Git

Git is a powerfull tool. Effective usage can make the usage really smooth, so I gathered a few best practices and tips.

## Usefull commands

### Remove merged branches

```bash
git branch --merged | grep -Ev "(^\*|master|main|dev)" | xargs git branch -d
```

## `.gitconfig`

These configurations I found usefull for myself.

```ini
[core]  
    editor = nano
[user]
        name = Michal Bahník
        email = <e-mail>
[alias]
    # Pretty log
    lg = log --graph --pretty=tformat:'%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
    lga = lg --all # Recursive aliases work in Git 2.30
    # Push new branch upstream
    pu = push origin -u HEAD
    list-aliases = config --get-regexp ^alias\\.
    # Interactive staging and commiting
    ic = !git add -p && git diff --cached && git commit
    # Show local branches sorted from the most recent (useful when working in paralell branches)
    bs = for-each-ref --count=30 --sort=-committerdate refs/heads/ --format='%(HEAD) %(color:yellow)%(refname:short)%(color:reset) - %(contents:subject) - %(authorname) (%(color:green)%(committerdate:relative)%(color:reset))'
    # Get list of files change in current branch
    df = !git --no-pager diff --name-only origin/main...
    # Switch to the last used branch
    sl = switch @{-1}
```

## `.pre-commit-config.yaml`

```yaml
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    hooks:
    -   id: check-yaml
    -   id: end-of-file-fixer
    -   id: trailing-whitespace
    -   id: check-added-large-files
    -   id: check-ast
    - id: check-merge-conflict
    -   id: no-commit-to-branch
        args: ["--branch", "main", '--pattern', '^(?!((feature|fix|hotfix|release)\/[a-zA-Z0-9\-/]+)$).*]

  - repo: https://github.com/astral-sh/ruff-pre-commit
    hooks:
      - id: ruff
      - id: ruff-format
        args: ["--check"]
```
