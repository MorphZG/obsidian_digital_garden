---
{"dg-publish":true,"permalink":"/01-reference/awesome-window-manager/","title":"Awesome window manager","tags":["window_manager","linux"]}
---


# Awesome window manager

## installation and basic configuration

```shell
sudo apt update
sudo apt install awesome awesome-doc awesome-extra
mkdir -p ~/.config/awesome
sudo cp /etc/xdg/awesome/rc.lua ~/.config/awesome/rc.lua
sudo cp /usr/share/awesome/themes/default/theme.lua ~/.config/awesome/theme.lua
```

### rc.lua

After saving the changes to the config file, press `ctrl + mod + r` to reload the window manager.

Global layout selection is available at the upper right corner of the screen. Switch between them by clicking the mouse. It is good to comment out layouts you will not use:
`awful.layout.layouts = {}`

### theme.lua

Help window with keybinds, change the colors to improve visibility:
`theme.hotkeys_modifiers_fg = "#FFFFFF"`
`theme.hotkeys_label_fg = "#111111"`

## Usefull shortcuts

`mod + s` - display keybinds
`mod + r` - run prompt
`mod + return` - open terminal

## read more

- [youtube.com/video](https://www.youtube.com/watch?v=WKdoC_VB2tU) "An Intro To Awesome WM, Your First Tiling Window Manager" by Vashinator
