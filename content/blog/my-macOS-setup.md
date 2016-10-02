+++
date = "2016-09-09T09:49:54+07:00"
draft = false
title = "#1 - my macOS Setup for iOS Development"
slug = "1-my-macOS-Setup-iOS-Development"
+++

I don't normally have to re-install my Mac, but when I do somehow I always forget setting up couple of tools and only find out about it later on.

So I figure I'll document everything here and keep it updated mostly for self references (:

List of apps from Appstore:

* Slack
* Evernote
* Dash 3
* Pocket
* Prepo
* Xcode
* Todoist (remind me to watch Apple September event at midnight <3)
* The Unarchiver

I have a private dotfiles repo that have all my `zsh`, `vim`, `aliases`, `git` configuration and also a script that config the Mac to fit my development style.

Here is the copy of the [.osx script](https://gist.github.com/khoiln/28966594298029b10f4342f90de1fa60)

Homebrew and Cask are the tools I use to install all the dependencies as well as the applications that are not available from Appstore

* Install `Homebrew`

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

* Install `brew cask`

```bash
brew tap caskroom/cask
```

Apps that are installed through Brew Cask

* Sketch https://www.sketchapp.com
* iTerm https://www.iterm2.com
* zsh https://github.com/robbyrussell/oh-my-zsh
* Hack fonts https://github.com/chrissimpkins/Hack (the font that used for code)
* Google Drive
* infinit.io (Awesome p2p file sharing tool, definitely check it out)
* 1password
* Alfred ( I can't live with out this )
* Moom ( windows management tool )
* Sublime Text 3 (for quick text editing, and yeah vim's also used sometimes)
* IntelliJ Ultimate (mostly for Node.js development)
* Kaleidoscope (A better diff tool for code merging)
* ScreenFlow
* Franz
* Skype
* Source Tree

Other customizations that I do

* Install rvm

```
\curl -sSL https://get.rvm.io | bash -s stable --ruby
rvm install 2.3.1
rvm --default use 2.3.1
```

* Also other iOS dependencies

```bash
gem install cocoapods carthage
```

Those are the tools that I use for my iOS Development. If I'm missing something cool, let me know.
