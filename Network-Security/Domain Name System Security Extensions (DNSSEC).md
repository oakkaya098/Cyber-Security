<h1 align=center> Domain Name System Security Extensions (DNSSEC) Nedir? </h1>
DNS Sistem Güvenliği Uzantısı (DNSSEC), kullanıcıların sahte Web sitelerine ve amaçlamadıkları adreslere yönlendirilmekten korunmasına yardımcı olarak İnternet'e duyulan güvenin artmasını sağlamak amacıyla ortaya çıkmıştır.

<h2> DNSSEC Birçok Fayda Sağlar </h2>

<ul>
  <li> İnternet kullanıcılarının güvenliğini arttırır. </li>

  <li> DNS üzerinde güvenliği sağlar. DNS'e bir eklentidir. (Eski sürüm DNS hala çalışmaktadır.) </li>

  <li> Gerçeklik doğrulamanın bir yolu olarak çalışır. </li>

  <li> Kimlik doğrulama, diğer güvenlik uygulamalarından (SSH (Secure Shell - Güvenli Kabuk), SSL (Secure Socket Layer - Güvenli Port Katmanı), PGP (Pretty Good Privacy - İyi Gizlilik), vb.) önce uygulanır. </li>

  <li> DNS güvenliğini güçlendiren DNSSEC, e-ticaret, çevrimiçi bankacılık, e-posta, VoIP (Voice Over IP - IP üzerinden Ses) ve çevrimiçi yazılım dağıtımı da dahil olmak üzere birçok İnternet etkinliğine duyulan güveni artırır. </li>

  <li> Kullanıcıların bir kaynağa erişmeye çalışırken farkında olmadan siber suçların kurbanı olması riskini azaltır. </li>

  <li> Yeni güvenli veri işlemi türleri oluşturmak için DNS sistemini kullanma imkanı sağlar. </li>

  <li> İnternet'te gezinirken DNS verilerinin kaynağını doğrulayarak ve doğruluğunu kontrol ederek MITM (Man In the Middle- Ortadaki Adam) saldırılarını ve önbellek zehirlenmesini ele almak üzere tasarlanmıştır. </li>
</ul>

<h2> DNSSEC'in Dezavantajları </h2>

<ul>
  <li> DNS verileri için bir güvenlik sağlayamaz. Hiçbir şifreleme yoktur ve ayrıca DNS'lerdeki veriler topluma açıktır. </li>
  
  <li> DNSSEC, hizmet reddi (denial of service) ve ölü paket (packets of death) gibi DNS sunucusu ataklarını adreslemez. </li>
</ul>

DNSSEC, ortak anahtarlama özelliğini kullanır.

DNSSEC yetkili bölge verilerine, sisteme geldiklerinde dijital imzalama yapar. Böylece DNS'ler internet üzerinde anahtarlı şekilde bir çeşit tasdiklenmiş, onaylanmış olarak yol alır. Bu özelliği DNSSEC'in bir internet sayfasının gerçekte var olup olmadığını da belirlenmesini sağlar. Bilindiği üzere sahte DNS'lere yönlendirilerek kullanıcıların, şirketlerin veya kurumların bilgilerine erişilip zararlar verilmektedir.

DNSSEC'de her bölgenin ortak-özel bir anahtar çifti vardır. Bölgeye ait ortak anahtarlar DNS'le birlikte yayımlanır. Özel anahtarlar gizli tutulur ve çevrimdışı yayımlanması sağlanır. Bu özel anahtarlar yereldeki DNS verilerini işaretleyerek DNS'lerle birlikte yayımlanan dijital imzaları oluştururlar.

DNSSEC güvenlik modeli katıdır ve hiyerarşik olarak üst katmandan alt katmana doğru ilerler. Yüksek katmandaki bölgeler, alt katmanlardaki bölgeleri kontrol eder, alt bölgelerin anahtarlarını imzalar ve onaylar. Bu bölgelerin yetkili sunucuları, kayıt şirketleri, ISS (İnternet Servis Sağlayıcıları), Web barındırma şirketleri veya Web sitesi operatörleri tarafından yönetilebilir.

Son kullanıcı bir Web sitesine erişmek istediğinde, kullanıcının bilgisayarındaki bir saplama çözümleyicisi, tekrarlamalı bir isim sunucusundan Web sitesinin IP adresini sorar. Sunucu bu kaydı istedikten sonra bölgeyle ilgili olan DNSSEC anahtarını da ister. Bu anahtar sayesinde sunucu aldığı IP adresin kaydının, yetkili isim sunucusundaki kayda benzer olduğunu doğrulayabilir.

Tekrarlamalı isim sunucusu, adres kaydının yetkili isim sunucusu tarafından gönderildiğini ve aktarma sırasında değiştirilmediğini belirlerse, etki alanı adını çözer ve kullanıcı siteye ulaşır. Bu sürece doğrulama (authentication) denir. Adres kaydı değiştirilmişse veya belirtilen kaynaktan değilse, tekrarlamalı isim sunucusu kullanıcının sahte adrese ulaşmasına izin vermez. Bu tetkiklerin sonucu olarak, DNS sorguları ve yanıtları MITM (Man in The Middle ) saldırılarından ve kimlik hırsızlığı ve pharming sitelerine yönlendirilen sahtekarlıklardan korunur.
