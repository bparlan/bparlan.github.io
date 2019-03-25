---
id: 1952
title: 'Ubuntu Yükleme: configuring bcmwl-kernel-source'
date: 2014-12-14T15:40:01+02:00
author: Barış Parlan
layout: post
guid: http://www.bparlan.com/?p=1952
permalink: /ubuntu-yukleme-configuring-bcmwl-kernel-source/
post_views_count:
  - "0"
dsq_thread_id:
  - "5498675583"
image: /wp-content/uploads/2014/12/distant-lights-linux-wallpaper-e1424505392313.jpg
categories:
  - Unix | Linux
tags:
  - bcmwl
  - kernel
  - ubuntu
  - yükleme
format: image
---
<div class="ttr_start">
</div>

Ubuntu Linux 14.10 Desktop &#8211; AMD 64 veya benzeri bir başka Ubuntu işletim sistemini bilgisayarınıza yüklerken **configuring bcmwl-kernel-source** aşamasında takılıp kalıyorsa eğer, kapatmayın, iptal etmeyin, çözümü hemen orada, o aşamada saklı:

_Ctrl + Alt + F2_&#8216;ye basıyorsunuz  
**pkill -9 modprobe**  
yazıp _Enter_&#8216;a basıyorsunuz.  
_Ctrl + Alt + F7_ ile yükleme ekranına geri dönüyorsunuz.

Yükleme problemsiz biçimde devam ediyor.

Aynı hata Ubuntu 12 ve 13&#8217;de de mevcut, anladığım kadarı ile 64bit AMD versiyonu &#8220;3rd party&#8221; yükleme seçeneği işaretli olduğunda oluyor. Eğer işaretlemezseniz de bu sefer driver filan uğraşmak zorunda kalıyorsunuz. En güzeli, işaretleyip, burada takılıp, çözümde anlatılanı yapıp, öyle devam etmek&#8230;

Ayrıca, hayatımda hiç bir Windows &#8220;yükleme takılması&#8221; probleminde böyle &#8220;o an işe yarayacak&#8221; bir çözüm görmemiş olmanın yarattığı saflık ile bu çözüm ayrıca bir içimi gülümsetmiştir ilk duyduğumda & uyguladığımda&#8230;

<div class="ttr_end">
</div>