# GNOME Ubuntu setup

## Themes

Install the `numix-icon-theme-circle` theme

```bash
$ sudo apt-add-repository ppa:numix/ppa
$ sudo apt-get update
$ sudo apt-get install numix-icon-theme-circle
```

In `Tweak Tool`, set `GTK+` theme to be `Numix` and `Icons` theme to be `Numix-Circle`.

## GUI applications

- Google Chrome
    - Chrome extensions
- Spotify
- Netease Music

## System settings

### Input method
    
Add `Chinese (pinyin)` as one of the input sources.

### Key mapping

Switch CapsLock and left Ctrl key

### Font

[Modify the priority of Noto Sans CJK](https://www.zhihu.com/question/47141667/answer/104906870)

## Terminal

### Shell

Use Zsh (together with oh-my-zsh) instead of Bash

```bash
$ sudo apt-get install -y zsh
$ sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

### Terminal appearance

First, install the base16 theme for GNOME Terminal

```bash
$ git clone https://github.com/chriskempson/base16-shell.git ~/.config/base16-shell
$ echo 'BASE16_SHELL=$HOME/.config/base16-shell/
[ -n "$PS1" ] && [ -s $BASE16_SHELL/profile_helper.sh ] && eval "$($BASE16_SHELL/profile_helper.sh)"' >> ~/.zshrc
$ source ~/.zshrc
$ base16_default-dark
```

Then change the font for terminal to the [Input font](http://input.fontbureau.com/download/) (`InputMonoNarrow-Light.ttf`)

### Terminal applications

#### SSH

Generate a key pair for use with SSH

```bash
$ ssh-keygen -t rsa
```

#### Git

First install Git with

```bash
$ sudo apt-get install -y git
```

Username and email should be configured for Git before commiting anything.

```bash
$ git config --global user.name "Siyuan Liu"
$ git config --global user.email "weifengzi2009@gmail.com"
```

Store public key generated with `ssh-keygen` on GitHub.

#### Vim

Install Vim with

```bash
$ sudo apt-get install -y vim
```

Create `~/.vimrc` with the content from my [dotfile repo](https://github.com/koallen/dotfiles). Then install all the plugins with Vundle

```bash
$ wget -O ~/.vimrc https://raw.githubusercontent.com/koallen/dotfiles/master/.vimrc
$ git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
$ vim +PluginInstall +qall
```
