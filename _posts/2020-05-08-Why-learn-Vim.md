---
layout: post
title:  "Why learn Vim"
date:   2020-05-08 21:12:30 +0800
categories: tools
---

Learning Vim had been one of the more rewarding things I've done in my life.

Before switching to Linux, I've heard that Vim is a powerful text editor, but when I first tried it, I was taken aback by how awkward the keybindings are.

For example, to move your cursor a word forward, it is to press `w`. At this point I expect moving a word backward would be something sensible, like `q` or something, so it would be like how arrow keys are, but it is `b`, for how `b` is on the right and `w` is on the left, but the direction of their movement is the opposite, it doesn't seem like a good mapping at first glance.

but down the road I've learnt that Vim keybindings is based more on mnemonics than directional mapping, `w` to move the cursor to a word forward, `b` to go a word backwards.

Here are some reasons why learning Vim is a good idea.

### Vim is fast
As someone working in the software world, editing text is a big part of our work, Vim let's you do it more efficiently.
Vim let's you edit text with speed, and you can configure it to match your workflow to enable you to do things you always do faster.

This is primarily done with writing Vim Scripts into your ~/.vimrc, or installing some plugins (preferrably with a plugin manager like VimPlug).

### Even Emacs embraces Vim
Emacs is a contender to Vim, but popular Emacs distributions like Doom Emacs, Spacemacs include `evil` (extensible vim layer), making the text editing have vim keybindings, this goes to say how good Vim is, that even their main contender's popular distributions include it.

### Vim keybinding is everywhere in Linux
If you plan on going into the Linux ecosystem, it is helpful to learn Vim. A lot of Linux tools ship with vim keybindings, for example mupdf, sxiv, ranger. Vimium browser extension could take your browser usage to the next level too.

### Useful for SSH
when we have to SSH into a remote server to edit config files, Vim is likely to be installed in the server, while GUI text editors like Sublime text, VScode, or Emacs, are not necessarily available.
