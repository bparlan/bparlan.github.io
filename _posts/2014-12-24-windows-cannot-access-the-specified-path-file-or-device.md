---
id: 1956
title: Windows cannot access the specified path file or device
date: 2014-12-24T10:11:37+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=1956
permalink: /windows-cannot-access-the-specified-path-file-or-device/
post_views_count:
  - "0"
dsq_thread_id:
  - "5523867255"
article_header:
  type: cover
  image:
    src: /wp-content/uploads/2014/12/blue_screen_microsoft_windows_blue_screen_of_death_1440x900_wallpaper_Wallpaper_1920x1200_www.wall321.com_-e1424505349544.jpg
categories:
  - Windows | PC
tags:
  - çözüm
  - problem
  - windows
format: image
---

Hata: &#8220;Windows cannot access the specified path file or device&#8221;

Evet, gayet ciddi miktarda &#8220;güvenlik&#8221; üzerine uğraştığım ev bilgisayarım, bu hata mesajı ile sapıttı. Çıldırmamak elde değil, böyle saçma bir kilitlenme &#8211; çıkışsız problem görmemiştim hayatımda. Resim &#8211; müzik &#8211; yazı &#8211; internet &#8211; program &#8211; control panel&#8217;de bir düğme, Command Line, her ne açmaya çalışırsam çalışayım, bu hatayı verdi. Eğer bilgisayarınızda bu hata &#8220;her yerde&#8221; var ise, bu yazıyı başka bir bilgisayardan okuyorsunuzdur. Belirtmeliyim ki, spesifik olarak bir programdan geliyorsa bu arıza, çözümü çok basit bir şekilde &#8220;Properties&#8221; kısmından &#8220;Ownership&#8221; ayarlarında. Benim yaşadığım, bilgisayardaki her dökümanın bu arızayı vermesi. Bu çıldırtan durumun çözümünü anlatacağım.

Öncelikle problemin nereden kaynaklandığını ifade edelim: ZoneAlarm veya Emsisoft Online Armor Firewall gibi alternatif firewall programı kullanan bilgisayarlarda, Windows Update açık ise, windowsun User Account Center&#8217;i (UAC) ve kendi güvenlik sistemi, bu yazılımlarla kardeş kardeş oynamıyor, aksine çakışıyor. Bir gün bilgisayarınız kapanırken &#8220;updating&#8221; yazıyorsa, tekrar açtığınızda bilgisayarınızı darmadağın ve hiç bir şey yapamaz halde bulabiliyorsunuz. Bu yüzden Windows Update her daim disable olmalı! Kim ne derse desin, faydasından çok zararını gördük bu olayın. Benim bilgisayarımda nasıl enable oldu bilmiyorum, ayrı konu, ama olmuş, indirmiş, ve update etti, ve açıldığında hiç bir dosya &#8211; döküman &#8211; yazılıma erişemiyordum.

#### Çözüm

Özette, önce 2. bir bilgisayardan şu yazılımı indiriyorsunuz:  
<a title="Windows Repair - All in One" href="http://www.tweaking.com/content/page/windows_repair_all_in_one.html" target="_blank">http://www.tweaking.com/content/page/windows_repair_all_in_one.html</a>

Bu yazılımı usb&#8217;ye atıp, bilgisayarı SafeMode&#8217;da açıyoruz. Dikkat, Safe Mode with Networking gibi alternatiflerle değil, salt SafeMode ile, zira networking olduğu anda güvenlik sistemi devreye giriyor ve yine kullanım dışı kalıyorsunuz.

SafeMode&#8217;da aşamaları takip edip, bittiğinde Add/Remove Programs&#8217;dan güvenlik programınızı kaldırma hakkı elde etmiş oluyorsunuz. O sıkıntı çıkaran hangi firewall ise onu kaldırınca da normal şekilde bilgisayarınızı açma hakkı elde ediyorsunuz&#8230; Artık böyle böyle, elinizden alınmış özgürlüğünüze tekrar kavuşabiliyorsunuz.

#### Detay

Derin plan&#8217;da olan ise, bilgisayarın bütün dökümanlarının &#8220;Ownership&#8221;lerinin değişmesi. Ve sizin Owner olmamanız. Bunların toplu çözümü o yazılımda. Normal açılan windows&#8217;a tekrar aynı firewall&#8217;ı yüklemek problem yaratmıyor.
