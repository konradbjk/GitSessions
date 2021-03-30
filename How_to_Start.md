# How to start working with Git
**Disclaimer**: below commands are working for UNIX/LINUX based OS. For Windows use terminal emulator such as [cmder](https://cmder.net/) or install Ubuntu.

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

## moving my project to github
1. Initialize the git
2. Remove sensitive data and make sure you have good ```.gitignore```
3. Add the files inside repository
4. Add remote (```git remote add origin <REMOTE_URL>```) and check if it is right (```git remote -v```)
5. Push the changes (```git push -u origin main``` or ```git push -u origin --all```)

## Using SSH keys
```
ssh-keygen -t ed25519 -C "your_email@example.com"
```
in the name, make sure to post the full path (or run it from within ~/.ssh folder)

Modify your ssh config file (```~/.ssh/config```) to reflect the ssh key.

Test connection
```
ssh -T github.com
```

[Generating SSH key](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
[Adding SSH key to the GitHub account](https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)

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