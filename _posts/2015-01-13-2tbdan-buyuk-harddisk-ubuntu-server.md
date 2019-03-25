---
id: 1982
title: 2TBdan Büyük Harddisk Ubuntu Server
date: 2015-01-13T09:36:28+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=1982
permalink: /2tbdan-buyuk-harddisk-ubuntu-server/
dsq_thread_id:
  - "5485651189"
article header:
  type: cover
  image:
    src: /wp-content/uploads/2014/12/distant-lights-linux-wallpaper-e1424505392313.jpg
categories:
  - Unix | Linux
tags:
  - 2tb
  - bölmek
  - büyük
  - fstab
  - harddisk
  - linux
format: image
---

Eğer mevcut çalışır haldeki Linux Server&#8217;inize 2TB&#8217;dan daha büyük yeni bir harddisk eklemek istiyorsanız, _fdisk_ komutu 2TB limitinden dolayı işinize yaramayacaktır. Bu işlem için, _gdisk_ kullanacağız. Öncelikle harddiski sağlam takabilmişmiyiz, öğrenelim:

`sudo fdisk -l`

`Disk /dev/sda: 74.5 GiB, 80026361856 bytes, 156301488 sectors<br />
Units: sectors of 1 * 512 = 512 bytes<br />
Sector size (logical/physical): 512 bytes / 512 bytes<br />
I/O size (minimum/optimal): 512 bytes / 512 bytes<br />
Disklabel type: dos<br />
Disk identifier: 0xc1e1c64b`

Device     Boot  Start       End   Sectors  Size Id Type  
/dev/sda1  *      2048    499711    497664  243M 83 Linux  
/dev/sda2       501758 156301311 155799554 74.3G  5 Extended  
/dev/sda5       501760 156301311 155799552 74.3G 8e Linux LVM

Disk /dev/sdb: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors  
Units: sectors of 1 * 512 = 512 bytes  
Sector size (logical/physical): 512 bytes / 4096 bytes

Gördüğünüz gibi, /dev/sda yani birincil harddiskimiz gayet formatlı ve bölümlenmiş, böylede sda1 &#8211; sda2 &#8211; sda5 oluşmuş. Ancak /dev/sdb (sizde farklı olabilir alfabe, bende sdb, bütün yazı bu örnekten gidecektir, gerekli yerde siz kendi sisteminize göre değiştiriniz) hiç bir düzenleme yaşamamış.

#### GDisk ile format

Şimdi, fdisk ile neredeyse aynı kullanımı olan gdisk&#8217;i yüklüyoruz. Tek fark, 2TB üzeri harddiskleri (örnekteki 4TB) formatlamaya yarar.

`sudo apt-get install gdisk`

Gdisk&#8217;i, harddiskimizin ismini vererek çalıştırıyoruz.

`sudo gdisk /dev/sdb`

bu aşamada ?&#8217;ne basarak bütün komutların listelenmesini sağlayabilirsiniz, zira çok bir şey de yok açıkçası. Öncelikle **&#8220;new partition&#8221;** yapacağımızdan:

`n`

Akabinde bu partisyon primary olacağından:

`p`

Kaç bölüme bölmek istediğimizi soracak, ben tek ve yekpare istiyorum harddiskimi, eğer daha fazla bölüm istiyorsanız 2-3-4 dilediğinizi söyleyebilirsiniz.

`1`

Eğer tek derseniz, o bölümün &#8220;başlangıç&#8221; ve &#8220;bitiş&#8221; noktalarını sorduğunda &#8220;_default_&#8221; olarak sadece enter&#8217;a basmanız yeterli olacaktır. Linux akıllıdır, ve harddiskin başından sonuna bütünününü atamış olur. Eğer 2-3-4 gibi farklı bölümler oluşturacaksanız, sakince 1&#8217;in başından sonra &#8220;1 şurda bitsin, 2 başlasın, 2 şurda bitsin, 3 başlasın. Harddiskin sonuna kadar da 3 gitsin&#8221; gibi demeniz gerekmektedir. Tek bölüm istediğimden:

`Enter - Enter`

Type Code diye sorduğu şey, harddiskimizin içindeki bölümlemelerin amaçları, bildiğiniz gibi sawp olabilir, logical olabilir, biz bu harddiski salt data arşivi olarak kullanacağımızdan, **8300** yazıyoruz.

`8300`

İşlemler bittikten sonra, bu girdilerden emin olduğumuz taktirde w&#8217;ya basarak bütün işlemlerin aktif hale gelmesini ve harddiske yazılmasını sağlıyoruz. Bir hata, sıkıntı, problem olduysa bu noktaya kadar, hiç panik yapmayın, basitçe **q**&#8216;ya basıp her şeyi iptal edip baştan yapabilirsiniz. Bizde problem yok. Bu yüzden:

`w`

Artık harddiskimiz formata hazır. _/dev/sdb1_ oluşturulmuş durumda. (2-3-4 için /dev/sdb2 filan da elbet). Şimdi bu harddiski formatlıyoruz:

`sudo mkfs /dev/sdb1 -t ext4`

#### Mount yapımı

Şimdi bir aşama daha ileri gidip bu harddiski, bir mount point ayarlayarak &#8220;**mount**&#8221; yapacağız. Yani dosya sistemi içerisinde kullanmaya başlayacağız. Genel olarak insanlar _/media_ veya _/mnt_ gibi bir dosya oluşturup, harddisklerini bu dosyalardaki altdosyalarda tutar, hepsine ulaşabilirler. Size mantığını ifade ediyorum zira ben böyle kullanmıyorum, doğrudan root altına /server ve /aktive şeklinde 2 dosyam var. /aktive dediğimiz, 20 gb&#8217;lık serverinde kurulu olduğu harddisk, ufak tefek işler için orayı paylaşıma açtım. /server dosyasına ise bu yeni harddiski mount yapacağız. Serverlik işi olan girsin.

`sudo mkdir /server`

Bu yarattığım dosyayı &#8220;**writable**&#8221; yapalım:

`sudo chmod 777 /server`

Şimdi de &#8220;mount&#8221; işlemi ile harddiski bu dosyaya atayalım:

`sudo mount /dev/sdb1 /server`

#### Fstab Ayarlaması

Sona yaklaşıyoruz, bu dosyanın, işletim sistemi her açıldığında okunup tanınması için yapmamız gereken sistem temelli bilgilendirme değişikliği:

`sudo pico /etc/fstab`

Açılan döküman ortalama şu şekildedir:  
`<br />
# /etc/fstab: static file system information.<br />
#<br />
# Use 'blkid' to print the universally unique identifier for a<br />
# device; this may be used with UUID= as a more robust way to name devices<br />
# that works even if disks are added and removed. See fstab(5).<br />
#<br />
# <file system> <mount point>   <type>  <options>       <dump>  <pass><br />
/dev/mapper/serverfactory--vg-root /               ext4    errors=remount-ro 0 $<br />
# /boot was on /dev/sda1 during installation<br />
UUID=d198ee4d-571d-476f-af46-495e70ce284f /boot           ext2    defaults     $<br />
/dev/mapper/serverfactory--vg-swap_1 none            swap    sw              0 $<br />
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0<br />
#aktif partition<br />
/dev/mapper/serverfactory--vg-aktif /aktif      ext4    rw      0       0`

Bu dökümanın en altına, şu satırları ekliyoruz (kendi sisteminize göre değiştirmeyi unutmayın lokasyonu ve hedefi:

`#server partition 4TB<br />
/dev/sdb1    /server    ext4    rw    0    0`

Artık _reboot_ ile veya _mount -a_ komutu ile bu değişiklikleri uygulamaya geçirebiliriz. İsterseniz bu /server dosyasını paylaşıma açın, ister bütün arşivinizi oraya kopyalıyın. Coşun, eylenin.
