---
title: "My  macOS development setup"
date: 2018-07-15T13:46:34+07:00
draft: false
---

- [Introduction](#introduction)
- [Homebrew](#homebrew)
- [Iterm2](#install-iterm2)
- [fish shell 🐡](#fish-shell-🐡)
- [dotfiles](#restoring-the-dotfiles)
- [Some `macOS` tweak](#some-macos-tweak)
- [Homebrew packages 🍺](#install-brews-packages-🍺)
- [ruby](#install-ruby-using-rbenv)
- [GUI Applications](#install-applications-using-brew-cask)
- [Xcode](#xcode)
- [Miscs](#miscs)
- [Conclusion](#conclusion)

## Introduction

I've recently acquired the new 15 inch Macbook Pro. Despite the UselessBar, I've been in love with it mainly because it's light and thin and black. And also coming from a mechanical keyboard "background", I actually really like the feely of the new Butterfly keyboard. 

However, this post is not going to be about how I love my new machine, but rather how I set it up for iOS and Golang development. Many people have asked me about my setup, especially on the terminal-thingy they called it. Thus, I'll try  to document everything in this post, and also try to keep it always up-to-date.

## Homebrew
The very first thing I do is to install [Homebrew](https://brew.sh) 

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## Install Iterm2

[Iterm2](https://iterm2.com) is my shell emulator of choice.

## Fish shell 🐡

My setup is going to be heavily relies on the shell, so let's get Terminal ready.

I've switched from `zsh` to `fish` shell for almost 2 years. And I feel like that `fish` although not as powerful as `zsh`, but it provides me with enough functionalities out of the box, and it requires very minimal configurations. 

### Installing fish

```bash
brew install fish
sudo echo /usr/local/bin/fish >> /etc/shells
chsh -s /usr/local/bin/fish
```

## Restoring the dotfiles

Now that I have `fish` in order, time to restore my beloved [dotfiles](https://github.com/khoi/dotfiles). My dotfiles mostly contains my [Neovim](https://neovim.io), Tmux, some Fish's custom functions.

I use the bare repo Git technique to manage my dotfiles. The method is described in detail on Atlassian's [blog](https://developer.atlassian.com/blog/2016/02/best-way-to-store-dotfiles-git-bare-repo/)

```bash
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
echo ".cfg" >> .gitignore
git clone --bare git@github.com:khoi/dotfiles.git $HOME/.cfg  
config checkout
```

## Some `macOS` tweak

- Run [.macos](https://github.com/khoi/dotfiles/blob/master/.macos) includes some tweak that I feel is necessary for a macOS. It's fully documented so feel free to dissect it.
- Remap `caps lock` to `Control` 
-  > System Preferences > Keyboard. Set `Key Repeat` to fastest, and `Delay Until Repeat` to shortest value.

## Install brew's packages 🍺

```bash
brew install neovim
brew install git 
brew install openssl
brew install reattach-to-user-namespace # Use for tmux
brew install pt # A better ag
brew install tmux
brew install hub 
brew install go
brew install jq
brew install rbenv
brew install node
brew install khoi/tap/sextant
brew install fzf && /usr/local/opt/fzf/install
```

I won't go in to detail on how I use my shell with `tmux` and `pt` since I think that's going to be lengthy and deserve its own blog post. 

## Install ruby using rbenv

```bash
#rbenv
brew install rbenv
rbenv init
rbenv install 2.5.1
rbenv global 2.5.1
```

## Install applications using `brew cask`

The ability to installing, maintaining, and removing apps using `brew cask` makes I feel like a super hero. This is my preferred way of installing software. 

```
brew cask install visual-studio-code
brew cask install gpg-suite
brew cask install google-chrome
brew cask install dash
Brew cask install google-backup-and-sync
brew cask install alfred
brew cask install charles # debug http requests never been easier
brew cask install adguard # Kernel level ad blocker
brew cask install jetbrains-toolbox # For Goland
brew cask install telegram 
brew cask install docker
brew cask install slack
brew cask install skype
brew cask install spotify
brew cask install tunnelbear
brew cask install 1password
brew cask install moom # window management hotkeys
brew cask install caskroom/fonts/font-hack 
brew cask install font-fira-code # My main coding font with ligatures
```

## Xcode

I use [xcode-install](https://github.com/KrauseFx/xcode-install) to maintain my Xcode.

```
gem install xcode-install
xcversion install 9.4.1
```

## Miscs

- I use [Dracula](http://draculatheme.com) as the color scheme for most of my editor.


## Conclusion

Overall, I'm really happy with the setup above. One thing I need to figure out is how to make use of this fancy-yet-useless TouchBar. Also I'll probably go in to detail on how I use my shell with `fish` + `tmux` + `neovim` in another blog post. Stay tuned 🙇‍♂️.
