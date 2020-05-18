---
layout: post
title:  "Initiate a google search outside a browser"
date:   2020-05-17 23:31:30 +0800
<!--published: false-->
---

Let's say you're reading some slides or PDF and you saw something you want to google search, normally you could navigate to your browser, open a new tab and type in your query.

<!--slow way DEMO GIF-->

Alternatively, you could speed this process up by mapping a shortcut key to run a bash script to let you start typing your query right away.

<!--script way DEMO GIF-->

```
#!/usr/bin/env bash

search=$(zenity --entry --title="Google search" --text="" 2>/dev/null)
if [ ! -z "$search" ]; then
  firefox -search "$search"
fi
```

# What it looks like
<img src="/assets/zenity_google_search.png">

<!--write a google chrome script variant-->
