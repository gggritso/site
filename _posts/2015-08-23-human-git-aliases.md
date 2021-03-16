---
title: Humane Git Aliases
subtitle: Stubbornly refusing to speak the computer's language
permalink: human-git-aliases
---

The most common `.gitconfig` I see is blank except for setting a username. The second most common is this:

```
[alias]
  ci = commit
  cia = commit -a
  cam = commit --amend
  cama = commit --amend -a

  cl = clean
  cldf = clean -df

  res = reset
  resa = reset HEAD

  ...

  # 82 more 4-character aliases
```

This config basically trades space in your head for keystrokes. Save on typing by remembering short command aliases. I don't love that. I make typos, and sometimes I don't get enough sleep, and generally this is just going to make life harder on me. I shouldn't be bending to suit the computer's language, the computer should learn mine. I don't care so much about having short commands, I have [a shell with autocomplete that works](http://fishshell.com/). Instead, I use real words and try to make the whole thing more human.

My goals with git aliases are:

1. smooth out [git's unwieldy UI](http://stevelosh.com/blog/2013/04/git-koans/)
2. make a few common workflows faster

For example, in git, trying to just get a list of something in the repository is insanely inconsistent. I fix it like so:

```
branches = branch -a
tags = tag
stashes = stash list
```

How about common operations for undoing work? I never want to Google "how to unstage a file", there should just be a %$&#ing command to unstage a file.

```
unstage = reset -q HEAD --
discard = checkout --
uncommit = reset --mixed HEAD~
amend = commit --amend
```

I even have a nuclear version:

```
nevermind = !git reset --hard HEAD && git clean -d -f
```

which unstages changes in the index, discards changes in the working directory, and removes any new files.

I also really like having

```
graph = log --graph -10 --branches --remotes --tags  --format=format:'%Cgreen%h %Creset• %<(75,trunc)%s (%cN, %cr) %Cred%d' --date-order
```

to see real timeline of who is working on what and when. Another good example:

```
precommit = diff --cached --diff-algorithm=minimal -w
```

This is a key part of my workflow. I run this before _every_ commit to make sure I don't need to use the undo commands.

Bend the aliases to how you think and work, not the other way around. Let your aliases reflect your values, instead of just saving you keystrokes.


---

I got a few great suggestions from Reddit comments on this post:

`unmerged = diff --name-only --diff-filter=U` by [kasbah](https://www.reddit.com/user/kasbah) and `remotes = remote -v` by [WrongSubreddit](https://www.reddit.com/user/WrongSubreddit) are my favourites. Thank you!
