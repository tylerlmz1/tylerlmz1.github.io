---
layout: post
title:  "A faster way to save and exit in Vim"
date:   2020-05-17 18:34:30 +0800
<!--published: false-->
---

To save and exit in Vim, we use
- `:w` to save
- `:q` to quit with `unsaved content warning`
- `:q!` to quit without saving
- `:x` to save and exit at the same time

but for such a frequently done action, having to reach for `:` and then w/q/x everytime,
can slow us down


By putting this mapping in your ~/.vimrc,

```
let mapleader = "\<Space>"
" [ Leader key save and exit vim ]
nmap <Leader>q :q<CR>
nmap <Leader>w :w<CR>
nmap <Leader>x :x<CR>
nmap <Leader>a :q!<CR>
```

you can just press
- `Space q` to do `:q`
- `Space w` to do `:w`
- `Space x` to do `:x`
- `Space a` to do `:q!` ( think `a` for `abort` )

Now you can save and exit faster in Vim, increasing your Vim productivity.

But do note, this changes your leader key from the default `\` to `Space` key
<!--( the default is `\`)-->
, which from my research, tend to be a favored leader key customization for a lot of Vim users.

