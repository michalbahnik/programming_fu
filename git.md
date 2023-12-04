# Git

Git is a powerfull tool. Effective usage can make the usage really smooth, so I gathered a few best practices and tips.

## .gitconfig

These configurations I found usefull for myself.

```ini
[core]  
    editor = nano
[alias]
    # Pretty log
    lg = log --graph --pretty=tformat:'%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
    # Push new branch upstream
    pu = push origin -u HEAD
    list-aliases = config --get-regexp ^alias\\.
    # Interactive staging and commiting
    ic = !git add -p && git diff --cached && git commit
    # Show local branches sorted from the most recent (useful when working in paralell branches)
    bs = for-each-ref --count=30 --sort=-committerdate refs/heads/ --format='%(HEAD) %(color:yellow)%(refname:short)%(color:reset) - %(contents:subject) - %(authorname) (%(color:green)%(committerdate:relative)%(color:reset))'
```
