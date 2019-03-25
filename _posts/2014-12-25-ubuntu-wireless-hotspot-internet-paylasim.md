---
id: 1962
title: Ubuntu Wireless Hotspot İnternet Paylaşım
date: 2014-12-25T16:27:52+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=1962
permalink: /ubuntu-wireless-hotspot-internet-paylasim/
post_views_count:
  - "0"
dsq_thread_id:
  - "5482318126"
article_header:
  type: cover
  image:
    src: /wp-content/uploads/2014/12/distant-lights-linux-wallpaper-e1424505392313.jpg
categories:
  - Unix | Linux
tags:
  - internet
  - ubuntu
  - wifi
format: image
---

Ubuntu Serveriniz için Wireless Hotspot programı ile nasıl İnternet Paylaşım yapabileceğinizi adım adım anlatıyorum._  
_ 

_Not: Her ne kadar **AP-Hotspot** adlı program destekten çekilmiş olsa da, eldeki örnekler genel geçer şekilde kullanıldığını göstermekte olduğundan, anlatımı bu program üzerinden yapıyorum. İleri bir zamanda eğer sıkıntı çıkar ise, lütfen yorumlardan bildiriniz._

Öncelikle AP-Hotspot yüklemesini yapalım:

`sudo add-apt-repository ppa:nilarimogard/webupd8<br />
sudo apt-get update<br />
sudo apt-get install ap-hotspot`

Ubuntu 14.04 sürümünde bulunan **hostapd** bug&#8217;lı olduğundan, o dökümanı downgrade yapıyor, ve **apt-mark hold** ile o dökümanın ileriki süreçte güncellenmemesini sağlıyoruz. Bu işlem 32bit ve 64bit sistemlerde farklı kaynaklardan yapılmakta. Sisteminize hangisi uygun ise, o işlemi yapınız:

64bit

`cd /tmp<br />
wget http://archive.ubuntu.com/ubuntu/pool/universe/w/wpa/hostapd_1.0-3ubuntu2.1_amd64.deb<br />
sudo dpkg -i hostapd*.deb<br />
sudo apt-mark hold hostapd`

32bit

`cd /tmp<br />
wget http://archive.ubuntu.com/ubuntu/pool/universe/w/wpa/hostapd_1.0-3ubuntu2.1_i386.deb<br />
sudo dpkg -i hostapd*.deb<br />
sudo apt-mark hold hostapd`

#### Wireless Internetimiz Hazır

Artık programımız kullanmaya hazır durumda. Başlatma komutunu ilk defa girdiğimizde, bize öncelikle aşağıdaki SSID &#8211; Şifre gibi ayarlarımızı yaptırıyor, akabinde program başlıyor.

`sudo ap-hotspot start`

Program ayarlarını değiştirmek için:

`sudo ap-hotspot configure`

Resetlemek için:

`sudo ap-hotspot stop`

Durdurmak için:

`sudo ap-hotspot stop`

Bu aşamadan sonra, mevcut Hotspot paylaşımının, server her başlatıldığında otomatik çalışmasını isteyen arkadaşlar, &#8220;Ubuntu otomatik başlatma&#8221; diye ararlarsa, sitemde ona dair de ders bulabilirler.

Güncelleme: Eğer ki arada sırada ap-hotspot programı takılıyorsa, bağlanma aşamasında cihazlarınız wifi&#8217;yi göremiyorsa ve aşağıdaki şekilde bir &#8220;not active&#8221; &#8211; &#8220;another process is already running&#8221; hatalar zincirinde sıkıştıysanız:

`parlan@server:~$ sudo ap-hotspot stop<br />
Wireless Hotspot is not active<br />
parlan@server:~$ sudo ap-hotspot start<br />
Another process is already running<br />
parlan@server:~$ sudo ap-hotspot debug<br />
Another process is already running<br />
parlan@server:~$ sudo ap-hotspot restart<br />
Restarting Wireless Hotspot...<br />
Wireless Hotspot is not active<br />
parlan@server:~$ sudo ap-hotspot start<br />
Another process is already running`

Çözüm olarak aşağıdaki kodu yazarak temp dosyasından Process ID dökümanını silip restart atabilirsiniz. Bu işlem hatanın çözümü olarak işe yarar bir sonuç vermektedir.

`sudo rm /tmp/hotspot.pid<br />
sudo ap-hotspot start`
