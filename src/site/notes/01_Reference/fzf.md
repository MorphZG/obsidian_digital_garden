---
{"dg-publish":true,"permalink":"/01_Reference/fzf/","title":"Fuzzy Finder FZF","tags":["linux","utility"]}
---


# Fuzzy Finder FZF

Open source fuzzy finder, can be downloaded from the [github.com/junegunn/fzf](https://github.com/junegunn/fzf)

## Installation

Clone the repository and run the install script.

```shell
git clone --depth=1 https://github.com/junegunn/fzf && cd fzf && ./install
```

> Would be good to update from time to time by running the command from the cloned fzf directory:
> `git pull && ./install`

## Daily usage

### Keybinds

Check out the [wiki page](https://github.com/junegunn/fzf/wiki/Configuring-shell-key-bindings) for more tips on how to configure shell key bindings.

- `ctrl-t` - Paste the selected files or directories into the prompt. Type the command into terminal and press the keybind to activate the search. Set the `$FZF_CTRL_T_COMMAND` to change the key or `$FZF_CTRL_T_OPTS` to add additional options like adding the preview

```shell
export FZF_CTRL_OPTS="
--preview 'bat -n --color=always {}'
--bind 'ctrl-/:change-preview-window(down|hidden|)'
"
```

- `ctrl-r`  Browse the history of commands and paste the selected command onto the prompt. To view the history in chronological order press the `ctrl-r` again, it toggles sorting by relevance. `$FZF_CTRL_R_OPTS` can hold additional options.

```shell
# ctrl-/ to toggle small preview window to see the full command
# ctrl-y to copy the command into the clipboard using pbcopy
export FZF_CTRL_R_OPTS="
--preview 'echo {}' --preview-window up:3:hidden:wrap
--bind 'ctrl-/:toggle-preview'
--bind 'ctrl-y:execute-silent(echo -n {2..} | pbcopy)+abort'
--color header:italic
--header 'Press CTRL-Y to copy command into clipboard'
"
```

- `alt-c` cd into selected directory. Set `FZF_ALT_C_COMMAND` to override the default. Set `FZF_ALT_C_OPTS` to pass additional options.

```shell
# print tree structure in the preview window
export FZF_ALT_C_OPTS="--preview 'tree -C {} | head -300'"
```

## Configuration
