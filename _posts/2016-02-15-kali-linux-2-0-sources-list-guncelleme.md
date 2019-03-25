---
id: 2831
title: Kali Linux 2.0 sources.list güncelleme
date: 2016-02-15T08:40:10+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=2831
permalink: /kali-linux-2-0-sources-list-guncelleme/
dsq_thread_id:
  - "5479542585"
article header:
  type: cover
  image:
    src: /wp-content/uploads/2014/09/unix.jpg
categories:
  - Bilişim
  - Unix | Linux
tags:
  - error
  - kali
  - linux
  - package
  - sources.list
format: image
---

Kali Linux 2.0 yüklemesi sırasında eğer herhangi bir network mirror seçmezseniz, büyük ihtimalle &#8220;basic&#8221; dediğimiz temel sources.list kaynakları ile kurulmuş bir sisteminiz olur. Bu liste, &#8220;apt&#8221; komutu ile yüklemeye çalıştığınız aplikasyon / program paketlerinin temelini oluşturur. Eğer verimli &#8211; düzgün bir kaynak listeniz olmaz ise, örnek olarak &#8220;htop&#8221; adlı programı veya &#8220;software-center&#8221; adlı programı yüklemekte sıkıntı yaşarsınız. En basit örnek ile: _E: Package &#8216;software-center&#8217; has no installation candidate_ şeklinde bir hata ile karşılaşırsınız. Şimdi Kali Linux kurulumunda hangi sources.lst dökümanını kullanmayı seçtiğinize bakmaksızın, düzgün bir kaynak kullanımı için yapılması gerekenlere bir bakalım.

Öncelikle mevcut list dökümanımızın bir yedeğini alıyoruz, herhangi bir sıkıntı anında tekrar yerine koyabilmek için bu önemli bir nokta:

<pre>mv /etc/apt/sources.list /etc/apt/sources.list-backup</pre>

Şimdi mevcut list dökümanını aşağıdaki komut ile güncellemek için açalım:

<pre>sudo pico /etc/apt/sources.list</pre>

Ve aşağıdaki satırları sources.list&#8217;in içindekilerin yerine yerleştirelim. Ancak unutmayınız, listedeki yazılı olanların altına &#8220;ekleme&#8221; yapmak Yanlıştır. Sisteminizin kesinlikle stabilitesini bozar. Yapmanız gereken, listeyi silip, aşağıdakileri yazmaktır:

<pre>deb http://http.kali.org/kali kali-rolling main contrib non-free
deb-src http://http.kali.org/kali kali-rolling main contrib non-free</pre>

Dökümanı kaydedip kapattıktan sonra update çekerek mevcut liste üzerinden güncelleme yapınız:

<pre>apt-get update</pre>

Artık _E: Package &#8216;software-center&#8217; has no installation candidate_ hatasını görmemeniz gerekir. Bu noktada şu konudan bahsetmek gerekir, Linux kurulumu sırasında &#8220;Use a Network Mirror&#8221; sorusu çıkar karşımıza, o soruya Yes veya No şeklinde cevap verip geçebilmekteyiz. No denildiği taktirde &#8220;basic&#8221; dediğimiz kaynak listesi üzerinden kurulum gerçekleşir. Ama eğer Yes dersek, karşımıza seçmemiz için linux kütüphane listesi çıkar. O listeden uygun olanını (artık 32bit 64bit konuları ile ilgili olarak) seçip yüklemeye devam edebilirsiniz. Network Mirror ile ilgili daha fazla bilgi için <a href="http://docs.kali.org/community/kali-linux-mirrors" target="_blank">Official Kali Linux Mirrors</a> sayfası uygundur. ThoughtlessKvothe&#8217;nin sorusu üzerine bu konuya dair bilgi paylaşımı yaptım. Böyle bir hatayı ben yaşamadığım için anlatımımı araştırma temelli ifade ettim, eğer bir problem sıkıntı oluşursa lütfen belirtiniz, gözden geçiririm.
