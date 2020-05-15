---
layout: post
title:  "Simple password management with GPG"
date:   2020-05-15 10:04:30 +0800
categories: tools
---

**This is a post about a password management system where you GPG encrypt markdown files on Linux and Syncthing them to Android.**

<!-- use the word `markdown files` instead of `plain-text files` is because people who care enough to read on are tech savvy people that knows markdown anyway, but then 会make it too 复杂吗, 再看吧, 感觉 say plain-text might 也比较好的 -->

I'm not too fond of using password management tools like `Dashlane` or `1Password`, I've never really tried them, because there's no guarantee that they will live forever, nor that their security perfect.

Even though some of them are open-source, they are still at the mercy of their developers unless I'm willing to modify it myself,
so it is harder to modify it to fit my needs better.

I just want a password management system that is simple, extensible and will live forever, this is my setup:

I create markdown files and store my login credentials plain-text, then

- On my computer, I use
  - `gpg` to encrypt the markdown files
  - `jamessan/vim-gnupg` Vim plugin to easily decrypt and edit the files
  - `Git` to version control the folder so I have full history of my login credentials
- To access them from my phone, I use
  - [Syncthing](https://syncthing.net/) to synchronize the folder to my phone
  - [OpenKeychain](https://play.google.com/store/apps/details?id=org.sufficientlysecure.keychain&hl=en) app to decrypt and read the encrypted files

I could just Syncthing the markdown files without encryption to my phone, but on the off chance that my phone is stolen / lost / hacked, I don't want my passwords to go down with it, so it is safer to have it gpg encrypted.

I'm aware of [pass](https://www.passwordstore.org/) and tried it before I came to this setup, but I want to put more info than just a password string in my files, so that's why `pass` doesn't fit my need.

### How to replicate this setup


**1. Generate a PGP keypair with GPG**

you can skip this if you already have a keypair.

$ `gpg --full-gen-key`


**2. Install the Vim plugin and put in corresponding config**

Assuming you're using VimPlug ( a vim plugin manager ),
put this into your ~/.vimrc and run `:VimPlug` in Vim.

NOTE: remember to modify the `youremail@provider.com` to the email associated with your PGP key

```
Plug 'jamessan/vim-gnupg'
" Armor files
let g:GPGPreferArmor=1
" Set the default option
let g:GPGDefaultRecipients=["youremail@provider.com"]"
```
<!--This plugin will auto decrypt encrypted files when you open them with Vim, making the only difference with opening a normal unencrypted file a slight delay of opening the file due to the decryption process.-->
<!--有点啰嗦 this ^ line, comment it out first-->


**3. Create a markdown file**

$ `touch mygmail.md`

**4. Encrypt the markdown file**

<!--$ `gpg --recipient youremail@provider.com --armor --output %f.asc --encrypt %f`-->
$ `gpg -e -r youremail@provider.com path/to/file`

if you use [Ranger](https://github.com/ranger/ranger), you can put this mapping into your rc.conf to encrypt it easily by pressing `te` when the selection is hovering on the file:

`map te shell gpg --recipient youremail@provider.com --armor --output %f.asc --encrypt %f && rm %f`

**5. Setup Syncthing**

Install Syncthing on Linux and Android, set it up to sync your password folder to your phone.

**6. Setup OpenKeychain**

Install [OpenKeychain](https://play.google.com/store/apps/details?id=org.sufficientlysecure.keychain&hl=en) Android app on your phone, export your keys from Linux and import them on your android phone.
<!--Install `OpenKeychain` Android app on your phone, export your keys from Linux and import them on your Android phone-->

**7. Try decrypting your files on Android**

To decrypt and view your password file:

1. Open the `OpenKeychain` app
2. Press the hamburger menu icon on the top left


3. Press `Encrypt/Decrypt`

<img src="/assets/decrypt.png" width="300px">

4. Press `Select input file` and browse to the file
5. Enter your PGP key passphrase


**8. Done**
