---
id: 2550
title: Ubuntu Server Linux Bahar Temizliği
date: 2015-08-24T10:35:06+02:00
author: Barış Parlan
layout: post
guid: http://www.bparlan.com/?p=2550
permalink: /ubuntu-server-linux-bahar-temizligi/
dsq_thread_id:
  - "5482626174"
image: /wp-content/uploads/2014/09/unix.jpg
categories:
  - Unix | Linux
tags:
  - linux
  - server
  - temizlik apt-get
  - ubuntu
  - update
  - upgrade
format: image
---
<div class="ttr_start">
</div>

Uzun süre bakım -temizlik yapılmamış ubuntu linux server için bahar temizliği zamanı geldiğini, bir program kurulumu sırasında aldığım hata mesajı ile anladım:

<pre>gzip: stdout: No space left on device</pre>

Bilgisayarın dosya sistemi içerisindeki kullanım / doluluk oranlarını görmek için **df -h** komutunu çalıştırınca acı gerçek ile yüzleşiyoruz:

<pre><strong>df -h</strong>
dev/sda1         236M  233M     0 100% /boot</pre>

### Server Kullanılmayan / Eski Kernelleri Temizliği

Sistemin /boot dosyası %100e ulaşmışsa eğer, en etkin çözüm olarak eski kullanılmayan yüklü kernellerin temizlenmesi gerektiğidir. Öncelikle sistemin zarar görmemesi için güncel kullanılan ve sorunsuz çalıştığından emin olunan kerneli öğrenmek için **uname -r** komutunu kullanıyoruz.**  
** 

<pre><strong>uname -r</strong>
3.19.0-22-generic</pre>

Silme işlemine başlamak için sistemde yüklü bütün kernellerin listesini alıyoruz karşımıza:

<pre><strong>dpkg --list | grep linux-image</strong></pre>

Kullandığınız kernelden eski olanları tek tek silmeniz için aşağıdaki komutu çalıştırıyoruz. Her seferince _x.x.x.x_ yerine bir sürüm yazarak ve **uname-r** sonucu çıkanı &#8220;kesinlikle yazmayarak&#8221; sistemdeki diğer kernelleri siliyoruz:

<pre><strong>sudo apt-get purge linux-image-x.x.x.x-generic</strong></pre>

Tekrar tekrar bütün kullanılmayan eski kerneller silindikten sonra grub listesini de güncellemek için (10.04 ve 12.04&#8217;de her purge işleminde update-grub otomatik yapılıyor gördüğüm kadarı ile, ama biz yinede işi garantiye alalım):

<pre><strong>sudo update-grub2</strong></pre>

Bütün işlem bittikten sonra, madem ki herkes satır satır tek tek uğraştı ve işi kavradı, şimdi de Unix sistemlerin komut satırının gücünü görmek için, bütün kernelleri listeleyip, eskileri bulup onları silip grub&#8217;u güncelleyen şu tek satırlık komutu inceleyelim:

<pre>dpkg --list | grep linux-image | awk '{ print $2 }' | sort -V | sed -n '/'`uname -r`'/q;p' | xargs sudo apt-get -y purge</pre>

  * **dpkg &#8211;list** Yüklü paketleri listeliyor
  * **grep linux-image** Yüklü linux image&#8217;lerine bakıyor
  * **awk &#8216;{ print $2 }&#8217;** 2. Sütunu output&#8217;a alıyor, yani paket isimlerini.
  * **sort -V** versiyon sırasına göre diziyor.
  * **sed -n &#8216;/&#8217;\`uname -r\`&#8217;/q;p&#8217;** mevcut kullanılan Kernel&#8217;den öncesini print yapıyor
  * **xargs sudo apt-get -y purge** listelenen kernelleri purge yapıyor.

### Linux Güncellenmesi (Update & Upgrade)

Hazır server bahar temizliği havasına girmişken sistemimizin güncellemelerini yapmayı ihmal etmiyoruz. Sistemin serverlara bağlanıp &#8220;yenilik olarak neler var neler yok?&#8221; diye sorması komutu &#8220;update&#8221;. Update hiç bir programda güncelleme yapmaz, sadece haberdar eden listeleri alır:

<pre>sudo apt-get update</pre>

Listeler geldikten sonra sistemde yüklü olan programların güncellenmesi için verilen komut &#8220;upgrade&#8221;. Liste olarak bunlar güncellenecek, şu kadar MB data inecek sistemde şu kadar MB değişiklik olacak filan şeklinde özet bilgi de geçer.

<pre>sudo apt-get upgrade</pre>

Yaptığımız güncellemelere bir de Kernel&#8217;i güncelleyerek tam bir destek vermek için:

<pre>sudo apt-get dist-upgrade</pre>

### Linux Genelinde Temizlik (Clean &#8211; Autoclean &#8211; Autoremove)

Son olarak linux server bahar temizliği sonrası yerleri süpürmek ve ortalıkta kalan bütün çöpleri &#8211; kullanım dışı programları sistemden temizlemek için yazmamız gereken komutlara geliyoruz. İlgilenen arkadaşlar ister man komutu ile, isterlerse internet üzerinden üç komutun da ayrı ayrı neler yaptıklarını araştırabilirler. İşin özetinde eski kerneller için yüklenmiş olan, ama artık hiç bir &#8220;dependencies&#8221;i kalmamış, hiç bir şey ile ilgili özelliği kalmamış programları silmek &#8211; temizlemek amaçlı komutlar. Sırası ile giriniz:

<pre><strong>apt-get clean</strong>
<strong>apt-get autoclean</strong>
<strong>apt-get autoremove</strong></pre>

<pre>After this operation, 711 MB disk space will be freed.</pre>

Ve işin özetinde başlangıçta girdiğimiz komut ile tekrar bakıyoruz:

<pre><strong>df -h</strong>
/dev/sda1  236M       106M          118M      48% /boot</pre>

Artık diğer pek çok sanal ve reel hafızalarda yaşanan yer kazanımları, güncellenmiş olmanın ise güvenliksel rahatlığı içinde linux kullanımına devam edebilirsiniz.

<div class="ttr_end">
</div>