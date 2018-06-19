---
title: "Prepend Jira Ticket to Git Commits using Git hooks"
date: 2017-11-05T19:28:45+07:00
draft: false
slug: "prepend-jira-ticket-commit-git-hook"
---

## One Line Installation

```bash
HOOKF=.git/hooks/prepare-commit-msg; if [ -d .git/hooks ] &&  [ ! -f $HOOKF ]; then curl -s https://gist.githubusercontent.com/khoi/e3d2cc8bceefdcd7bda32a337c978e32/raw > $HOOKF && chmod 755 $HOOKF; else echo "Can't install hook"; fi
```

## Boring Explaination Text

If you're using Jira as your issue tracker, it's probably a good idea to use the
`Smart Commit` feature to link the Git commits to the tickets.

![Remap CapsLock to Ctrl](/images/jira-smart-commit.png)

Adding those ticket numbers to commit message is an error-prone process, and you
might end up with the commits being linked to the wrong Jira issue.

Install the snippet below as your Git `prepare-commit` hook and you'll have the
ticket id automatically prepend to all your commits.

<script src="https://gist.github.com/khoi/e3d2cc8bceefdcd7bda32a337c978e32.js"></script>





