---
id: 1680
title: Görünmez Dosya Görünür Olmuyor
date: 2012-05-02T09:17:47+02:00
author: Barış Parlan
layout: post
guid: http://www.bparlan.com/?p=1680
permalink: /gorunmez-dosya-gorunur-olmuyor/
dsq_thread_id:
  - "5538672733"
image: /wp-content/uploads/2012/03/Technolog.jpg
categories:
  - Windows | PC
tags:
  - çözüm
  - gizli
  - görünmez dosya
  - problem
  - windows
format: image
---
<div class="ttr_start">
</div>

Gerek USB Flash memory içerisindeki virüslerden arta kalan dosyalar, gerekse sapıtmış bir Windows sonrası, &#8220;Hidden&#8221; / Görünmez folderlar kalır, bu görünmez dosyalar görünür olmuyor. Özellikle &#8220;Flash memory&#8217;nin içinde hiç bir dosya yok ama yarısına kadar dolu gösteriyor&#8221; ve benzeri problemler yaşıyorsanız, merak etmeyin, o usb&#8217;nin içi gerçekten dolu&#8230; Yapılması gereken öncelikle windowsun &#8220;görünmez dosyaları göster&#8221; ve &#8220;sistem dosyalarını göster&#8221; olaylarını halletmek \[Araçlar > Klasör Seçenekleri\] \[Tools > Folder Options\], sonrasında görseniz ve kopyalasanız bile değiştiremeyeceğiniz &#8220;görünmez&#8221; ve &#8220;sistem&#8221; ve &#8220;salt okunur arşiv&#8221; dosyası özelliklerini ancak şu şekilde değiştirebilirsiniz:

#### Çözüm

<pre>Run &gt; CMD</pre>

<pre>attrib -r -s -h "C:\DosyaAdi"</pre>

Yani command penceresini açıp, tipik dos komutları ile o folderların adlarını sırası ile yazmak&#8230; Dilerim çözümde yardımcı olur&#8230;

<div class="ttr_end">
</div>