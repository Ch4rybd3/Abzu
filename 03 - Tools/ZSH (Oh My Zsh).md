---
Type: "[[Tools]]"
date: 2026-01-07
tags:
  - Terminal
  - Productivity
Input: no specific
Output: no specific
Description: a terminal with a tons of useful plugins and themes
Platform:
  - Linux
---
# Overview
Zsh is another terminal, just like bash, but with the extension "Oh My Zsh", it become a really simple to configure and powerful tool.
The main advantages are : 
- Themes (lots of thèmes, so you can have different options of prompt including githu branches, folder paths, date/time, ...)
- Plugins (the main thing, you get advanced auto completions, colors, etc)
- Custom commands that make it faster to navigate and search the filesystem
# Usage
Shortcuts
```shell
.. # cd ..
... # cd ../..
Documents # cd Documents/
ls **/*json # search for all json files in subfolders
```
Changing the ZSH config (themes and plugins)
```shell
nano ~/.zshrc # edit the config
source ~/.zshrc # reload the terminal (and config)
```
# Plugins
```shell
# Download Syntax Highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# Download Auto-suggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

For native plugins, you don't have to DL anything.
Here's an example of a curated, DFIR oriented plugin variable
```shell
plugins=(
  git
  sudo
  extract
  encode64
  urltools
  history
  colored-man-pages
  zsh-autosuggestions
  zsh-syntax-highlighting
)
```

-   git : shortcuts for using git
  - sudo : double press on the escape key input a sudo at the start of the prompt in case you forgot
  - extract : extract archives in 2 words, works with all formats, .zip, .tar.gz, 7z, ...
  - encode64 : `| en64` or `| de64` to encode or decode base64 strings 
  - urltools : `urldecode "http%3A%2F%2Fgoogle.fr"` to a human readable url
  - history : search through the history for strings like `hs docker
  - colored-man-pages : do as its name implies, color the man pages
  - zsh-autosuggestions : auto-suggest in grey based on the history, really useful
  - zsh-syntax-highlighting : if command is incorrect, is red, if correct, is green
# Screenshot