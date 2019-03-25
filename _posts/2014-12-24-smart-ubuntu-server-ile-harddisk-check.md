---
id: 1960
title: 'SMART &#038; Ubuntu Server ile Harddisk Check'
date: 2014-12-24T10:38:51+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=1960
permalink: /smart-ubuntu-server-ile-harddisk-check/
post_views_count:
  - "0"
dsq_thread_id:
  - "5487647082"
article_header:
  type: cover
  image:
    src: /wp-content/uploads/2014/09/unix.jpg
categories:
  - Unix | Linux
tags:
  - linux
  - server
  - ubuntu
format: image
---

Elimizde 4-5 Harddisk var, bozuk mu her birisi? Ömrü ne kadar? gibi soruların cevaplarını alacağız Ubuntu Server kullanarak. Zira harddiskleriniz S.M.A.R.T. adlı teknolojiyi destekliyor ise, muazzam detaylı bilgi alabiliyoruz. Bu teknoloji, harddiskin kendi kendisinin sağlığını kontrol etmesini sağlamaktadır. Aşağıda anlatılanlar için önce kontrol etmek istediğiniz harddisk&#8217;i, bilgisayarınıza takıyorsunuz, normal ubuntu server açılıyor, yani büyük ihtimal 2. harddiskiniz &#8220;sdb&#8221; oluyor

#### Harddisk Check

Harddisk&#8217;lerin listesini ve isimlerini görmek için: (anlatım boyu sdb yerine, burada görebileceğiniz harddisk ismini yazabilirsiniz)  
sudo fdisk -l

S.M.A.R.T. Yüklemek için  
_sudo apt-get install smartmontools_

Harddiskiniz Smart destekli mi anlamak için (sdb yerine harddiskinizin ismini yazınız)  
_sudo smartctl -i /dev/sdb_

Şöyle bir sonuç görmüş olmanız gerek:  
_SMART support is: Available &#8211; device has SMART capability._  
_SMART support is: Enabled_

Eğer SMART Enabled değil ise:  
_sudo smartctl -s on /dev/sdb_

Farklı test yöntemleri mevcut.  
1- Kısa  
2- Uzun  
3- Conveyance (Nakil)

Her bir test yönteminin ne kadar süreceğini görmek için:  
_sudo smartctl -c /dev/sdb_

En tavsiye edileni Uzun (2) olan testtir. Başlatmak için:  
_sudo smartctl -t long /dev/sdb_

Ekranda &#8220;şu saatte gel bak&#8221; diyecek size bilgisayar. O saat geçene kadar bekleyin. Sonrasında test sonucunu görmek için:  
_sudo smartctl -l selftest /dev/sdb_

Detaylı SMART Sonuçları için: (IDE)  
_sudo smartctl -a /dev/sdb_

Detaylı SMART Sonuçları için: (SATA)  
_sudo smartctl -a -d ata /dev/sdb_
