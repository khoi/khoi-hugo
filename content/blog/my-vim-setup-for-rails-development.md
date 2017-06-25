+++
date = "2017-06-25T23:24:48+07:00"
draft = false
title = "My Vim Setup for Rails Development"
+++

![Vim Tmux on Rails](/images/vim_tmux_on_rails.png)

Vim has recently become my editor of choice for code editting, especially for Ruby. I spent half of my time in the Tmux/Vim environment, and the other half is on Xcode. 

In this blog post, I am going to share my Rails development workflow, the plugins that I use, and some general useful Vim tips that 
hopefully everyone can make use of.

## First some key re-mapping

I personally find the `Capslock` key useless, and the `Control` key is kind of hard to reach. So I remap my Caplocks to Control, homerow key FTW!

![Remap CapsLock to Ctrl](images/caplocks_to_control_key_remapping.png)

One extra side effects, you can't even be ANGRY with anyone anymore. Less anger, less carpal tunnel syndrome.

## Fuzzy file navigation with `ag` and `ctrlp.vim`

[The Silver Searcher](https://github.com/ggreer/the_silver_searcher) is a code searching tool just like `ack`, just "magnitude faster". And it takes your `.gitignore` in to account. Using it as the default grepping engine of Vim make your search and file navigating operations executed a thousand time faster.

Install it using brew

```bash
brew install the_silver_searcher
```

Adding these configuration to your `.vimrc` to set `ag` as the default grepping tool for `ctrlp.vim`

```bash
" Make CTRL-P use ag for listing the files. Way faster
if executable('ag')
  let g:ctrlp_user_command = 'ag %s -l --hidden --nocolor -g ""'
  let g:ctrlp_use_caching = 0
endif
```

Now you can navigate file using fuzzy filename searching with the speed of light

[![asciicast](https://asciinema.org/a/ZWQtjarToJmhrIkWBHCh1XS48.png)](https://asciinema.org/a/ZWQtjarToJmhrIkWBHCh1XS48)