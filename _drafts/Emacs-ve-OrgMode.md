---
id: 3660
title: Emacs ve OrgMode
date: 2017-08-04T03:55:47+02:00
author: Barış Parlan
layout: post
guid: http://www.bparlan.com/?p=3660
permalink: /?p=3660
wp_featherlight_disable:
  - ""
ampforwp_custom_content_editor:
  - ""
ampforwp_custom_content_editor_checkbox:
  - null
ampforwp-amp-on-off:
  - default
categories:
  - Blog
---
<div class="ttr_start">
</div>

Emacs Yükleme:  
emacs25 ubuntu:  
1. Open terminal by pressing Ctrl+Alt+T or searching for “Terminal” from start menu. When it opens, run command to add the PPA:  
sudo add-apt-repository ppa:kelleyk/emacs

Type in your password (no visual feedback due to security reason) when prompts and hit Enter.

  1. Then update and install Emacs 25 via commands:  
    sudo apt update  
    sudo apt install emacs25

For text-only interface, replace emacs25 with emacs25-nox in the last command.  
Don’t know why, but I need to log out and back in to be able to launch Emacs 25 from the Dash.

How to Remove:

To remove Emacs25, open terminal and run commands:

sudo apt remove emacs25 emacs25-nox && sudo apt autoremove

The PPA can be removed by going to System Settings -> Software & Updates -> Other Software tab.

## http://ubuntuhandbook.org/index.php/2017/04/install-emacs-25-ppa-ubuntu-16-04-14-04/

Prelude yüklemek:

<blockquote class="wp-embedded-content" data-secret="dE2SKOtZWS">
  <p>
    <a href="http://pragmaticemacs.com/installing-and-setting-up-emacs/">Installing and setting up emacs</a>
  </p>
</blockquote>



* * *

Orgmode tutorial:  
http://orgmode.org/worg/org-tutorials/org4beginners.html

video dersler:  
http://orgmode.org/worg/org-tutorials/org-screencasts/org-series-episode-1.html

<div class="ttr_end">
</div>