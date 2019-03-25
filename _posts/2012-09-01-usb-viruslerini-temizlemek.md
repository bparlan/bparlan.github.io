---
id: 1801
title: Usb Virüslerini Temizlemek
date: 2012-09-01T12:50:02+02:00
author: Barış Parlan
layout: post
guid: http://www.bparlan.com/?p=1801
permalink: /usb-viruslerini-temizlemek/
dsq_thread_id:
  - "5796860208"
image: /wp-content/uploads/2012/03/Technolog.jpg
categories:
  - 'İnceleme &amp; Tanıtım'
tags:
  - rehber
  - silmek
  - temizlemek
  - usb
  - virüs
format: aside
---
<div class="ttr_start">
</div>

Bütün insanlığın baş belası olan USB Virüs problemi, evet o dosyalarınızın USB memory stick&#8217;inizde olduğuna emin olduğunuz halde onları göremeyişiniz (ki aslında oradalar ve sadece görünmezler), veya onları görüyorken, tıkladığınızda açılmıyor olmaları (ki aslında tıkladıklarınız sadece onların &#8220;kısa yol kopyaları&#8221; ve orjinal dökümana gitmiyor bu kısa yollar, tıklanmak için sizi aldatıyorlar, zira tıklayınca bağlı bilgisayara da bulaşıyorlar), o ne işe yaradığını hiç anlamadığınız ama USB&#8217;nizde herdaim bulunan autorun.inf dökümanı&#8230; Uzatmayacağım, çok bir detay da açıklamayacağım, sadece nasıl kurtulursunuz, buna dair ileri seviye bir teknik paylaşacağım, dilerim ihtiyacı olanların işine yarar.

### USB Virüs temizlemek

Önce My Computer açıp USB&#8217;nizin isminin sonundaki harfi öğreniyoruz. G: olabilir, H: olabilir, o harf önemli.

_Start &#8211; Run düğmesine basıp (eğer windows 7 &#8211; 8 ise, o en alttaki kutuya doğrudan yazabilirsiniz) cmd yazıyoruz, tırnaklar olmadan._

Start > Run > &#8220;cmd&#8221;

_Açılan komut satırında aşağıdaki komutu aynen yazıyoruz, sadece X harfini, ilk öğrendiğimiz USB&#8217;nizin Harfi ile değiştiriyoruz. Ve bütün komutu yazınca Enter&#8217;a basıp çalıştırıyoruz komutu. Bitmesi biraz zaman alır._

attrib -r -a -s -h /s /d **X**:\*.*

Bittikten sonra bu sefer de o USB&#8217;nin içine giriyoruz komut satırından, yine X yerine sizin harfinizi yazıp entera basıyorsunuz:

X:

Son olarak aşağıdaki komutu yazıp bütün o sahte virüs kalıntılarına güle güle diyoruz:

del /s /q /f *.lnk

Hayırlı olsun efendim.

&nbsp;

X: -> Usb Flash Disk&#8217;in bulunduğu drive letter olacak.

<div class="ttr_end">
</div>