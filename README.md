# GNOME Ubuntu setup

## Themes

### Icon theme

Install the `numix-icon-theme-circle` theme

```bash
$ sudo apt-add-repository ppa:numix/ppa
$ sudo apt-get update
$ sudo apt-get install numix-icon-theme-circle
```

In `Tweak Tool`, set `Icons` theme to be `Numix-Circle`.

### GTK & GNOME shell theme

Install the `arc-theme`

```bash
$ sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_16.04/ /' > /etc/apt/sources.list.d/arc-theme.list"
$ sudo apt-get update
$ sudo apt-get install arc-theme
```

Set `GTK+` theme and `Shell theme` to be `Arc-Dark`.

(**Note**: Shell theme may be disabled by default, the `User themes` GNOME extension need to be enabled first)

## GUI applications

### Google Chrome

[Download Google Chrome](https://www.google.com/chrome/browser/desktop/index.html)

### Spotify

```bash
$ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys BBEBDCB318AD50EC6865090613B00F1FD2C19886
$ echo deb http://repository.spotify.com stable non-free | sudo tee /etc/apt/sources.list.d/spotify.list
$ sudo apt-get update
$ sudo apt-get install spotify-client
```

### Netease Music

[Download Netease Music](http://s1.music.126.net/download/pc/netease-cloud-music_1.0.0_amd64_ubuntu16.04.deb)

### Slack

[Download Slack](https://downloads.slack-edge.com/linux_releases/slack-desktop-2.4.2-amd64.deb)

## System settings

### Input method
    
Add `Chinese (pinyin)` as one of the input sources.

### Key mapping

Set these in GNOME Tweak Tool

- Swap CapsLock and left Ctrl key
- Swap Alt and Win key (if using a Mac keyboard)

### Font

[Modify the priority of Noto Sans CJK](https://www.zhihu.com/question/47141667/answer/104906870) (for displaying Simplified Chinese properly)

## Terminal

### Shell

Use Zsh (together with oh-my-zsh) instead of Bash

```bash
$ sudo apt-get install -y zsh
$ sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
$ chsh -s `which zsh`
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
$ git config --global push.default simple
```

Store public key generated with `ssh-keygen` on GitHub.

#### Vim

Install Vim with

```bash
$ sudo add-apt-repository ppa:jonathonf/vim
$ sudo apt-get update
$ sudo apt-get install -y vim
```

Create `~/.vimrc` with the content from my [dotfile repo](https://github.com/koallen/dotfiles). Then install all the plugins with Vundle

```bash
$ wget -O ~/.vimrc https://raw.githubusercontent.com/koallen/dotfiles/master/.vimrc
$ git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
$ vim +PluginInstall +qall
```

#### tmux

```bash
$ sudo apt-get install -y tmux
```

Configuration available in my [dotfile repo](https://github.com/koallen/dotfiles).

#### Java

```bash
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt-get update
$ sudo apt-get install -y oracle-java8-installer
```

## GNOME plugins

- Removable drive menu
- User themes
- [System-monitor](https://github.com/paradoxxxzero/gnome-shell-system-monitor-applet#manual-install)
- [Media player indicator](https://github.com/eonpatapon/gnome-shell-extensions-mediaplayer)

## Fixes

### Plymouth crash

```bash
$ sudo chown -R : /sbin/plymouthd
```
