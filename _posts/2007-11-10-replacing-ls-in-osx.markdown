---
layout: post
title: Replacing ls in OSX
date: 2007-11-10 00:19:00 -0700
categories: diy hacks mac
---

Ever since I replaced my laptop with a MacBook in January of this year I've been impressed with Apple's OS X - in fact I've moved over to using it entirely, having replaced my desktop with a Mac Pro in July. It has a very snazzy interface and overall good user experience, and underneath all that prettiness it's running on BSD so I can hack away via terminal all I like. However, coming from a Linux background, I've found the color options for the default OSX/BSD `ls -G` command lacking. With the GNU `ls`, you have a very large degree of control over how things look by using the `.dir_colors` file in your home directory. With that in mind, I decided to replace the default `ls` using this simple method.

First, install [XCode Tools](http://developer.apple.com/xcode/), found on the original OS X disc (or now via the Mac App Store). There are a number of useful developer tools included, but what you really want is a C Compiler (`gcc` originally, `clang` in newer versions). If you do much programming, you've probably already installed this. The idea here is we're simply going to compile the GNU `ls` and `dircolors` for our Mac. If you've used Linux much, you'll recognize the steps exactly.

Next, download the newest version of coreutils from the [GNU FTP](http://ftp.gnu.org/gnu/coreutils/). Pop open a terminal and make a temporary directory, then decompress the archive – for instance `tar -xvjf coreutils-6.9.tar.bz2`.

Enter the directory created from decompressing coreutils. Now we'll compile for our system. Simply run `./configure` and then `make` when it's done. If either `configure` or `make` gives you any guff, you probably just need a new version of XCode Tools.

Presuming that all went well, we've now got a new `ls` binary ready to go. To backup your old one (and its man pages) and replace it with the new, simply run:

```bash
sudo mv /bin/ls /bin/ls.bak
sudo cp src/ls /bin/ls
sudo cp src/dircolors /bin/dircolors
sudo mv /usr/share/man/man1/ls.1 /usr/share/man/man1/ls.1.bak
sudo cp man/ls.1 /usr/share/man/man1/ls.1
sudo cp man/dircolors.1 /usr/share/man/man1/dircolors.1
````

Don't forget to trash the coreutils directory once you're done with it.

Now all you need to do is run `ls --color=auto` to get colored output. I suggest adding the line `alias ls='ls -hF --color=auto'` to your `.bash_profile` file. This makes `ls` color-code output, as well as giving helpful symbols to indicate executable/directory/etc status and displaying file sizes in a human-readable format.

To get the full benefit of the color system, you'll also want to create a `.dir_colors` file in your home directory, and have `dircolors` run when you start a shell. Add a line to your `.bash_profile` such as ``eval `dircolors` ``. You may [download my `.dir_colors`]({{site.baseurl}}/blog/assets/2007/.dir_colors) and modify it if you like. With all that done, you can get pretty results like this:

{% include figure.html url="/blog/assets/2007/replaced_ls.png" caption="ls with colors!" %}