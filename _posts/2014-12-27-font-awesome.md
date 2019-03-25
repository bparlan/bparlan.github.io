---
id: 1973
title: 'Font Awesome &#8211; Icon Derdine Son'
date: 2014-12-27T14:11:22+02:00
author: Barış Parlan
layout: article
guid: http://www.bparlan.com/?p=1973
permalink: /font-awesome/
dsq_thread_id:
  - "5481678377"
article header:
  type: cover
  image:
    src: /wp-content/uploads/2014/12/how-to-switch-fontawesome-icon-mouseover-e1424505337869.jpg
categories:
  - 'İnceleme &amp; Tanıtım'
tags:
  - awesome
  - font
  - ikon
  - sembol
  - wordpress
format: image
---

Duyanların &#8220;neden daha önce hiç düşünemedik lan bunu&#8221; dediği, ve hemen kullanmaya başladığı Font Awesome, özette bütün icon taleplerinizi sona erdiren bir font tipi. Dökümanı siteniz ile kullanmaya başlıyorsunuz, sonrasında ise mevcut yüzlerce sosyal medya &#8211; web site tasarımı için olmazsa olmaz diyebileceğiniz ikon, simgle, sembol, bu font dosyası ile birlikte elinizin altında bulunuyor. Font&#8217;lara renk verebildiğinizden bu ikonlara da renk verebiliyorsunuz. Mevcut yazıyı okuduğunuz sayfamdaki &#8220;arama&#8221; ve diğer bütün sosyal medya ikonları, esasta bu font dökümanından çekilmekte&#8230; Mutlaka incelemenizi ve bir deneme yapmanızı tavsiye edeceğim, web tasarımı konseptinde yep yeni bir standart olmaya aday FontAwesome hakkında daha fazla bilgiyi <a title="FontAwesome" href="http://fontawesome.io/" target="_blank">bu linke tıklayarak</a> alabilirsiniz. Kendisi, GitHub (<a title="FontAwesome GitHub" href="http://fortawesome.github.io/Font-Awesome/" target="_blank">FontAwesomeGitHub</a>) üzerinden geliştirilen OpenSource bir sistemdir&#8230;

#### Chrome Gözükmüyor mu?

Ayrıca, Heuman vb. wordpress teması kullanıyor, ve fakat browserinizde FontAwesome ikonları kare şeklinde, yani arızalı gözüküyorsa, farklı browserlarda deneme yapınız. Eğer Chrome vs. dahil bütün browserlarda arıza mevcut ise, aşağıdaki satırları, Child Theme&#8217;nizin function.php kodunun başına ekleyiniz:

`//* Load Font Awesome<br />
add_action( 'wp_enqueue_scripts', 'enqueue_font_awesome' );<br />
function enqueue_font_awesome() {<br />
wp_enqueue_style( 'font-awesome', '//netdna.bootstrapcdn.com/font-awesome/4.1.0/css/font-awesome.min.css'); }`

Eğer sadece Firefox&#8217;da arıza alıyorsanız, aşağıdaki satırları .htaccess dökümanınıza ekleyiniz:

`<FilesMatch ".(ttf|otf|eot|woff)$"><br />
<IfModule mod_headers.c> Header set Access-Control-Allow-Origin "*"<br />
</IfModule> </FilesMatch>`
