+++
date = "2017-06-25T23:24:48+07:00"
draft = false
title = "My Vim Setup for Rails Development"
+++

![Vim Tmux on Rails](/images/vim_tmux_on_rails.png)

Vim has recently become my editor of choice for code editing, especially for Ruby. I spent half of my time in the Tmux/Vim environment, and the other half is in Xcode. 

In this blog post, I am going to share my Rails development workflow, the plugins that I use, and some general useful Vim tips that hopefully, everyone can make use of.

## First some key re-mapping

I find the `Capslock` key useless, and the `Control` key is kind of hard to reach. So I remap my Caplocks to Control, home row key FTW!

![Remap CapsLock to Ctrl](images/caplocks_to_control_key_remapping.png)

One extra side effects, you can't even be ANGRY with anyone anymore. Less anger, less carpal tunnel syndrome.

## Fuzzy file navigation with `ag` and `ctrlp.vim`

[The Silver Searcher](https://github.com/ggreer/the_silver_searcher) is a code searching tool just like `ack`, just "magnitude faster". And it takes your `.gitignore` into account. Using it as the default grepping engine of Vim make your search and file navigating operations executed a thousand time faster.

Install it using brew

```bash
brew install the_silver_searcher
```

Adding these configurations to your `.vimrc` to set `ag` as the default grepping tool for `ctrlp.vim`

```bash
" Make CTRL-P use ag for listing the files. Way faster
if executable('ag')
  let g:ctrlp_user_command = 'ag %s -l --hidden --nocolor -g ""'
  let g:ctrlp_use_caching = 0
endif
```

Now you can navigate files using fuzzy searching with the speed of light.

<script type="text/javascript" src="https://asciinema.org/a/77OkkZUSLiukEOU3fBwcltpmV.js" id="asciicast-77OkkZUSLiukEOU3fBwcltpmV" async></script>

## Rails Integration with `vim-rails`

[vim-rails](https://github.com/tpope/vim-rails) by the legend `tpope` is the go to plugin for Rails development. It provides functionalities like syntax highlighting, resources navigation, refactoring, running rake and rails commands.

A quick demo before digging in:

<script type="text/javascript" src="https://asciinema.org/a/RZqNhheHMeTGEhYXDf14eN7YM.js" id="asciicast-RZqNhheHMeTGEhYXDf14eN7YM" async></script>

### Resources Navigation

I mostly use `fuzzy searching` for navigating between files, but `vim-rails` does provide another nice way to work with the resources.

For instance, to open the `Commit` model, you'd do:

```bash
:Emodel commit
```

and to open its controller

```bash
:Econtroller commit
```

You can also do `mailer`, `spec`, `helper`, `view`, `migration` and some others. It's also context-aware, so if your cursor is at the `Message#show` and you typed `Eview`, it will open `views/messages/open.html.erb`. 

### Rails Commands Integration

Doing `:Server!` will run a Rails server in a new window using `Tmux`. You can also do all of the Rails' commands inside vim, for example:

```bash
:Rails g model User email password_digest
```

Rake commands work as well:

```bash
:Rake db:create db:migrate
```

### Jump to Definition with `gf`

`vim-rails` extends the "Go To File" behavior by allowing jumping to the corresponding file under the cursor.

<script type="text/javascript" src="https://asciinema.org/a/PMT5PKVTQKMdzrXNRQnoWwDaw.js" id="asciicast-PMT5PKVTQKMdzrXNRQnoWwDaw" async></script>  

### Concern and Partial Extraction

Using the `:Rextract` command for concern and partial extraction. If you're editing a model, the result will be concern extraction. For example, while editing `User` model, you can go into visual mode, highlight the methods and run:

```bash
:'<,'>Rextract concern_name
``` 

Using line number also works:

```
:19,29Rextract concern_name
```

The extracted methods will be put in a new file in `app/models/concerns` and your model will include this file.

The same goes for partials.

<script type="text/javascript" src="https://asciinema.org/a/2JuNB2oftMh1pBXSZ6mel7RHM.js" id="asciicast-2JuNB2oftMh1pBXSZ6mel7RHM" async></script>

## HTML Editting with Emmet

Install `emmet-vim` with Vundle by adding this to your `.vimrc`

```bash
Plugin 'mattn/emmet-vim'
```

Doing HTML is boring, and Emmet allows me to do ultra-fast HTML typing using CSS-like abbreviation. 

Typing the `emmet language` and then `CTRL + Y + ,` will translate it to the HTML.

<script type="text/javascript" src="https://asciinema.org/a/4izI9n4VpD8DV1KutHmET5hJB.js" id="asciicast-4izI9n4VpD8DV1KutHmET5hJB" async></script>

## Final words

This is not the entire configurations/plugins that I use for Vim. My complete dotfiles can be found on my [Github repo](https://github.com/khoiln/dotfiles). I hope you found this article useful and go Vim-on.
