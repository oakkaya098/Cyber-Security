<h1 align=center> Network Access Control (NAC) Nedir? </h1>
NAC (Network Access Control); uç nokta güvenlik teknolojisini, kullanıcı veya sistem yetkilendirmesini ve ağ güvenliği uygulamasının denetlemesini yapan bilgisayar güvenliğine yönelik bir yaklaşımdır. 

<p></p>

Güvenlik ilkelerine uyan ve giriş izni verilmiş kullanıcıların ağa dahil olmasını sağlamaktadır.  

NAC ile ağ güvenliği 4 aşamada sağlanır:

<ul>
  <li> Kimlik Doğrulama </li>

  <li> Yetkilendirme </li>

  <li> Güvenlik Taraması </li>

  <li> İyileştirme </li>
</ul>

Bu özelliklerin hepsini aynı anda sağlamaktadır.

<h2> NAC Neden Önemlidir? </h2>
Günümüz teknoloji dünyasında güvenlik risklerinin artması nedeniyle, ağ güvenliği altyapılarının güçlendirilmesi için gereken denetimi, erişim kontrolünü ve uyumluluk işlevlerini uygulayacak araçlara sahip olunması gerekmektedir.

<p></p>

Ağ Erişim Kontrolü, tam olarak adından da anlaşılacağı gibi, kullanıcıların ve cihazların bir ağda nereye gidebilecekleri ve neler yapabilecekleri konusunda gerekli güvenlik politikalarının uygulanmasını ve ardından ağ ortamına yönelik güvenlik risklerini ortadan kaldırılmasını, önlenmesini ve azaltılmasını hedeflemektedir.

Bilgisayarlar, sunucular, güvenlik duvarları, yönlendiriciler ve ağa eriştikleri yöntem gibi tüm uç noktalara kapsamlı bir NAC çözümü uygulanabilir.

<h2> NAC Nasıl Çalışmaktadır? </h2>
NAC sisteminin son kullanıcı odaklı olmasından dolayı, sistemlerin kontrollerin derinlemesine incelenmesi için bilgisayarlara ajan yüklemesi yapılmaktadır.  

<p></p>

Genel kontrol noktaları; kullanıcının işletim sistemi, kayıtlı olduğu ağ ve NAC ajanının varlığı olmasıdır. Bu üç ön kontrolü geçenler zaten NAC ajanı çalışan bilgisayarlar olduğundan, NAC sisteminde uygulanan önceden yapılandırılmış politikalara göre detaylı kontroller yapılır ve politikayı geçen bilgisayar sorunsuzca ağa dahil olurken, geçemeyenler iyileştirme (remediation) sürecine girmektedirler. 

<h2> NAC Çözümleri'nin Amaçları Nelerdir? </h2>
<ul>
  
  <li> Sıfır gün (Zero- Day) saldırılarının azaltılması </li>

  <li> Ağ bağlantılarının yetkilendirilmesi (Authorization) , doğrulanması (Authentication) ve hesaplanması (Accounting) </li>

  <li> EAP-TLS, EAP-PEAP veya EAP-MSCHAP gibi 802.1X protokollerini kullanarak kablosuz ve kablolu ağa giden trafiğin şifrelenmesi </li>

  <li> Kimlik doğrulama sonrası kullanıcı, cihaz, uygulama veya güvenlik duruşunun rol tabanlı kontrolleri </li>

  <li> Virüsten koruma, yamalar veya ana bilgisayar izinsiz giriş önleme yazılımı olmayan uç istasyonların ağa erişmesini ve diğer bilgisayarları bilgisayar solucanlarının (worms) çapraz bulaşma riskine (risk of cross contamination) sokmasını önlemektir </li>

  <li> Ağ operatörlerinin, ağ alanlarına erişmesine izin verilen bilgisayar türleri veya kullanıcıların rolleri gibi ilkeleri tanımlamasına ve bunları anahtarlarda, yönlendiricilerde ve ağ orta kutularında (middleboxes) zorlamasına olanak tanır </li>

  <li> Geleneksel IP ağlarının IP adresleri açısından erişim ilkelerini zorunlu kıldığı durumlarda, NAC ortamları, dizüstü bilgisayarlar ve masaüstü bilgisayarlar gibi kullanıcı uç istasyonları için, kimliği doğrulanmış kullanıcı kimliklerine dayalı olarak bunu yapmaya çalışır </li>

</ul>

<h2> NAC Kullanım Amaçları Nelerdir? </h2>
<h3> Kurumsal Amaçlar </h3>

<ul>
  
  <li> Kullanım çevresinin gözlenmesi ve araştırılması </li>

  <li> Çalışma koşullarının ( yamalar (patches), güncellemeler (updates) gibi ) güncel olması </li>

  <li> Yetkisiz ve misafir kullanıcıları iç ağdan uzak tutulması  </li>

  <li> Risk koşullarının belirlenmesi </li>

  <li> Her alan (domain) için farklı politikaların geliştirilmesi ve birbirinden bağımsız ağ yapısı oluşturulması </li>

  <li> Risk cihazlarının karantinaya alınması ve ağa karşı oluşacak zararların engellenmesi amaçlanmaktadır </li>
  
</ul>

<h3> İşlevsel Amaçlar </h3>

<ul>
  
  <li> NAC sisteminin hangi alanlarda uygulanacağının belirlenmesi </li>

  <li> Uygulanma sebebinin belirlenmesi </li>

  <li> Uygulanma durumunda elde edilecek kazancın tahmin edilmesi amaçlanmaktadır </li>
  
</ul>

<h3> Teknik Amaçlar </h3>

<ul>

  <li> Yönetim sunucusunun konumlanacağı yerin tespit edilmesi </li>

  <li> Politikaların uygulanacağı sunucuların konumlarına karar verilmesi </li>

  <li> Politikaların belirlenmesi ve uygulanma yöntemlerinin belirlenmesi </li>

  <li> Wlan tanımlamalarına karar verilmesi </li>

  <li> Tanımlı olmayan cihaz ve misafir kullanıcılar, yazıcılar, VOIP cihazların tanımlamalarının yapılması </li>

  <li> Kullanıcıların yetkilerinin belirlenmesi amaçlanmaktadır </li>
  
</ul>

<h3> Uygulama Alanı Belirleme </h3>

<ul>

  <li> Hangi tip cihazlara izin verileceğinin belirlenmesi </li>

  <li> Ağa erişimi olacak kullanıcı profillerinin kararlaştırılması </li>

  <li> Bu profillerinin kullanım kısıtlarının tanımlanması </li>

  <li> Hangi tip erişim metotları kullanılacağının belirlenmesi </li>

  <li> Bağlantı şekillerinin belirlenmesi ( Kablolu, kablosuz) </li>

  <li> Mevcut son kullanıcıya verilen desteklerin belirtilmesi </li>

  <li> Mevcut ağ topolojisinin çıkartılması amaçlanmaktadır </li>
  
</ul>
