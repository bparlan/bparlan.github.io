---
id: 3647
title: Ubuntu 16.04 LTS Yükledikten Sonra Yapılacaklar
date: 2017-07-30T15:18:48+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=3647
permalink: /ubuntu-16-04-lts-yukledikten-sonra-yapilacaklar/
wp_featherlight_disable:
  - ""
ampforwp_custom_content_editor:
  - ""
ampforwp_custom_content_editor_checkbox:
  - null
ampforwp-amp-on-off:
  - default
dsq_thread_id:
  - "6027994318"
article header:
  type: cover
  image:
    src: /wp-content/uploads/2014/12/distant-lights-linux-wallpaper-e1424505392313.jpg
categories:
  - Unix | Linux
tags:
  - linux
  - lts
  - rehber
  - ubuntu
  - yapılacaklar
  - yardım
  - yükleme
format: image
---

Ubuntu 16.04 LTS (Long-Term Support / Uzun Süreli Destek) sürümünü bilgisayarınıza yükledikten sonra tam olarak neler yapmanız gerektiğine dair bir fikriniz yok ise, aşağıdaki listeyi adım adım takip ederek hem çok daha sağlıklı bir ubuntu işletim sistemine kavuşmuş olursunuz, hem de genel olarak linux bünyesinde işlerin nasıl yürüdüğüne dair rehber eşliğinde uygulama yaparak deneyim kazanma fırsatını değerlendirmiş olursunuz.

  1. **Güncelleme**
Yükleme sonrası Güncellemeleri yapmak ile işe başlamak önemli elbette. Software Updater aracını çalıştırıp check for updates düğmesine basıp, sonrasında da install diyerek yeni yüklenmiş ubuntu&#8217;yu bir de güncellemiş olursunuz.  
Komut satırı kullanmak isteyenler için:

<pre>sudo apt update && sudo apt upgrade</pre>

  2. **Canonical Partners&#8217;i etkinleştirmek**
Üçüncü parti yazılım üreticilerinin repo&#8217;larına bağlanıp yazılım kaynakları listesini kullanarak Skype ve benzeri pek çok farklı popüler programa da erişiminiz kolaylaşmış olur. Bunu yapmak için Software & Updates&#8217;deki Other Software tab&#8217;ında bulunan Canonical Partners kutularına tik atmanız yeterlidir.

  3. **Additional Drivers Paneli**
Ekran kartı &#8211; CPU gibi diğer sürücüleri yüklemek için yine Software & Updates düğmesine basıp, açılan menüde Additional Drivers tab&#8217;ına geçip kısa bir beklemenin ardından Install ve Apply Changes diyerek gerekli güncellemeler sağlanır.

  4. **Ubuntu Restricted Extras yüklemek**
Ubuntu sistemi tarafından legal limitler yüzünden standart bir şekilde desteklenmeyen bir takım &#8220;kısıtlı extralar&#8221; diyebileceğimiz MP3, MP4, AVI gibi formatların desteklenmesini sağlayan media codec&#8217;ler söz konusu. Eğer yükleme sırasında bunların da dahil edilmesini sağlayan opsiyonu seçmeyi unuttuysanız komut satırı işinizi çözecektir:

<pre>sudo apt-get install ubuntu-restricted-extras</pre>

  5. **Synaptic Packet Management**
Paket yönetim sistemi olan Synaptic ile sisteminize yüklenen ve yükleyebileceğiniz bütün paketlerin muazzam listesine ulaşabilir, bütün paketlerin kontrolünü elinize alabilirsiniz:

<pre>sudo apt install synaptic</pre>

  6. **Guest Account silmek**
Bilgisayarınızda &#8220;Misafir hesabı&#8221; ile oturum açma opsiyonunu iptal ederek yabancı kişilerin şifre girmeden sisteminize erişmesini engelleyebilirsiniz, ve engellemelisiniz de. Öncelikle gksu paketini yüklüyoruz:

<pre>sudo apt-get install gksu</pre>

Sonra terminal&#8217;de aşağıdaki komutu girerek lightdm.conf dosyasını düzenlemek için açıyoruz:

<pre>gksu gedit /etc/lightdm/lightdm.conf</pre>

Aşağıdaki ayarları aynen copy+paste yapıyoruz dökümanın sonuna, kaydedip kapatıyoruz:

<pre>[SeatDefaults]
greeter-session=unity-greeter
allow-guest=false</pre>

Ve aşağıdaki komutu terminale girerek lightdm&#8217;i baştan başlatıyoruz (restart olayı, kaydedilmemiş dökümanlarınız gider):

<pre>sudo /etc/init.d/lightdm restart</pre>

Artık logout olduktan sonra Guest Account şeklinde bir login opsiyonu göremeyeceksiniz.

  7. **Dash üzerinden Online Search**
Dash eskisi gibi aramalarda internet üzerinden arama gerçekleştirmemekte. Her ne kadar güvenlik için kullanıcıların talep ettiği bir seçenek olsa da, online sonuçların direk oradan erişilebilmesi güzel bir özellikti. Online arama sonuçlarını Dash&#8217;da görebilmek için:  
_Ubuntu System Settings > Security & Privacy > Search_  
bölümüne gidiyoruz ve **Off** olan slider&#8217;ı **On** yapıyoruz.

  8. **Firewall kurulumu**
Elbette ki Ubuntu işletim sistemi, diğer bütün linux sistemler gibi hiç bir şekilde virüsler tarafından etkilenmezler. Ancak gelin görün ki konu saldırı olunca Firewall bütün sistemlerin ihtiyacı olduğu bir konu. Ubuntu kendi bünyesinde UFW adlı firewall ile gelse de bu program çalışır halde sunulmuyor. Firewall&#8217;ınızı çalıştırıp daha rahat kontrol edebilmenizi sağlayan GUFW&#8217;yi yükleyebilirsiniz:

<pre>sudo apt-get install gufw</pre>

  9. **Java Plugin**
Java, Ubuntu için sonradan yüklenmesi gereken bir plugin.

<pre>sudo apt install icedtea-8-plugin openjdk-8-jre</pre>

 10. **Telegram kurulumu**
Çok hızlı, güvenli ve basit bir mesajlaşma sistemi olan Telegram ile tanışmadıysanız eğer, gün bugündür:

<pre>sudo add-apt-repository ppa:atareao/telegram
sudo apt update
sudo apt install telegram</pre>

 11. **Unity Tweak Tool**
Unity Tweak Tool adlı programını kurmanız karşılığında Unity masaüstü ve menülerinin hem görünüş hem de işleyişine dair çok ciddi bir kontrol gücü elde etmiş olacaksınız.

 12. **Minimise on Click ayarlaması**
App launcher&#8217;da bir icon&#8217;a bastığınızda o program açılır. Peki tekrar bastığınızda? Minimize olması çok pratik duruyor değil mi? Evet ama default bir durum değil bu. Yapmak için Unity Teak Tool yükledikten sonra:  
_Unity Tweak Tool > Unity > Launcher > Minimise_  
ile bu ayarı gerçekleştirmiş olursunuz. Veya alternatif olarak aşağıdaki komutu da komut satırından girebilirsiniz:

<pre>gsettings set org.compiz.unityshell:/org/compiz/profiles/unity/plugins/unityshell/ launcher-minimize-window true</pre>

 13. **App Launcher&#8217;i aşağıya almak**
Windows kullanımından Ubuntu&#8217;ya geçenler için en pratik UI davranışlarından birisi de, App Launcher denilen sol taraftaki program icon&#8217;larının ekranın alt kısmına yatay olarak yerleşmesidir sanırım. Bunu yapmak için yine Unity Tweak Tool ile:  
_Unity Tweak Tool > Unity > Launcher > Position_  
ayarını uygulayabilir, veya aşağıdaki komutu girebilirsiniz:

<pre>gsettings set com.canonical.Unity.Launcher launcher-position Bottom</pre>

 14. **Video Oynatıcısı**
Standart olan gelenden daha güzel bir video player kurmanız şiddetle tavsiye edilir. VLC, Miro veya SMPlayer en popüler seçenekler arasında. Aşağıdaki komut ise VLC yüklemeye yarıyor:

<pre>sudo apt install vlc</pre>

 15. **Bulut Hesaplarını Senkronize Etmek**
Dropbox, OneDrive, Google Drive gibi hizmetlerden faydalanarak kişisel dosyalarınızın düzenli yedeğini tutmanızı ve gerekli gördüğünüz dosyalara her yerden erişebilmenizi sağlayan sistemlerin tamamı Ubuntu tarafından desteklenmektedir. Eğer Windows &#8211; Ubuntu dual boot yapmışsanız, dropbox&#8217;unuzun ortak bir harddiskten aynı anda nasıl sync olacağını çok yakında sizlerle paylaşacağım.

 16. **Online Hesaplar ile entegrasyon**
System Settings > Online Accounts bölümünden, sosyal medya vb. hesaplarınızın loginlerini yapıp bilgisayarınızın internet hesaplarınız ile maksimum entegre şekilde çalışmasını sağlayabilirsiniz.

 17. **BleachBit Sistem Temizleyici**
Sisteminizi temiz ve hızlı bir şekilde kullanmaya uzun süreler devam etmeniz için yapmanız gereken onlarca bakımı arka planda sizin için yapmayı hedefleyen BleachBit programı ile bütün sisteminizin kontrolünü ve temizliğini tek bir merkezden yapabilirsiniz.

 18. **Hayırlı Olsun**
Bundan sonrası düzenli aralıklarla aşağıdaki iki komutu çalıştırmak:

<pre>sudo apt-get update
sudo apt-get upgrade</pre>

 19. **_Başka insanlara Ubuntu&#8217;dan bahset!_**

Ayrıca bu yazının size bir faydası dokunduğunu düşünüyorsanız bana teşekkür etmek için yazıyı paylaşmanız ve sitedeki mail listesine üye olmanız gayet yeterli olur (: Kaynaklarınız açık olsun!
