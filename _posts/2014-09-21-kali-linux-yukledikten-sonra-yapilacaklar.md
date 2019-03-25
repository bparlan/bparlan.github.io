---
id: 1919
title: Kali Linux Yükledikten Sonra Yapılacaklar
date: 2014-09-21T20:49:35+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=1919
permalink: /kali-linux-yukledikten-sonra-yapilacaklar/
post_views_count:
  - "0"
dsq_thread_id:
  - "5479395123"
wp_featherlight_disable:
  - ""
article header:
  type: cover
  image:
    src: /wp-content/uploads/2014/09/unix.jpg
categories:
  - Rehber
  - Unix | Linux
tags:
  - hacking
  - kali
  - kurulum
  - linux
  - rehber
format: image
---

Bilgisayarınıza Kali Linux yükledikten sonra yapılacaklar şeklinde bir liste oluşturdum ki, hem kendim ihtiyaç hissettiğimde doğrudan danışayım, hem de başkaları faydalanabilsin bu rehberden. Eklenmesi gerektiğini düşündüğünüz maddeler veya güncellenmesi gerekenler olursa eğer, yazıya yorum olarak yazabilirsiniz.

#### Yapılacaklar Listesi

  1. &#8220;Device not managed&#8221; Hatası  
    **/etc/NetworkManager/NetworkManager.conf** dökümanını açın, **managed=false** satırını **managed=true** yapıp kaydedin.
  2. Repository listesini düzenlemek  
    **/etc/apt/sources.list** dökümanını açın, ve oradaki listeyi silip (veya comment&#8217;leyip), yerine aşağıdaki listeyi yazıp kaydedin.</p> 
    <pre><em>## Regular repositories</em>

 <em>deb http://http.kali.org/kali kali main non-free contrib</em>

 <em>deb http://security.kali.org/kali-security kali/updates main contrib non-free</em>

 <em>## Source repositories</em>

 <em>deb-src http://http.kali.org/kali kali main non-free contrib</em>

 <em>deb-src http://security.kali.org/kali-security kali/updates main contrib non-free</em></pre>

  3. Apt-Get Hızlandırmak  
    **/etc/resolv.conf** dökümanını açın, Google&#8217;ın DNS&#8217;leri olan aşağıdaki ns bilgilerini, dökümanda bulunanlar ile değiştirin.</p> 
    <pre><em>nameserver 8.8.8.8</em>

 <em>nameserver 8.8.4.4</em></pre>

  4. Yapılanların Toparlanması 
    <pre><em>apt-get clean</em>

 <em>apt-get update</em>

 <em>apt-get upgrade</em>

 <em>apt-get dist-upgrade</em></pre>

  5. PulseAudio Uyarısını Düzeltin  
    **/etc/default/pulseaudio** dökümanını açın.  
    **PULSEAUDIO\_SYSTEM\_START=0** değerini **1** olarak değiştirin.  
    **reboot**
  6. Ses Sorununu Çözmek  
    Boot sırasında Ses&#8217;in açılmasını sağlamak için öncelikle alsa-utils&#8217;i kurmalısınız.</p> 
    <pre><em>apt-get install alsa-utils -y</em></pre>
    
    Sağ üst köşedeki küçük ses kontrol ikonuna sağ tıklayıp **Sound Preferences**&#8216;i seçin.  
    Output Volume slider&#8217;ini **ON&#8217;**a getirin. Pencereyi kapatın.  
    Artık unix&#8217;inizin sesi açık.</li> 
    
      * Kali Linux&#8217;e Java JDK Yüklemek  
        Son java sürümünü Google&#8217;a &#8220;Oracle Java Download&#8221; arayarak bulun, uygun mimarideki linux sürümlü java tar.gz&#8217;yi download edin. Aşağıdaki komutlarla arşivi açıp /opt klasörüne yerleştirin:_tar -xzvf /root/jdk-7u45-linux-x64.tar.gz_  
        _mv jdk1.7.0_45 /opt_  
        _cd /opt/jdk1.7.0_45_Aşağıdaki komutlar ise, bu yüklediğiniz Java&#8217;yı default olarak kaydetmenize yarar (kod içerisinde Java versiyonunuza göre düzeltmeler yapmanız gerekebilir, lütfen copy+paste yapmayın, inceleyin, araştırın)</p> 
        <pre><em>update-alternatives --install /usr/bin/java java /opt/jdk1.7.0_45/bin/java 1</em>

 <em>update-alternatives --install /usr/bin/javac javac /opt/jdk1.7.0_45/bin/javac 1</em>

 <em>update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /opt/jdk1.7.0_45/jre/lib/amd64/libnpjp2.so 1</em>

 <em>update-alternatives --set java /opt/jdk1.7.0_45/bin/java</em>

 <em>update-alternatives --set javac /opt/jdk1.7.0_45/bin/javac</em>

 <em>update-alternatives --set mozilla-javaplugin.so /opt/jdk1.7.0_45/jre/lib/amd64/libnpjp2.so</em></pre>
        
        Test etmek için aşağıdaki adrese gidin:  
        _http://www.java.com/en/download/installed.jsp_</li> 
        
          * Flash Yükleyin  
            Flash yüklemesi, Kali için diğer bütün unix&#8217;lerde olduğu gibi, kolay bir işlemdir:</p> 
            <pre><em>apt-get install flashplugin-nonfree</em>

 <em>update-flashplugin-nonfree --install</em></pre>
        
          * Tor Yükleyin  
            Ne olduğunu bilen bilir.</p> 
            <pre><em>apt-get install tor</em>

 <em>service tor start</em>

 <em>proxychains iceweasel</em></pre>
        
          * FileZilla Yükleyin 
            <pre><em>apt-get install filezilla filezilla-common -y</em></pre>
        
          * HTOP ve NetHogs Yükleyin  
            _apt-get install htop nethogs -y_  
            Yüklemeden sonra çalıştırmak için aşağıdaki komutları kullanabilirsiniz:</p> 
            <pre><em>htop</em>

 <em>nethogs eth0</em>

 <em>nethogs wlan0</em></pre>
        
          * AutoLogin Ayarlaması  
            **/etc/gdm3/daemon.conf** dökümanını açın,  
            2 Satırın commentlerini silin, döküman şöyle görünmeli:</p> 
            <pre>[daemon]

 <em># Enabling automatic login</em>

 <em>  AutomaticLoginEnable = true</em>

 <em>  AutomaticLogin = root</em></pre>
            
            Çalışması için **reboot** yapın.</li> </ol> 
            
            #### **Kendinizin çözmesi gereken, ama yapmanızı tavsiye ettiğim diğer notlar:**
            
              * NVidia / AMD Ekran Kartı Driverinizi yükleyin
              * GPU Processing Ayarlarını Yapın
              * Reminna Yüklemesi
              * GDebi Package Manager Yüklemesi
              * Theme Yüklemesi
              * XFCE Desktop Yüklemesi
            
            <div class="ttr_end">
            </div>