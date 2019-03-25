---
id: 1967
title: Linux Sisteminiz 32bit mi 64bit mi?
date: 2014-12-25T16:37:03+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=1967
permalink: /linux-sisteminiz-32bit-mi-64bit-mi/
post_views_count:
  - "0"
dsq_thread_id:
  - "5484134076"
article_header:
  type: cover
  image:
    src: /wp-content/uploads/2014/09/unix.jpg
categories:
  - Unix | Linux
tags:
  - linux
  - problem
  - ubuntu
format: image
---

Evet, bazen çok saçma ve basit gelebilir, bir insanın kullandığı linux sisteminin 32bit mi 64bit mi olduğunu öğrenmesi gerekliliği, ancak deneyim göstermiştir ki, bazen çok gereklidir. (:

Aşağıdaki kod, kernel ismini, network host ismini, sürüm, versiyon, makine ismi ve işlemci türünü, işletim sistemini göstermektedir, bu bilgiler ışığında 32bit &#8211; 64bit farkını da elde etmiş olursunuz:

`uname -a`

i686 ve i386&#8217;lar 32bit demektir.  
x86_64&#8217;ler ise 64bit.
