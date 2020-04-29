---
title: "My  macOS development setup"
date: 2018-07-15T13:46:34+07:00
draft: false
---

[TOC]

## Introduction

The stuff that I do when I setup a new macOS. Mostly for personal references.

## Git

Get git

```bash
xcode-select --install
```

## Restoring the dotfiles

Time to restore my beloved [dotfiles](https://github.com/khoi/dotfiles). My dotfiles mostly contains my zsh, [Neovim](https://neovim.io), Tmux, some other customizations.

I use the bare repo Git technique to manage my dotfiles. The method is described in detail on Atlassian's [blog](https://developer.atlassian.com/blog/2016/02/best-way-to-store-dotfiles-git-bare-repo/)

```bash
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
config config --local status.showUntrackedFiles no
echo ".cfg" >> .gitignore
git clone --bare https://github.com/khoi/dotfiles.git $HOME/.cfg
config checkout
```

## `macOS` tweaks

- Remap `caps lock` to `Control`
- Run [.macos](https://github.com/khoi/dotfiles/blob/master/.macos)

## `nix`

I recently moved from Homebrew to [nix](https://nixos.org/nix/) to manage my dependencies.

```bash
curl -L https://nixos.org/nix/install | sh
```

The packages are defined in [~/.config/nixpkgs/config.nix](~/.config/nixpkgs/config.nix).

To install

```bash
nix-env -iA nixpkgs.myPackages
```

## Homebrew

The very first thing I do is to install [Homebrew](https://brew.sh)

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## Install brew's packages 🍺

```bash
brew install aria2
brew install mas
brew install tldr
brew install youtube-dl
brew install neovim
brew install git
brew install openssl
brew install reattach-to-user-namespace # Use for tmux
brew install ripgrep
brew install tmux
brew install hub
brew install fd
brew install go
brew install jq
brew install node
brew install khoi/tap/compass
brew install htop
brew install ffmpeg
brew install m-cli
brew install fzf && /usr/local/opt/fzf/install
brew install git-extras
brew install bat
brew install diff-so-fancy
brew install starship
```

## Install AppStore application with `mas`

```bash
mas lucky 1Password
mas lucky moom
mas lucky telegram
mas lucky “The Unarchiver”
mas lucky xcode
```

## Install applications using `brew cask`

The ability to installing, maintaining, and removing apps using `brew cask` makes I feel like a super hero. This is my preferred way of installing software.

```bash
brew cask install gpg-suite-no-mail
brew cask install google-chrome
brew cask install dash
brew cask install alfred
brew cask install charles
brew cask install adguard
brew cask install jetbrains-toolbox
brew cask install docker
brew cask install font-jetbrains-mono
brew cask install vlc
brew cask install 1password-cli
brew cask install wireguard
brew cask install sf-symbols
```

## Restore private keys

I stored my private keys, environment variables in 1Password.

```bash
export OP_SESSION_my=$(op signin https://my.1password.com khoiracle@gmail.com --output=raw)
mkdir ~/.ssh
op get document id_rsa > ~/.ssh/id_rsa
op get document id_rsa.pub > ~/.ssh/id_rsa.pub
chmod 0600 ~/.ssh/id_rsa

op get document GPG > /tmp/1.asc
gpg --import /tmp/1.asc; rm /tmp/1.asc
```

## Miscs

- I use [Dracula](http://draculatheme.com) as the color scheme for most of my editor.

## Conclusion

Overall, I'm really happy with the setup above. One thing I need to figure out is how to make use of this fancy-yet-useless TouchBar. Also I'll probably go in to detail on how I use my shell with `fish` + `tmux` + `neovim` in another blog post. Stay tuned 🙇‍♂️.
