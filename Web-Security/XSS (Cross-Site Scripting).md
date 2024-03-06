<h1 align="center"> XSS (Cross-Site Scripting)  </h1>

<h2> XSS (Cross-Site Scripting) Nedir? </h2>

Siteler arası komut dosyası çalıştırma veya XSS saldırısı, savunmasız bir web uygulamasının parçası olarak kötü amaçlı kod çalıştırmayı içeren bir siber saldırı yöntemidir. 
SQL injectionları gibi diğer saldırı vektörlerinin aksine XSS uygulamayı doğrudan hedeflemez, öncelikli olarak kullanıcıyı hedefler.

<h2> XSS (Cross-Site Scripting) Nasıl Çalışır? </h2>

![XSS-1](https://github.com/oakkaya098/Cyber-Security/assets/152402130/846dabc5-002c-499e-b362-f8ea98f85051)


Bilgisayar korsanlarının XSS gerçekleştirmek için öncelikle hedeflenen kişinin ziyaret ettiği bir web sitesine kötü amaçlı kodu (yük) enjekte etmenin bir yolunu bulması gerekir. 
Yürütme, bir web sayfası yüklendiğinde veya bir kullanıcı köprüler gibi belirli öğelerin üzerine geldiğinde başka şekillerde tetiklenebilir.

Web sitesi veya uygulamada uygun veri temizliği yoksa, kötü amaçlı komut dosyası hedeflenen kişinin sisteminde kod yürütür. 
Komut dosyası, görünüşte güvenilir bir web sitesinden geldiği için hedeflenen kişinin tarayıcısı, meşruiyetini sorgulamadan onu çalıştırır.

Kötü amaçlı komut dosyası, güvenilir web sitesi adına hareket ettiğinden, 
oturum belirteçleri ve çerezler dahil olmak üzere müşterinin tarayıcısında saklanan potansiyel olarak hassas bilgilere erişebilecektir.

<h2> XSS (Cross-Site Scripting) Saldırılarının Sebepleri </h2>

Siteler arası Komut Dosyası Çalıştırma (XSS) saldırıları aşağıdaki durumlarda gerçekleşir:

<ul>

  <li> Veriler bir web uygulamasına güvenilmeyen bir kaynaktan, çoğunlukla bir web isteğinden girer. </li>

  <li> Veriler, kötü amaçlı içerik için doğrulanmadan bir web kullanıcısına gönderilen dinamik içeriğe dahil edilir. </li>

</ul>

Web tarayıcısına gönderilen kötü amaçlı içerik, genellikle bir JavaScript segmenti biçimini alır,
ancak HTML, Flash veya tarayıcının yürütebileceği diğer herhangi bir kod türünü de içerebilir. XSS’e dayalı saldırıların çeşitliliği neredeyse sınırsızdır, 
ancak bunlar genellikle çerezler veya diğer oturum bilgileri gibi özel verilerin bilgisayar korsanına iletilmesini, 
hedeflenen kişinin bilgisayar korsanı tarafından kontrol edilen web içeriğine yönlendirilmesini veya kullanıcının makinesinde diğer kötü amaçlı işlemlerin gerçekleştirilmesini içerir.

<h2> XSS (Cross-Site Scripting) Saldırılarını Tespit Etme </h2>

XSS güvenlik açıklarını tespit etmenin en kolay yolu, bir güvenlik açığı tarayıcısı kullanmaktır. Bir web sayfasında manuel kod kontrolleri uygulayabilirsiniz. 

<ul>

  <li> Girdinin HTML veya JavaScript ile aynı HTTP yanıtlarında taşınmadığından emin olun. </li>

  <li> Kendi veri tabanınızdan gelen referans değerler olmadığı ve kurcalanmadığından emin olmadığınız sürece tüm verileri aktarım için kodlayın. </li>

  <li> Verilerin belge nesne modeline (DOM) nasıl eklendiği konusunda dikkatli olun. </li>
  
</ul>

<h2> XSS Saldırı Türleri </h2>

XSS’nin üç ana türü vardır: stored, reflected ve DOM tabanlı XSS saldırıları.

<h2> 1. Stored XSS </h2>

Stored XS kalıcı veya Tip-1 XSS olarak da bilinir. Bilgisayar korsanı burada bir payload enjekte eder ve bunu web sitesine veya web uygulaması veri tabanına kaydeder. 
Kötü amaçlı komut dosyası, bir istek sırasında sitenin yasal koduyla birlikte yürütülür.

Blind XSS olarak bilinen stored XSS saldırılarının başka bir alt kategorisi vardır. 
Blind XSS saldırısıyla, bilgisayar korsanı sistemin kendisinin erişemeyeceği bir bölümünü hedefler ve bu nedenle enjeksiyonun başarılı olup olmadığını hemen kontrol edemez. 
Bunun için bir hedef, içeriği daha sonra müşterilere değil bir yöneticiye gösterilen bir iletişim formu olabilir.

<h2> 2. Reflected XSS </h2>

Reflected XSS, kalıcı olmayan veya Tip-2 XSS olarak da bilinir. Reflected XSS saldırılarında, bilgisayar korsanları yükü uygulamada veya web sitesinin altyapısında depolamaz. 
Bunun yerine, özel olarak hazırlanmış bir bağlantıya yanıt olarak sunucudan yansıtılır.

Reflected XSS, web uygulamalarında çok daha yaygındır ve yükün yalnızca bir istekte geçerli olduğu tek seferlik bir siber saldırı olduğu için daha az zararlı olarak kabul edilir.

![XSS-2](https://github.com/oakkaya098/Cyber-Security/assets/152402130/3ca0a266-abbc-489f-a5c5-69755f5dc9e8)


<h2> 3. DOM Tabanlı XSS </h2>

DOM tabanlı bir XSS saldırısı, kullanıcılar bir bilgisayar korsanı tarafından oluşturulan bir bağlantıya tıkladığında gerçekleşir. 
Bilgisayar korsanları daha sonra yükü kötü amaçlı URL bağlantısına yerleştirir. Oradan, yürütüldüğü tarayıcının Belge Nesne Modeli’ne (DOM) iletilir. 
Bunun nedeni, tarayıcının isteği güvenilir bir web sitesinden veya uygulamadan geliyormuş gibi yorumlamasıdır.

<h2> XSS İle Neler Yapılabilir? </h2>

Siteler arası komut dosyası çalıştırma saldırısı gerçekleştiren bilgisayar korsanlarının birden çok hedefi olabilir, ancak hepsinin niyeti kötüdür. Bunlar aşağıdakileri içerebilir:

<ul>

  <li> Oturum kimlikleri gibi verilere erişme </li>

  <li> Hassas bilgileri veya oturum açma kimlik bilgilerini çalmak </li>

  <li> Truva atı saldırısı gerçekleştirme </li>

  <li> Site davranışını manipüle etme ve içeriği değiştirme </li>

  <li> Kötü amaçlı yönlendirmeler </li>

</ul>
