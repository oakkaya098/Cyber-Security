<h1 align=center> Modern Web Nasıl Çalışır? </h1>

<ul>

  <li> Örneğin; Bilgisayar ilk açıldığında DHCP protokolü 192.168.1.0 üzerinden broadcast yapar. IP verilecek bilgisayara IP'yi DHCP protokolü verir. </li>

<p></p>

![1](https://github.com/oakkaya098/Cyber-Security/assets/152402130/7ed5f326-21fd-42bc-b5ee-494146243675)


  

  <li> Bilgisayarlar birbiriyle haberleşmek için MAC adreslerini öğrenir. Bunun için Layer 2’de ARP protokolünü kullanırlar ve OS ARP Table oluşturulur. <br>

![arp-table](https://github.com/oakkaya098/Cyber-Security/assets/152402130/3cde0407-8ecd-4922-841b-044ceea680dd)

  
  <ul> <b> OS ARP Table Nedir : </b>
      <li> Her sistemde, komşu cihazlara ait IP adreslerinin, o cihazların MAC adresine dönüşüm tabloları bulunmaktadır. Bu tablolara ARP Tablosu adı verilmektedir. </li>
  </ul>
  
  </li>

  <li> Bilgisayarı açtığımızda DNS’i ve Gateway’i manuel olarak girmeyiz. Bunları DHCP sağlar. </li>

  <li> Bir IP adresinin LAN içinde olduğunu anlaması Subnet Mask sayesinde oluyor. 255.255.255.0. Bilgisayar konuşmak istediği IP ile Subnet Mask IP’nin bit karşılıklarını yazar, ikilik sayı sistemi ile işleme sokar ve çıkan sonuca göre karar verir. </li>

<p></p>

![2](https://github.com/oakkaya098/Cyber-Security/assets/152402130/9b65baf3-bd72-4d0b-82a9-f989a56b7ce4)



  <p></p>

  <li> Örneğin x.com ‘a gitmek istediğinde, önce bilgisayar “Host” dosyasına bakar. /etc/hosts burada bulamayınca DNS’e sorar: <br>
    <ul> 
      <li> Host dosyası, işletim sistemleri içerisinde bulunan ve metin düzenleme programları ile açılan ve gerektiğinde düzenlemeler yapılabilen bir metin dosyasıdır. Web site adreslerini sunucu ip adresleri ile eşleştirmek için kullanılır. </li>
      <li> DNS’e (8.8.8.8 - Resolver DNS) UDP protokolüyle 53 numaralı porta x.com'un IP adresini sorar. </li>

  </li>

  <li> Resolver DNS bilmiyor ise, Root DNS’e gider sorar. Root DNS'de x.com'un IP adresini bilmiyor ise Top Level Domain’e yönlendirir(TLD *.com/.net/.org). </li>

  <li> TLD de x.com’un kayıtlarını tutan DNS'e, Authoritative DNS (Yetkili DNS)'e yönlendirir.
  <br>

  </li>

  
</ul>

<h2> Riskler Nelerdir? </h2>

Başka biri 8.8.8.8’e gittiğinde bütün süreç tekrar yaşanmayacak çünkü TTL’lere göre Cache’de tutma mekanizması vardır.

<ul>

  <li> Bu Cache poison edilebilirse x.com’a gidecek HTTP paketleri istediğimiz gibi yönlendirilebilir. </li>

  <li> Authoritative DNS sunucusu ele geçirilirse, MX kayıtları değiştirilebilir ve bütün e-postaları üstümüze alabilir, Cname ağ recordları'nı değiştirebilir, tüm kayıtları üstümüze alabiliriz. .txt kayıtlarını değiştirirsek sertifika issue ortaya çıkar. </li>

  <li> TLD saldırıları, tüm *.com cevaplarını yanlış döndürebilir. </li>
  
</ul>

<h2> 3-Way Handshake </h2>

<ul> <b>Bir ana bilgisayarın, istemci ve sunucu arasındaki bağlantıyı oluşturmak için kullanılan bir yöntemdir. Bağlantı kurmak için önce oturum açma işlemleri gerçekleşir ve her TCP protokolü oturum açma ile başlamak zorundadır.</b>
<p></p>

  <li> İstemci sunucuya IP adresi üzerinden SYN paketi gönderir. Bu paketin amacı, sunucuya yeni bir bağlantı talebinde bulunur. </li>

  <li> SYN mesajını alan sunucu ise bağlantıları başlatabilmek için bağlantı noktalarına sahip olmalıdır. Sunucu kendisine gelen bu isteği SYN-ACK paketi ile onaylar. </li>

  <li> İstemci her şeyin yolunda olduğunu ACK paketi ile cevaplayarak bağlantının başlamasını sağlar. </li>
  
</ul>



<p></p>


![3](https://github.com/oakkaya098/Cyber-Security/assets/152402130/628ee487-8bc2-413b-a54f-8ee254983fad)


<p></p>



<h2> Sunucular Bölgesi (DMZ) </h2>

<ul> <li> En basit tanımı ile fiziksel ya da mantıksal olarak sadece dış dünya ile irtibatta olan sunucuların iç ağlarınızdan ayrılıp farklı bir ağda konumlandırılmasıdır </li> </ul>

80 yada 443 numaralı portlara gidildiğinde aslında Firewall'a gideriz. Peki bu Firewall nedir?

<ul>

  <li> <b> Firewall : </b> Zararlı yazılımlara karşı bir duvar örer ve bunların ağ yolu ile bilgisayara sızmasının önüne geçer. </li>

  <li> <b> TCP SYN Attack : </b> TCP paketinin içine farklı bir IP adresi yazılır ve web sunucusuna yollanır. Web sunucusu da farklı bir IP ile iletişime geçmeye çalışır ve kaynaklarını tüketir. Bu saldırı tipine <b> TCP SYN Attack (SYN FLOAD) </b> denir. </li>
  
</ul>

<h2> Virtual Hosting (VHOST) </h2>

<ul> <li> Virtual Hosting, bir ana sunucunun kaynaklarını belli oranda sınırlandırıp, bölümlere ayrılarak kullanıcılara kiralanmasıdır. </li> </ul>

Domain sayısı, IP sayısını geçtiği için böyle bir teknoloji çıkmıştır.

Host firmasının konfigürasyonuna göre hangi siteye gidiliyor ise /var/www/... sitesine yönlendirir.

<p></p>

![4](https://github.com/oakkaya098/Cyber-Security/assets/152402130/854cfefd-ec47-4e57-9403-ce6a97625827)


<p></p>

Bunun bir e-ticaret sitesi olduğunu düşünelim. Çok satış yaptığı dönemlerde bu sunucu yetmeyebilir. Eskiden RAM eklenirdi fakat günümüzde ise bir tane daha web sunucusu kurulabilir. Kaynak kodlarının hepsi eklenir ve DataBase'ler kurulur. Bu sistemi kurmak için ReverseProxy (LoadBalancer)'a ihtiyaç vardır.

<ul> <li> Reverse Proxy, internete erişim için kullanılma amacına sahip ara sunucular olarak tanımlanır. Daha basit ve anlaşılır bir tanımla; bir web sitesine giriş için tarayıcı proxy ile bağlantı kurar. Proxy, bu aşamadan sonra sayfaya bağlanır ve içeriği tarayıcıya iletir. Reverse Proxy’nin amacı ağ trafiğinin düzgün akışını sağlamaktır. </li> </ul>

<p></p>

![5](https://github.com/oakkaya098/Cyber-Security/assets/152402130/efee5b3f-dc4e-454a-9d1b-76827f39caf9)


Burada bazı sorunlar çıkmaya başlıyor.

<ul>

  <li> Eğer session diskte tutuluyorsa bu kullanıcının tüm requestler'de aynı yere gelmesi gerekir. Çünkü session ilk sunucuda bulunuyor, diğer sunucularda bunun bilgisi yok. Eğerki ilk sunucu çöker ise kullanıcı log-out olur. </li>

  <li> <b> DataBaseler'den biri düşerse ne olacak? : </b> Birden fazla DataBase olur ise SQL Proxy servisine ihtiyaç vardır. Tüm SQL sorguları SQL Proxy'e sorulur ve SQL Proxy hangi DataBase uygun ise ona sorar. Günümüzde "MicroService" yapıları buradan ortaya çıkmaktadır. </li>  

  <li> <b> Statik Dosyalar : </b> Sunucuya bir dosya yüklendiğinde sadece bir tanesinde tutuluyormuş gibi olur. Bunun olmaması için CDN (Content Delivery Network) gereklidir. </li>

</ul>

Bütün web uygulamalarında statik dosyalarda aynı içerik olması için CDN (Content Delivery Network) gereklidir. Tüm kullanıcılar bir resmin yüklenmesi için CDN sunucusuna istek atmaması için, CloudFlare gibi programlar ile bir dosyanın veya HTTP response'un kolaylıkla dönebilmesi (Resmin cache'i döner) sağlanır. Mesela bir resmin yüklenmesi için farklı ülkelerdeki kullanıcılara teker teker sunucu isteği atılıp gönderilmez. Bunun yerine CloudFlare üzerinden (Arada Firewall ve ReverseProxy olur) otomatik gönderilir. Bütün trafik CloudFlare üzerinden geçer.

<p></p>

![6](https://github.com/oakkaya098/Cyber-Security/assets/152402130/ef208289-ba79-4603-a789-323bd892d76f)


<p></p>

Full text searchler'in DataBase'ler üzerinden yapılması sonucu ortaya çıkan maaliyetleri engellemek için <b> Elastic Search </b> kullanılır.

<ul>

  <li> <b> Elastic Search </b> ElasticSearch, BigData yani büyük veriler ile çalışan şirketlerin, içerik arama, veri analizi, sorgulamalar ve öneriler gibi işlemlerde özellikle performans kabiliyetleri, güçlü ve esnek olmasından dolayı tercih ettiği bir search engine’dir. </li>
  
</ul>

Sunucuya gelen bütün HTTP isteklerinin "Loging"'ini tutan sunucular bulunur.

Bu sunucunun da aynısının yedeğinin bulunduğu bir sunucu daha olur. <b> (DRC) </b>

<ul>

  <li> Sistemin çalıştığı data center çalışmayı durdurur ise, tüm trafik hiçbir kesinti yaşanmadan <b> DRC </b> hizmet verir. </li>

</ul>
