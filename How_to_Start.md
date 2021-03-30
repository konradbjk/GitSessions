# How to start working with Git

## Git config
Global vs Repository based
```
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```
Our global config is saved in ~/.gitconfig, while local in git/config file

What is the defaul text editor for Git in macOS? (parameter core.editor)

```
git config --global -e
```

## Usefull Aliases
```
alias gs='git status'
alias ga='git add'
alias gb='git branch'
alias gc='git commit'
alias gd='git diff'
```
And aliases due to typos
```
alias got='git'
alias get='git'
```