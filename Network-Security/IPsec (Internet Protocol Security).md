<h1 align=center> IPsec (Internet Protocol Security) Nedir </h1>
Genellikle IPsec olarak adlandırılan Internet Protocol Security, internet üzerinde güvenli iletişim sağlayan protokol ve algoritmalardan oluşan bir çerçevedir. 
Bu, IP katmanında uçtan uca güvenlik sağlayarak veri trafiğini koruyarak elde edilir. 
IPsec, iletilen verilerin hem bütünlüğünün hem de gizliliğinin korunmasını sağlamak için şifreleme ve dijital imzalamadan yararlanır. 
Genellikle Sanal Özel Ağlarda (VPN’ler) iki nokta arasındaki tüm trafiği güvence altına almak için kullanılır.

<h2> IPsec Neden Önemlidir? </h2>
Siber tehditlerin yaygın olduğu bir dünyada, IPsec verilerin korunmasında çok önemli bir rol oynamaktadır. 
Çünkü IP protokolünün kendisi doğal güvenlik önlemlerine sahip değildir. Bu nedenle IPsec, güvenli IP iletişimi için bir çerçeve sunarak boşluğu doldurur. 
IPsec’in uygulanması, hassas bilgileri yetkisiz erişim veya değişikliklerden korumak için gereklidir.
Ayrıca IPsec, genel ağlar üzerinden güvenli uzaktan erişim ve siteden siteye iletişim sağlayarak uzak çalışanları olan işletmeler, 
birden fazla ofis konumu veya çevrimiçi etkileşimlerinde gizliliğe ihtiyaç duyan bireyler için önemli bir araç haline getirir. 
Ayrıca sanal özel ağlar (VPN’ler) arasında ve farklı ağ cihazları arasında güvenli iletişimi kolaylaştırır.

<h2> IPsec Nasıl Çalışır? </h2>
IPsec süreci, bir kullanıcı bir ağ üzerinden veri gönderdiğinde başlar. 
Veriler daha sonra IPsec şifrelemesi kullanılarak yalnızca alıcının cihazı tarafından okunabilecek bir biçime dönüştürülür ve böylece bilgilerin iletim sırasında gizli ve güvenli kalması sağlanır.
IPsec iki temel protokol aracılığıyla çalışır: Encapsulation Security Payload (ESP) ve Authentication Header (AH). 
ESP gizlilik, veri kaynağı kimlik doğrulaması, bağlantısız bütünlük, tekrarlama önleme hizmeti ve sınırlı trafik akışı gizliliği sağlar. 
Öte yandan AH, verilerin gerçekliğini ve bütünlüğünü sağlayarak IP iletişimlerine ek bir güvenlik katmanı sağlar.

<h2> IPsec Protokolleri Nelerdir? </h2>
IPsec’in tek bir protokol değil, bir protokoller paketidir. Protokol, ağda, verileri biçimlendirmek ve ağ iletimi için bilgi hazırlamak için kullanılır.
Bazı IPsec protokolleri aşağıdaki şekildedir:

<ul> <li> <b> Authentication Header (AH) :  </b> AH protokolü, veri paketlerinin güvenilir bir kaynaktan gelip gelmediğini veya tahrif edilip edilmediğini doğrulamak için kullanılır. 
Başka bir deyişle, veri kaynağı kimlik doğrulaması, veri bütünlüğü ve yeniden oynatma koruması sağlar. </li> </ul>

<ul> <li> <b> Encapsulating Security Payload (ESP) :  </b> Güvenlik yükünü kapsülleme, Sanal Özel Ağ (VPN) kullanan bilgisayarlar arasındaki veri paketlerini şifrelemek ve kimliklerini doğrulamak için kullanılır. 
Her paket için IP başlığını ve yükünü şifreler ve her veri paketine kendi başlığını ve bir fragman ekler. </li> </ul>

<ul> <li> <b> Internet Key Exchange (IKE) :  </b> Internet key exchange (IKE), iki cihaz arasında güvenli, kimliği doğrulanmış bir iletişim kanalı kurmak için kullanılan güvenli bir anahtar yönetimi protokolüdür.
Her iki cihaz da şifreleme anahtarlarını ve algoritmalarını müzakere etmek için kullanılan bir dizi protokolü ifade eden güvenlik ilişkisi (SA) kurar ve İnternet anahtar değişimi en yaygın SA protokollerinden biridir. </li> </ul>

<h2> IPsec Modları Nelerdir? </h2>
IPsec farklı koruma derecelerine sahip iki farklı modda çalışır:

<ul> <li> <b> Tünel modu :  </b> Bu mod, verileri şifreleme yoluyla yetkisiz taraflardan korumak için genel ağlarda veri aktarımı için uygulanabilir. 
İki ağ geçidi ana bilgisayarı arasında bir IPsec tüneli kurulur, ancak tünelin kendisi korunan ağdaki herhangi bir ana bilgisayardan gelen trafiği taşır. </li> </ul>

<ul> <li> <b> Aktarım modu :  </b> Tünel modundan farklı olarak, aktarım modu yalnızca veri paketinin yükünü şifrelerken IP başlığı orijinal haliyle kalır. 
Şifrelenmemiş kısım, yönlendiricinin her veri paketinin hedef adresini tanımlamasına olanak tanır. 
Bu nedenle, bir ana bilgisayarın başka bir ana bilgisayarla etkileşime girmesi gerektiğinde taşıma modu daha iyi bir seçim olabilir. </li> </ul>

<h2> IPsec Şifreleme Nedir? </h2>
IPsec şifreleme, her paketi şifreleyerek ve kimlik doğrulaması yaparak verileri korur. 
Şifreleme anahtarları verileri kodlamak için kullanılırken, şifre çözme anahtarları orijinal verileri geri yüklemek için kullanılır.
IPsec bunu başarmak için hem simetrik hem de asimetrik şifreleme tekniklerini kullanır. 
Simetrik şifreleme, verileri şifrelemek ve şifresini çözmek için aynı anahtarı kullanırken, asimetrik şifreleme bir çift anahtar kullanır: genel ve özel anahtarlar. 
Genel anahtar herkesle paylaşılabilir, ancak sahibi özel anahtarı gizli tutar. IPsec, veri yükü için simetrik şifreleme ve anahtar değişimi için asimetrik şifreleme kullanır.
