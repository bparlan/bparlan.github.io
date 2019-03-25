---
id: 717
title: 'Windows XP Göçüğü&#8230;'
date: 2011-10-07T07:17:07+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=717
permalink: /windows-xp-gocugu/
dsq_thread_id:
  - "6025590227"
article_header:
  type: cover
  image:
    src: /wp-content/uploads/2012/03/Technolog.jpg
categories:
  - 'İnceleme &amp; Tanıtım'
tags:
  - bilişim
---

Evet bir başka Murphy haftası, en yoğun iki iş günü arası elime babamın göçmüş windows XP&#8217;si geldi, tamir için gece vakti oturdum bilgisayar karşısına, buyrun seyir defteri:

Hata: Windows XP Açılmıyor, boot-screen&#8217;den sonra Windows logosu görünüyor ve restart atıyor. &#8220;Last known good config&#8221;. gibi seçmeler de aynı sonucu veriyor. &#8220;Safe Mode&#8221; denemesinde Mup.sys&#8217;ye kadar listeleme yapıyor sonra yine takılıyor, ve restart atıyor. Bios update hatası gibi bir problem değil, hardware olarak bir problem yaşanmadı. Tipik olarak kullanıcı &#8220;hiç bir şey yapmadı&#8221;, en son kapattığında normaldi. Açmaya çalıştığında hiç açılmadı.<!--more-->

Çözüm İhtimali: öncelikle arşivimdeki yedek bir windows XP cd&#8217;sini taktım. amacım format atmadan içindeki dökümanların kaydını almak ve her daim söylediğim gibi bilgisayarı &#8220;formatlamak&#8221; değil &#8220;tamir etmek&#8221;. Cd&#8217;deki Recovery Console mode&#8217;a geçiş yaptım. Dos komut satırı açıldıktan sonra oralarda biraz gezindim, C:\&#8217;de &#8220;dir&#8221; dediğimiz zaman beliren error:

**&#8220;an error occurred during directory enumeration.&#8221;**

evet ilk gördüğümde ben de çok korktum, windows göçmesinden öte harddisk gitti sandım. yaptığım araştırmala sonucu öğrendim ki burda giden bir harddisk filan yok, çözümü ise gerçekten iki satır komut:

C:\> **chkdsk /p /r**

Evet, C&#8217;de dir çalışmasa da chkdsk işe yarıyor, 80Gb harddisk ortalama 3 saat sürdü, bazen %56&#8217;da filan takılıyor, sonra geri 30&#8217;a dönüyor, dert değil, sabırla bekliyoruz.

Akabinde &#8220;dir&#8221; işe yaradı, harddiskdeki dökümanları görebildim. Sonra dedim restart atıyım da bakıyım desktop&#8217;da filan kalan şeyler varsa komut satırı ile cebelleşmiyim back-up almak için. Windowsu açtım, tata:

**Windows XP: Taskbar yok, Ses yok, sürükle/bırak yapılmıyor, internet yok, wireless yok, RPC çalışmıyor, servislerin özellikleri açılmıyor, en önemlisi: copy/paste yok, çalışmıyor&#8230;**

Her şey yeni başlamış, ve buralar virüs kokuyor artık. Öncelikle belirtmeliyim ki windows xp bu noktadan dönmezdi, yani bu noktadan sonra formatsız kurtuluş mümkün değil. ANCAK! copy/paste olmadığından dolayı nasıl back-up alabileceğim üzerine uğraştım bir süre, çözüm şu şekilde:

**xcopy**

Run>cmd -> **xcopy /?**

pratik olarak external harddisk&#8217;de bir folder yaratıp, o folderin içindeyken örneğin kopyasını almayı istediğiniz döküman bütün userprofile&#8217;ınız, o zaman:

F:\SysBackup\> **xcopy &#8220;c:\Documents and Settings\<span style="color: #ff0000;"><em>Username</em></span>&#8221; -e**

Dolu boş bütün file ve folder&#8217;ları aynı düzende kopyalıyor. Akabinde en azından dökümanların kaydı alınmış bir şekilde formata gidebiliriz, döküman aktarımı sırasında göze çarpan &#8220;LimeWire&#8221; virüsün nerden gelmiş olabileceği konusunda bana büyük bir ipucu verdi. Ayrıca &#8220;henüz format atmadım&#8221;, işe gideceğim, döndüğümde formatsız opsiyonu kendimi sınamak için deneyeceğim, bir gelişme olursa not düşülecektir.
