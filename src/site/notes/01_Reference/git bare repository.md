---
{"dg-publish":true,"permalink":"/01-reference/git-bare-repository/","title":"Git bare repository","tags":["configuration","devops","linux"],"created":"2025-12-05T03:27:51.078+01:00"}
---


# Git bare repository

Backing up dotfiles using a `git bare` repository is a great way to manage, backup and version control them without cluttering `$HOME` directory. Here is a guide on how to set it up to work.

## Initialise bare git repository

```bash
git init --bare $HOME/.dotfiles
```

## Set `alias` for simplicity

```bash
alias config="/usr/bin/git --git-dir=$HOME/.dotfiles --work-tree=$HOME"
```

- `--git-dir=<path>` Set the path to the repository (".git" directory). This can also be controlled by setting the `GIT_DIR` environment variable. It can be an absolute path or relative path to current working directory. Specifying the location of the ".git" directory using this option (or `GIT_DIR` environment variable) turns off the repository discovery that tries to find a directory with ".git" subdirectory (which is how the repository and the top-level of the working tree are discovered), and tells Git that you are at the top level of the working tree. If you are not at the top-level directory of the working tree, you should tell Git where the top-level of the working tree is, with the `--work-tree=<path>` option (or `GIT_WORK_TREE` environment variable) If you just want to run git as if it was started in `<path>` then use `git -C <path>`.

- `--work-tree=<path>` Set the path to the working tree. It can be an absolute path or a path relative to the current working directory. This can also be controlled by setting the GIT_WORK_TREE environment variable and the core.worktree configuration variable (see `core.worktree` in [git-config](https://git-scm.com/docs/git-config) for a more detailed discussion).

## Store the permanent `alias` in a shell config file

Depending on your active shell, you should store the previous alias in one of the following configuration files: `.bashrc`, `.zshrc`, `.profile`. There should be the following line: `alias config="/usr/bin/git --git-dir=$HOME/.dotfiles --work-tree=$HOME"`

```bash
echo "alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'" >> ~/.bashrc
source ~/.bashrc
```

## Ensure untracked files don't interfere

Prevent the git from showing every untracked file in your home directory by calling the alias with another command.

```bash
config config --local status.showUntrackedFiles no
```

## Start tracking dotfiles

Finaly add files or directories you want to track.

```bash
config add .bashrc
config add .vimrc
config add .config/nvim/init.vim
```

## Commit the changes and push to remote

```bash
# commit changes to local git repository
config commit -m "initial commit"

# To back up your dotfiles to github or another git host:
config push -u origin master
```

## Restore on a new machine

When restoring the files on a new machine you should clone the repository, set the alias

```bash
git clone --bare git@github.com:username/dotfiles.git $HOME/.dotfiles
alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
config checkout
```

If there are conflicts with existing files, resolve them or create a backup.

```bash
mkdir -p .dotfiles.bak
config checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | xargs -I{} mv {} .dotfiles.bak/{}
config checkout
```
