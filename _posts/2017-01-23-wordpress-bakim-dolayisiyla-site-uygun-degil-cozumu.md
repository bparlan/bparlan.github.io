---
id: 3334
title: WordPress Bakım Dolayısıyla Site Uygun Değil Çözümü
date: 2017-01-23T09:42:49+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=3334
permalink: /wordpress-bakim-dolayisiyla-site-uygun-degil-cozumu/
dsq_thread_id:
  - "5499301550"
article_header:
  type: cover
  image:
    src: /wp-content/uploads/2017/01/2017-01-23-wordpress-2.jpg
categories:
  - Bilişim
  - Genel | Yazılım
tags:
  - bakım
  - çözüm
  - problem
  - wordpress
format: image
---

WordPress&#8217;de kimi zamanlar bakım sebebi ile kendi sisteminin güncellenmesi gerekiyor, dosyalarınızın yedeğini alıyor, tema &#8211; plugin kayıtlarınızı indiriyor ve database&#8217;inizi arşivliyorsunuz, sonra güncelle düğmesine basıyorsunuz, biraz vakit geçiyor, sayfa boşa dönmeye başlıyor, not responding hatası ile karşılaşıyorsnuz, yenile&#8217;ye basınca (f5) ise karşınıza şöyle bir yazı çıkıveriyor:

> Zamanlanmış bakım dolayısıyla site uygun değil. Bir kaç dakika içinde tekrar kontrol edin.

Eğer wordpress&#8217;i ingilizce kullanmayı tercih ediyorsanız, aynı hata mesajı şu şekilde okunmakta:

> <span class="st">Briefly unavailable for scheduled maintenance</span>

Çözüm olarak yapmanız gereken şey çok basit. FTP ile sitenizin server&#8217;ina bağlanıyorsunuz ve ana dizinde yer alan **.maintenance** adlı dökümanı siliyorsunuz. Sayfanızı yenilediğinizde siteniz çalışır hale geliyor.

### Peki neden?

Merak edenler için bilgi vermek istiyorum. WordPress kendisini güncellerken öyle herhangi bir plugin güncellemesi kadar basit bir işe girişmiyor, bu işlem sırasında güvenlik açığı oluşmaması gibi konular sebebi ile siteye &#8220;bakımdayım&#8221; mesajını verecek bir düzenleme getiriyor. Sonrasında ise güncelleme için gerekli dosyaların değişiklikleri filan o bu derken aslında server tarafında o işlerine devam ediyor, ancak client olan sizin pencerenizde bağlantı kopuyor. Sıkıntı ise, anladığımız kadarıyla &#8220;bakımdayım&#8221; şeklinde verilen ayarın silinmesi komutunu wordpress kendi kendisine işlemler bitince vermiyor, bunu yine güvenlik sebepli akıllıca bir uygulama olarak değerlendirebiliriz. Client&#8217;tan &#8211; sizin pencerenizden bu komutu bekliyor, ancak geçen süre sebebi ile kopan pencereniz de bu komutu veremiyor. Çözüm olarak ise işte biz ftp&#8217;den bağlanıp bu komutun uyguladığı şeyi, yani o dosyayı silme işlemini yapmış bulunuyoruz&#8230;
