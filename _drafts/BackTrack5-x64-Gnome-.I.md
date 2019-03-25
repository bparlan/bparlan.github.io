---
id: 1805
title: BackTrack5 x64 Gnome .I
date: 2012-09-03T23:02:19+02:00
author: Barış Parlan
layout: post
guid: http://www.bparlan.com/?p=1805
permalink: /?p=1805
categories:
  - 'İnceleme &amp; Tanıtım'
---
<div class="ttr_start">
</div>

Gnome vs KDE Kıyaslaması  
&#8211;  
Backbox / BackTrack / Blackbuntu Kıyaslaması  
&#8211;

&#8212;  
I&#8217;m new to linux, is BackTrack a good place to start ?

Sorry, the simple answer to that is no.

BackTrack is a highly specialized distro, where a lot of normal tasks are not done automatically for you as they are in a mainstream distro.

Our best advice if you wish to start off using linux with BackTrack as your first linux operating system, is don&#8217;t.

Start off by downloading a copy of Kubuntu (as it is a similar base operating system to BackTrack) boot into that and force yourself to do everything you are used to doing on a daily basis using that, preferably spending most of your time using the command line tools. When and only when you can perform all of those daily tasks without having to look-up the commands should you move to BackTrack.

Please don&#8217;t take this as us saying you shouldn&#8217;t use BackTrack, take it as friendly advice that you are letting yourself in for a whole world of pain and frustration if you are not fully comfortable performing administration of your own linux machine before you start with Backtrack.  
&#8212;

BackTrack 5 download ve dualboot kurulum

http://www.backtrack-linux.org/tutorials/dual-boot-install/

&#8211;

Wireless bağlantısı [ip address vermek]

&#8220;BackTrack wireless connected but no internet&#8221;

sudo -i  
service wicd stop  
ip link set wlan0 down  
ip link set wlan0 up  
iwconfig wlan0 essid XXXX  
iwconfig key XXXX(hex)  
dhclient wlan0

Çözüm: Manuel connection

wpa_passphrase ASUS ak123456

ifconfig wlan0 up  
iwlist wlan0 scan  
iwconfig wlan0 essid ASUS key [3]  
dhclient wlan0

&#8212;

Useful Commands:  
lspci  
sh x.run  
aptitude  
vim i :x  
cp file file2  
mv file file2  
rm file

lshw  
xrandr

pico

&#8211;  
&#8220;BackTrack disconnected after 5 minute&#8221;  
iwconfig wlan0 power off  
reconnect wicd  
&#8211;

Nvidia Driver Ekran Kartı Driver&#8217;i

apt-get install yum

gksu gedit /etc/modprobe.d/blacklist.conf  
blacklist vga16fb  
blacklist nouveau  
blacklist rivafb  
blacklist nvidiafb  
blacklist rivatv  
sudo update-initramfs -u  
reboot

nano /etc/X11/xorg.conf

&#8211;

Ses Driveri

&#8220;waiting for sound system to respond&#8221; yazıyordu Sound Preferences&#8217;e basınca.

Çözüm için:

System > Preferences > Startup Applications

Add&#8217;e Tıkla. Herhangi bir isim ver, Browse&#8217;dan /usr/bin/pulseaudio seç.

Logout ol ve startx&#8217;i tekrar başlat.

&#8211;

Amarok media player:

apt-get install amarok

apt-get install gxine

&#8211;

apt-get update

apt-get upgrade

&#8211;

Flash Player Installation

&#8211;

Siteler:  
Intel i915 &#8211; resolution: http://www.backtrack-linux.org/forums/showthread.php?t=48904&highlight=intel+graphics  
Basics: http://lifehacker.com/5633909/who-needs-a-mouse-learn-to-use-the-command-line-for-almost-anything  
How to Install Bumblebee Optimus Nvidia: http://www.backtrack-linux.org/forums/showthread.php?t=46478  
Pyrita Cıuda Optimus: http://www.backtrack-linux.org/forums/showthread.php?t=48331  
Nvidia Driver ıon Linux: http://blog.musicvm.com/solved-you-do-not-appear-be-using-nvidia-x-driver-linux-ubuntu

<div class="ttr_end">
</div>