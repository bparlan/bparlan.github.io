---
id: 1910
title: '&#8220;Package is not available&#8221; Hatası'
date: 2014-09-21T09:36:43+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=1910
permalink: /package-is-not-available-hatasi/
dsq_thread_id:
  - "5496335751"
article_header:
  type: cover
  image:
    src: /wp-content/uploads/2014/09/unix.jpg
categories:
  - Unix | Linux
tags:
  - çözüm
  - linux
  - problem
  - kali
format: image
---

Paket yüklemesi yapmak istediğinizde, örneğin OpenVPN kurmak için gerekli olan paketleri command-line&#8217;da yazdığınızda aldığınız bir hata mesajı şu şekilde olabilir:

Package **network-manager-openvpn** is not available, but is referred to by another package.  
This may mean that the package is missing, has been obsoleted, or  
is only available from another source  
E: Package **&#8216;network-manager-openvpn&#8217;** has no installation candidate

#### Package is not available Hata Çözümü

Bu durum, VPN ile ilgili değildir, sadece unix source-list&#8217;inizde bilgisayarınızın paketleri alması için gereken doğru adresler &#8211; kaynaklar yoktur. Çözüm için, /etc/apt/source.list dökümanını açıp, sonuna aşağıdaki kaynak listesini ekliyoruz ve kaydediyoruz:

_deb http://archive.ubuntu.com/ubuntu quantal universe  
deb http://ftp.de.debian.org/debian wheezy main  
deb http://http.kali.org/ /kali main contrib non-free  
deb http://http.kali.org/ /wheezy main contrib non-free  
deb http://http.kali.org/kali kali-dev main contrib non-free  
deb http://http.kali.org/kali kali-dev main/debian-installer  
deb-src http://http.kali.org/kali kali-dev main contrib non-free  
deb http://http.kali.org/kali kali main contrib non-free  
deb http://http.kali.org/kali kali main/debian-installer  
deb-src http://http.kali.org/kali kali main contrib non-free  
deb http://security.kali.org/kali-security kali/updates main contrib non-free  
deb-src http://security.kali.org/kali-security kali/updates main contrib non-free  
deb http://mirror.nus.edu.sg/kali/kali kali main  
deb http://repo.kali.org/kali kali-bleeding-edge main  
_ 

sonrasında ise:

**sudo apt-get update**

artık dilediğiniz paketin _install_  komutunu başarı ile verebilirsiniz.
