---
id: 1949
title: Corel Draw Power Clip Yavaşlaması Çözüm
date: 2014-12-12T14:38:00+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=1949
permalink: /corel-draw-power-clip-yavaslamasi-cozum/
post_views_count:
  - "0"
dsq_thread_id:
  - "5486053693"
article_header:
  type: cover
  image:
    src: /wp-content/uploads/2014/12/coreldraw.jpg
categories:
  - Genel | Yazılım
tags:
  - çözüm
  - problem
  - program
format: image
---

Corel Draw Power Clip Yavaşlaması, ister X6 ister X7 olsun, son güncellemelerinden beridir Power Clip içerisine girince, Clip dışındaki objeleri şeffaf gösterme çabası ile muazzam bir yavaşlama yaşamaktadır. Bu şeffaflaşma registry&#8217;den iptal edilerek düzeltilebilir. Bilginiz olsun ki program içerisinde böyle bir ayar mümkün değil. Aşağıdaki çözüm anlatımı sırasında Corel X6 için 16.0, X7 için 17.0 isimli dosyayı seçmeniz yeterlidir. Kalan her şey aynıdır.

#### Corel Draw Power ClipYavaşlamasına Çözüm

  * Corel Draw&#8217;u kapat, Start > Run&#8217;dan Regedit yaz ve çalıştır. Aşağıdaki adrese git:
  * _HKEY\_CURRENT\_USER\Software\Corel\CorelDRAW\16.0\Draw\Application Preferences\Powerclip_
  * _EditDisplayWithPageContext_ adlı girdinin değerini “1” den “0”a çevir. Kaydet kapat.

Corel Draw&#8217;ı tekrar açabilirsin. X6&#8217;da başlayan problem, ileriki sürümlerde de aynı şekilde devam edeceği izlenimi verdiğinden dolayı, aksi bir değişiklik olmadığı sürece bu çözüm işinize her daim yarayacaktır&#8230;
