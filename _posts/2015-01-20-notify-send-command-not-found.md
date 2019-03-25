---
id: 1984
title: 'notify-send: command not found'
date: 2015-01-20T09:37:30+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=1984
permalink: /notify-send-command-not-found/
dsq_thread_id:
  - "5583530916"
article_header:
  type: cover
  image:
    src: /wp-content/uploads/2014/12/distant-lights-linux-wallpaper-e1424505392313.jpg
categories:
  - Unix | Linux
tags:
  - çözüm
  - hotspot
  - ubuntu
format: image
---

_Ubuntu Server 14_&#8216;ümüze Wifi AP Hotspot sistemi kurduğumdan beri şöyle bir sıkıntı yaşıyordum, sistem açıldıktan sonra kendi kendisine Hotspot&#8217;u başlattığından dolayı ekrana şu mesaj geliyor:

`Wireless Hotspot Active<br />
bash: notify-send: command not found`

ve sonrasında bu mesaj gün boyu tekrar tekrar ekrana çıkıyordu. Bu, terminal1&#8217;i işgal ediyordu. Ben Ctrl+Alt+F2 ile 2. terminale geçtiğim zaman herhangi bir işleme çalışma sıkıntısı olmuyor, wireless AP canavar gibi hizmet vermeye devam ediyor, ancak 1. terminalde bu mesaj 10 saniyede bir yenilenmek üzere sonsuzluğa kavuşuyordu. Meğersem tek derdi, **notify-send** komutunun ubuntu server 14 üzerinde bulunmamasıymış, ve programın bize söylemeye çalıştığı tek şey, _&#8220;Wireless Hotspot Active&#8221;_ miş.

#### Notify-send: Command not found | Çözümü

`sudo apt-get install libnotify-bin`

yani bilgisayarın notify-send komutunu kullanabilmesini sağlıyoruz. Bize açılınca wireless active ulan diyor, ve bitiyor. tty1&#8217;i de problemsiz bir şekilde kullanabiliyoruz.
