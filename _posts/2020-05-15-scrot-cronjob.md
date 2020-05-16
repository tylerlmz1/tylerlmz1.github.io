---
layout: post
title:  "Save a screenshot every 5 min on Linux"
date:   2020-05-16 18:25:30 +0800
<!--published: false-->
---

On Linux, you can take a screenshot of your currently focused window every X interval.

These are some of my screenshots, previewed with `sxiv` image viewer.
<img src="/assets/cronscrot_sxiv_preview.png">
<!--<img src="/assets/cronscrot_files.png">-->
<!--my massive amount of screenshots-->

Why would you want to do so? So you have a high definition record of what you're working on back then, so in the future you have a better contrast of how much you and your computing environment have changed over time.

For example, I can look back and pin point the exact day I switched to Vim from Typora as my main text editor. This puts things into perspective, the time certain things happened is no longer a vague memory that fades over time without recovery.

This can be achieved with 3 tools
- the bash script below
- `scrot`
- `cron`

Install scrot
```
$ sudo apt-get install scrot
```

<!--`cron` is included in most Linux distributions so no need to install it.-->

Save this bash script:

```
#!/bin/bash

#cd to script location
cd "$(dirname "$0")"

date_string=$(date --iso-8601=date)
folderName=$date_string
mkdir -p ../cron_scrot_snapshot/$folderName

DISPLAY=:0 scrot -u ../cron_scrot_snapshot/$folderName/%Y-%m-%d_%H:%M:%S_scrot.png
```

This bash script creates a folder with the current date, in ISO8601 format (e.g. 2020-05-02)
and saves the currently focused window into the folder as a png file.


You can set up a cronjob to run the script every X interval, for example every 5 minutes.

```
*/5 * * * * /path/to/script.sh
```

