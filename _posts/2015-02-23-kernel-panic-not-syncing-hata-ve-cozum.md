---
id: 2358
title: 'Kernel Panic Not Syncing &#8211; Hata ve Çözüm'
date: 2015-02-23T10:17:32+02:00
author: Barış Parlan
layout: post
guid: http://www.bparlan.com/?p=2358
permalink: /kernel-panic-not-syncing-hata-ve-cozum/
post_views_count:
  - "0"
dsq_thread_id:
  - "5479554447"
image: /wp-content/uploads/2014/12/distant-lights-linux-wallpaper-e1424505392313.jpg
categories:
  - Unix | Linux
tags:
  - çözüm
  - initramfs
  - kernel
  - noy syncing
  - panic
format: image
---
<div class="ttr_start">
</div>

Ubuntu Server son update &#8211; upgrade aktivitesinden sonra Kernel sürümünü 3.16 dan 3.18 e yükseltince Kernel Panic &#8211; Not Syncing diyebileceğimiz hata çözümünü yazacağım. Hata şöyle:

Kernel panic &#8211; not syncing : VFS : Unable to mount the root fs on unknown-block(0,0)

Bu hata, kernel update ettikten sonra initramfs modülünün yanlış yeri (genelde /bin/true lokasyonunu) işaret etmesi, root&#8217;u göstermemesi sonucu yaşanan bir sıkıntı, ve root&#8217;un bulunamaması, ubuntu serverin açılmamasını sağlıyor. Hiç bir tty açılmadığı gibi, komut girmek de mümkün olmuyor. Çözümü ise teorik olarak önce eski bir Kernel sürümü ile bilgisayarı açıp, en son güncellenen kernel&#8217;in initramfs&#8217;sini baştan yüklemek&#8230;

#### Çözüm

Öncelikle bilgisayarı baştan başlattığımızda Grub Loader ekranında Ubuntu değil, &#8220;Advanced Ubuntu&#8221; seçiyoruz, ve çalışan bir Kernel versiyonu bulana kadar sırası ile eski Kernel versiyonları ile bilgisayarı açmaya çalışıyoruz.

Eski ama çalışan bir kernel versiyonu bulup bilgisayarı açınca, öncelikle en güncel Kernel versiyonumuzun tam ismini öğrenmek için şu komutu giriyoruz:

`cat /proc/version`

Bu komut, çalışan değil, yüklü olan en son versiyonu gösterecektir. Akabinde aşağıdaki komutu yazıyoruz, ancak -k&#8217;dan sonra en güncel versiyon ismini de giriyoruz:

`sudo update-initramfs -u -k 3.18.0-13-generic`

Esasen -k &#8216;nın yanına cat /proc komutu ile öğrendiğimiz versiyonu yazmamız gerekse de, açıkçası ben bütün initramfs&#8217;lerin güncellenmesinde bir sakınca görmediğimden, eğer bu versiyon ismi konusunda sıkıntı yaşarsanız, şu komutu da kullanarak bütün güncellemeleri yapabilirsiniz:

`sudo update-initramfs -u -k all`

Son olarak, bozuk olan paketlerin veya bayraklı (arızalı) olarak işaretli paketlerin tekrar ayarlanması için aşağıdaki komutu giriyoruz:

`sudo dpkg –reconfigure`

Artık serverinize bir restart atarak sıkıntının çözülmüş olduğunu test edebilirsiniz.

<div class="ttr_end">
</div>