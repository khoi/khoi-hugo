+++
date = "2016-09-25T23:19:31+07:00"
draft = false
title = "macOS Apps that I couldn’t live without #1 - Alfred"
slug = "macOS-Apps-alfred"
+++

In my very first blog post, I've written about ["macOS Setup for iOS Development"](/blog/my-macos-setup-for-ios-development/). I thought some of the tools in there deserve more attention than just a `li` html tag. That's why the series `macOS Apps that I couldn't live without` was born. Today I'll start with my most favorite *how-do-i-survive-without-it* **Alfred**.

So what is Alfred. I'll steal the tagline from the homepage as a brief super short introduction

>Alfred is an award-winning app for Mac OS X which boosts your efficiency with hotkeys, keywords, text expansion and more. Search your Mac and the web, and be more productive with custom actions to control your Mac.

There are plenty of amazing resources that teach you how to be efficient with Alfred out there, so I'll focus on my personal use cases.

## My Alfred Setup

I use Command + Space as my hotkey for opening Alfred (yep, Alfred totally replaces Spotlight)

![Alfred Hotkey](/images/alfred_hotkey.png)

In order to set that hotkey you'll need to disable Spotlight hotkey in your `System Preferences > Keyboard`

![Disable Spotlight Hotkey](/images/disable_spotlight_hotkey.png)

## 1.Open Apps

Just like Spotlight you can search for app and open it with one big twist. Alfred learns how you use your Mac and prioritizes the results.

![alfred-evernote](/images/alfred_evernote.png)

>See how `Evernote` is at the top of the list? And I still can open `Energy Saver` or other apps just by pressing `Command + {2|3|4}`

## 2.Finding files

Just like with Apps, finding file and previewing them has never been easier.

![alfred-finding-files](/images/searching_file1.png)

>Yep, Alfred knows that I've been struggling with the new schedule layout implementation for [Planday](https://www.planday.com) lately. You can open the file with `Enter`, or reveal the find with Finder using `Cmd + Enter`.

![alfred-finding-files](/images/searching_file2.png)

>Or just press `->` for the list of available actions.

## 3. Clipboard History and Snippets

Tired of typing the same thing over and over again? Alfred's got you covered, use the `Clipboard History` to locate any text, image, or files that you have copied earlier and use it again.

![alfred-clipboard](/images/alfred_clipboard.png)

You can also create your own snippets and type just a short abbreviation and Alfred will auto-expand to the full text, saving yourself hours of typing in the long run. For instances:

>`;ds` and it will turn to `25/09/2016`

>`;blog` to `https://khoiln.github.io`

![alfred-snippets](/images/alfred_snippets.png)

> Setting up `Snippets` is dead easy, and the posibilities are endless.

## 4. System Commands

I also use Alfred for various common Mac action like `controlling iTunes`, `lock`, `shutdown`, `force quit apps` ...

![alfred-snippets](/images/alfred_lock.png)

>I've been using Mac for almost 10 years and without Alfred, I don't even know how to `lock` the Mac. Am I stupid or something?

That was my brief introduction to Alfred. Alfred is much more powerful than that with many advance feature like [expandable worlflows](https://www.alfredapp.com/workflows/), so if you're in to productivity like me. Start using it today and save your precious time. And did I say Alfred sync your settings across all the Macs too? Plainly awesome!
