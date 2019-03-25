---
id: 2806
title: Web Sitesi Optimizasyon ve Hızlandırma
date: 2017-06-19T20:20:09+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=2806
permalink: /web-sitesi-optimizasyon-ve-hizlandirma/
dsq_thread_id:
  - "5924465869"
wp_featherlight_disable:
  - ""
article_header:
  type: cover
  image:
    src: /wp-content/uploads/2017/06/website-optimizasyon.jpg
categories:
  - Bilişim
  - Rehber
tags:
  - optimizasyon
  - rapor
  - website
format: image
---

Google ve insanların en büyük ortak noktası, hızlı açılan websitelerini sevmeleridir. Başarılı optimizasyon bu yüzden çok önemlidir. İster wordpress, joomla, drupal vb. CMS (content management system) kullanıyor olun, isterseniz kendi sitenizi baştan sonra kendiniz yazmış olun, sayfanızın yüklenme hızı bütünüyle sitenize yaptığınız optimizasyon ile ilgilidir. Bu yazıda dört temel optimizasyon testini tanıtmanın yanında, nice zamandır notlarını düştüğüm daha pek çok optimizasyon ile ilgili yöntem ve aracın da tanıtımlarını yaptım. Öncelikle mahşerin dört atlısı olarak adlandırabileceğimiz dört önemli optimizasyon test sistemini tanıtmak ile başlayalım: Pingdom, GTmetrix, Varvy ve Google PageSpeed.

  1. **[Pingdom](https://tools.pingdom.com/) Website Speed Test**  
    Testin hangi merkezden yapılacağını seçmenizi sağlayan Pingdom, yükleme süres, sayfa büyüklüğü, File Request Flow gibi güzel sonuçların yanında, notunuzu düşüren ana etkenleri listeleyip isterseniz nasıl düzeltebileceğinize dair çözüm araştırmasına girmeniz için size yol yordam göstermekte.
  2. **[GMetrix](https://gtmetrix.com/) Optimization**  
    Hem Pagespeed and YSlow skoru sağlayan sistem özellikle Waterfall grafiğini inceleyerek content &#8211; server &#8211; user konularında her bir saniye hangi döküman ne kadar milisaniyede yüklenmiş ve ne gibi sıkıntılara yol açmış gibi detaylara inmek isteyenler için tavsiye edebileceğim bir kaynak.
  3. **[Varvy](https://varvy.com/pagespeed/) PageSpeed**  
    Varvy bünyesinde SEO test araçlarından CSS &#8211; JS minimize araçlarına kadar pek çok farklı konuda test ve bilgi sistemi bulabilirsiniz. Ancak özellikle Varvy Pagespeed ve Varvy SEO, test sonuçlarını sunarken muazzam detaylı ve bilgilendirici tablolar ile sitenizi optimize etmek noktasında çok sağlam bir kaynak olarak size destek sağlayabilecek durumdadır.
  4. **[Google](https://developers.google.com/speed/pagespeed/insights/) PageSpeed Insights**  
    Her ne kadar şimdiye kadarki test sayfalarına tek tek girip bütün notlarınızı %100 yapmış olsanız bile sanırım bu test hüsranı dibine kadar yaşayacağınız yerdir, ya da bütün bu durum sadece benim hüsnü kuruntum. Zira ne kadar uğraşırsam uğraşayım Google&#8217;ın Insights sistemi diğer sitelerde en azından B+ (85/100) ortalamalı sayfalara bile hiç sıkılmadan 45/100 notunu verebilmektedir.

### Diğer Optimizasyon Kaynakları

**Load Tester Tool  
** 5 Dakika boyunca her saniyede 20 request sayfanıza gelse serveriniz &#8211; siteniz bu yükü kaldırabilir mi? Buna benzer soruların cevabını arıyorsanız eğer, [LoadTesterTool](http://loadtestertool.com) tam size göre bir online test aracı. Elbette ki kötü amaçlı kişilere alet olmaması için, bu test sistemini kullanmak istiyorsanız önce siteden sayfanız için hazırlanmış .xml dosyasını indirip ftp ile sitenize yüklemeniz gerekmektedir.

**Gzip Testi  
** Web sitenizdeki içeriği gzip metodu ile küçülterek ziyaretçiye sunma sistemi internet üzerinde standartlaşmış bir uygulama.  [CheckGzipCompression.com](http://checkgzipcompression.com/) ile sitenizin GZip uygulaması doğru şekilde ayarlanmışmı diye kontrol edebilirsiniz. WordPress siteler için .htaccess düzenlemesi, plugin kurulumu gibi pek çok farklı yol ile çözebileceğiniz bu metod, web site optimizasyonunun olmazsa olmazı bir uygulamadır.

**CSS Min Tool  
** W3Club tarafından sunulan [CSSMin](http://tools.w3clubs.com/cssmin/) adlı araç, mevcut CSS dosyalarınızı doğrudan crunch yaparak küçültüp minimize etmeye yaramaktadır.

**Redirect Kontrolü  
** Örnek olarak kendi domainimi kullanarak konuyu izah edeceğim: http://www.bparlan.com adresi uygun ve çalışır bir adres. Peki https://www.bparlan.com? Veya doğrudan bparlan.com? Bütün bu www / non-www ve http / https opsiyonlarının oluşturduğu yönlendirme zinciri sayfanın yüklenmesinde ciddi bir yavaşlamaya sebep olabilmektedir. Kendi websitenizin kontrolünü yapmak için [Redirect Mapper](https://varvy.com/tools/redirects/) adlı sistemi kullanabilirsiniz. Ne kadar az &#8220;redirect&#8221; sonucu çıkarsa o kadar iyi bir başarı elde etmiş olur sayfanız. Örnek olarak benim sayfam bütün dört kategorinin toplamında sadece 1 redirect alarak mükemmel başarıdan bir puan aşağıya düşmekte, ancak benim için yeterli bir sonuç bu.

**Kısa Kısa  
** [_ipv6prepared.com_](http://www.ipv6prepared.com) / Sayfanız IPv6 sistemine uyumlu mu diye merak ediyorsanız&#8230;  
[_richpreview.com_](http://www.richpreview.com) / Sayfanız sosyal medyada paylaşıldığında nasıl bir preview görüntüsü oluşacak diye merak ediyorsanız&#8230;  
[_detectcharset.com_](http://www.detectcharset.com) / Sayfanızın encode olduğu karakter biçimi browserlar tarafından nasıl algılanıyor diye merak ediyorsanız&#8230;

**Bonus:** Aşağıdaki problem ile karşılaşırsanız, uğraşmayın!  
**_Server static content from a cookieless domain_  
** Eğer websiteniz için CloudFlare CDN kullanıyorsanız ne yazık ki bu problemin bir çözümü yok. KeyCDN veya diğer alternatiflerde uzun ve ciddi adımlarla çözülebilecek bu problem bir başka yazı konusu olacak kadar uzun ve incelikli bir iş.
