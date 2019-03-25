---
id: 2759
title: Ubuntu Kullanılmayan Linux Kernel Silmek
date: 2016-01-15T12:09:32+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=2759
permalink: /ubuntu-linux-kernel-silmek/
dsq_thread_id:
  - "5479564870"
article_header:
  type: cover
  image:
    src: /wp-content/uploads/2014/09/unix.jpg
categories:
  - Bilişim
  - Unix | Linux
tags:
  - linux
  - temizlik
  - ubuntu
format: image
---

Ubuntu Server Linux sisteminizde /boot full olduğunda, eski kullanılmayan kernel dosyalarınız biriktiği için bir takım problemler yaşamaya başlarsınız, onları silmek gerekir. Örneğin herhangi bir yükleme yapacağınızda şöyle bir hata almanız çok normaldir:

<pre>E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).</pre>

veya benzer şekilde server açıldığında login olduktan sonra ekrana şöyle bir uyarı hatası gelir, ancak işleyişde o an için bir sıkıntı çıkmaz:

<pre>E: Error: BrokenCount &gt; 0run-parts /etc/update-motd.d/90-updates-available exited with return code 255</pre>

<img class="alignright size-medium wp-image-2761" src="https://i1.wp.com/www.bparlan.com/wp-content/uploads/2016/01/Kernel-Linux.jpg?resize=300%2C237" alt="Kernel Linux" width="300" height="237" srcset="https://i1.wp.com/www.bparlan.com/wp-content/uploads/2016/01/Kernel-Linux.jpg?resize=300%2C237 300w, https://i1.wp.com/www.bparlan.com/wp-content/uploads/2016/01/Kernel-Linux.jpg?w=400 400w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" /> Bu ikinci hatanın pek çok oluşma sebebi söz konusu aslında, zira muhtemel çözümler listesi güncellenmiş olarak <a href="http://ubuntuforums.org/showthread.php?p=11789959" target="_blank">I upgraded, and now I have this error&#8230;</a> linkinde bulunmakta. Ancak benim başıma gelen problem, yine /boot dosyasının dolması ile oluşması durumuydu, ve kesin olan bir şey var ki, bu ikinci örnek olarak sunduğum hata mesajı, Ubuntu Server makinenizin sağlıksız olduğunu &#8211; ciddi problem yaşadığını göstermektedir, ve mutlaka çözülmelidir. Öncelikle command&#8217;da yazacağınız df komutu ile dosya yapınızı ve mevcut yapıda nerenin %kaç dolu olduğunu göstermektedir.

<pre>Filesystem                1K-blocks     Available Use% Mounted on
udev                        1020600       1020600   0% /dev
tmpfs                        206316        201288   3% /run
/dev/mapper/serverfactory  17027924      12514644  23% /
tmpfs                       1031564       1031564   0% /dev/shm
tmpfs                          5120          5120   0% /run/lock
tmpfs                       1031564       1031564   0% /sys/fs/cgroup
/dev/sdb1                3845578572    1542482460  58% /server
/dev/mapper/serverfactory  56635708      17485804  68% /aktif
/dev/sda1                    240972             0 100% /boot
tmpfs                        206316        206316   0% /run/user/1000</pre>

Sonrasında /boot neden dolu, içinde neler var, hangi kernel versiyonları mevcut diye bakmak için şu komutu yazıyoruz:

<pre>dpkg -l linux-image*</pre>

<pre>un  linux-image          &lt;none&gt;          &lt;none&gt;
un  linux-image-3.0      &lt;none&gt;          &lt;none&gt;
ii  linux-image-3.19.0-2 3.19.0-22.22    i386  
rc  linux-image-3.19.0-2 3.19.0-25.26    i386  
ii  linux-image-3.19.0-2 3.19.0-26.28    i386  
ii  linux-image-3.19.0-2 3.19.0-28.30    i386  
ii  linux-image-3.19.0-3 3.19.0-30.34    i386  
ii  linux-image-3.19.0-3 3.19.0-31.36    i386  
ii  linux-image-3.19.0-3 3.19.0-32.37    i386  
ii  linux-image-3.19.0-3 3.19.0-33.38    i386</pre>

Çıkan listede muhtemelen pek çok linux-image-X göreceksiniz. X yerine geçen versiyonların eskileri genel olarak silinmesi problem yaratmayacak, güncellenme sonucunda eskiyen linux kernellerimiz. Ancak emin olmak için aşağıdaki komut ile en güncel ve sistem tarafından kullanılan kerneli öğrenebiliriz:

<pre>uname -r
3.19.0-33-generic</pre>

Küçük bir bilgilendirme notu eklemek istiyorum. 3.19.0-33-generic şeklinde görülen bu &#8220;versiyon&#8221; rakamının açılımı şu şekildedir: 3>Kernel Versiyonu, 19>Majör revizyon, 0>Minör revizyon, 33>Kritik hatalar için yapılmış acil düzeltmeler, generic>dağıtım modeli. Bu noktadan sonra yapmamız gereken aslında basit, aşağıdaki komutu her &#8220;eski&#8221; ve şu an kullanılmayan komut için yazmak, elbette ki x yerine :

<pre>sudo apt-get remove linux-image-x</pre>

Ancak birkaç satır işlem ve paket bilgilendirmesinden sonra aşağıdaki hata ile karşılaşıyor olmanız muhtemel:

<pre>E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).</pre>

Benim bu yazıyı yazma amacım, konunun tam olarak bu noktasında devreye giriyor, zira /boot dolu, kernel eski, ancak silemiyoruz. Zira apt-get remove aslında bir kernel versiyonu silmek için uygun bir komut değil. Esasen komutu şu şekilde yazmalıyız:

<pre>sudo dpkg --force-all -P linux-image-3.16.0-22-generic</pre>

Komutu bu şekilde yazdığınızda, özellikle isim olarak sıkıntı yaşarsanız versiyon noktasında TAB tuşuna basarak sistemin tamamlayabildiği kısımlarını kendisi tamamlamasını sağlayabilirsiniz. 0-22 kısmından sonra TAB tuşuna bastığınızda -generic yerine tam olarak versiyonun bütün eksiklerini tamamlayıp komutu doğru yazmanızı sağlayacaktır. Bu noktada uyarmalıyım ki, en az 2 kerneli sistemde yüklü tutmanızdır. Ayrıca, işlemi tamamladıktan sonra linux-image listesinde görebileceğiniz gibi pek çok eski versiyon &#8220;linux-image-extra-x&#8221; olacaktır. Bunların da, sisteminizden sildiğiniz kernellerin versiyonları ile aynı olanlarını gönül rahatlığı ile silebilirsiniz. Bu noktada aslında komut olarak değişen hiç bir şey yok, örneğin:

<pre>sudo dpkg --force-all -P linux-image-extra-3.19.0-22-generic</pre>

Bu şekilde gerekli gördüğünüz bütün linux-image kernelleri ve linux-image-extra&#8217;ları sildikten sonra, /boot kısmında hatırı sayılır ölçüde yer açılacağı için (benim %70 boşaldı) sisteminizi güncelleyip en güncel kernele eriştikten sonra eski kernelleri (1-2 yedek eski versiyon bırakmayı unutmadan) tekrar silebilirsiniz.

<pre>The following packages have unmet dependencies:
 linux-image-extra-3.19.0-37-generic : Depends: linux-image-3.19.0-37-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.19.0-37-generic but it is not installed
E: Unmet dependencies. Try using -f.</pre>

Yukarıdaki şeklinde bir hata alıyorsanız eğer, mevcut kernel ile ilgili büyük ihtimal ile yükleme sırasında belleğiniz dolmuştu en son, doğal olarak yüklü olması gereken kernel tam &#8211; sağlıklı şekilde yüklenmemişti. Bu noktada o kernelin ismi hata komutunun içerisinde ifade edilir, size tavsiyem spesifik olarak o kernelin yüklenmesi için gerekli komutu girmenizdir. Yukarıdaki örnekte 3.19.0-37-generic için hata vermektedir, ben de komutumu o versiyonu kullanarak yazıyorum:

<pre>sudo apt-get install linux-image-3.19.0-37-generic</pre>

Tekrar atacağınız bir uname -r komutu henüz yeni kerneli kullanmaya başlamadığınızı göstermektedir, ama dpkg -l linux-image* komutu ile de yüklemenin tamam ve gayet yerinde olduğunun sağlamasını yapabilirsiniz.

Bu noktadan sonra eski kernellere dair temizliği netleştirmek ve tekrar bir üzerinden cila atmak için aşağıdaki iki komut sırası ile kullanılabilir:

<pre>sudo apt-get autoremove
sudo apt-get autoclean</pre>

Bu komutlar, hali hazırda &#8220;önceki 2 kernelinizi saklayın&#8221; tavsiyemin farkında olan komutlardır, yani onlar da eski kernelleri çöpe atarlar, ancak garantili olmak için son 2 kernele dokunmazlar, bu yüzden gönül rahatlığı ile kullanabilirsiniz.

Artık yapmanız gereken son şey, sisteme bir clean &#8211; update &#8211; upgrade çekmektir. Sırası ile:

<pre>sudo apt-get clean
sudo apt-get update        # Fetches the list of available updates
sudo apt-get upgrade       # Strictly upgrades the current packages
sudo apt-get dist-upgrade  # Installs updates (new ones)</pre>

Bu noktadan sonra devam etmeden önce bir reboot tavsiye edilir, zira yüklenen kernele geçiş henüz sağlanmadı.
