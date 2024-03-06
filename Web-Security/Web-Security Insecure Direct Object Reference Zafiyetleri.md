<h1 align="center"> IDOR (Insecure Direct Object Reference) </h1>

<h2> IDOR Nedir? </h2>
Insecure Direct Object References (IDOR) zafiyeti bir saldırganın hedef web uygulamasında yetkisiz erişim elde etmesine ve eylemler gerçekleştirmesine olanak tanıyan bir web uygulama zafiyetidir. Sunucu nesnelere (belgeler, dosyalar, veriler vb.) erişmek için gelen HTTP isteklerini doğrulayamadığında IDOR zafiyeti oluşur.

<h3> IDOR Zafiyeti Etkileri : </h3>

IDOR (Insecure Direct Object References) zafiyetinin oldukça büyük etkileri olabilmektedir. Saldırganlar, ele geçirdiği hesabı kontrol edebileceği için hesap üzerindeki tüm bilgileri elde edebilir. Ayrıca IDOR zafiyeti kimlik doğrulanmasının atlatılmasını mümkün kılacağından dolayı, daha yetkili bir hesaba giriş yapılmasını da mümkün kılacaktır. Yetkili hesaba erişim sağlayan saldırgan, sistemde tespit ettiği diğer zafiyet türlerini de aktif ederek zafiyet zincirlemesine sebep olabilmektedir.

<ul style="list-style-type:square;">
  <li> Hesap devralma, çok kritik bilgilere erişim. </li>
  <li> Başka bir kullanıcının verilerini değiştirme/silme, özel/kamuya açık önemli verilere erişim. (Bilet, fatura, ödeme bilgileri vb.) </li>
  <li> Özel verilere erişim/ silme/ değiştirme (Adres, isim vb.) </li>
</ul>


<h2> Örnek Senaryo </h2>

Bir banka uygulaması düşünelim. Bankaya kayıt olduk. Hesabımız açıldı ve internet bankacılığı için bize bir ID değeri verildi.

<b> https://testbank.com/dashboard/user?id=1234 </b> (Bu ID değeri saldırganımızın ID değeri olsun.)

<b> https://testbank.com/dashboard/user?id=1235 </b> (Bu ID değeri kullanıcımızın ID değeri olsun.)

Eğer saldırgan URL’de bulunan kendi ID değerini değiştirip, kurbanın ID değerini yazdıktan sonra kurbanın bilgilerine erişebilirse IDOR zafiyetinden yararlanmış olur.

<h2> Uygulamalı Örnek </h2>

Bir e-ticaret sitesi düşünelim. Ve elimizde iki kullanıcı olsun; kullanıcı-A ve kullanıcı-B.(kullanıcı-A idsi = 14, kullanıcı-B idsi= 18) 

Kullanıcı-A bir sipariş versin. Ve adres bilgilerinin databaseden  “user_id” verisi ile alındığını varsayalım. 

Eğer IDOR varsa sipariş sırasında user_id = 14 iken 18 yaparsam kullanıcı-B nin adres bilgilerini siparişe ekleneceğini beklerim.

<br>

Daha iyi anlaşılması için portswiggerın IDOR labına bakalım,
<br>


![IDOR-1](https://github.com/oakkaya098/Web-Security/assets/152402130/5766c480-b0a4-474c-8d6d-2cf64cd1fd12)

Live chat opsiyonuna baktığımızda Hal adında birisi ile konuşabiliyoruz. View transcript seçeneği ise yaptığımız konuşmaları download etmemize olanak sağlıyor. Bu isteği burp suite ile yakalıyoruz.

![IDOR-2](https://github.com/oakkaya098/Web-Security/assets/152402130/d5840707-1a3f-4e9c-a329-6dacc6886f67)

Bakıyoruz ki view transcript bir get komutu çalıştırıp “4.txt” adında bir dosyayı indiriyor. Yani “1/2/3.txt” gibi dosyalar olarabilir. “4.txt” yerine “1/2/3.txt” gibi dosyaları deneyelim. 

![IDOR-3](https://github.com/oakkaya098/Web-Security/assets/152402130/197aa3e7-4240-4248-ae22-55707becc72b)

“1.txt” denediğimizde indirdi ve başka bir kullanıcının mesaj içeriğine ulaştık. Ve başka bir kullanıcının şifre bilgisini öğrendik. 

![IDOR-4](https://github.com/oakkaya098/Web-Security/assets/152402130/a97a2da8-66d8-4504-bb3d-f2bd2b6c0ebb)

User name : carlos

Password : 1gi9*******
<br>
<br>

‘User name’ bilgisi laba giriş yaparken veriliyor.

![IDOR-5](https://github.com/oakkaya098/Web-Security/assets/152402130/59817303-6af8-49fd-a081-ec1501a34167)




<h2> Çözüm Önerileri: IDOR Zafiyeti Nasıl Önlenir? </h2>

IDOR güvenlik açığını kapatmak veya etkisini azaltmak için erişim kontrolleri sıkıştırılmalıdır. Web uygulama altyapısı geliştirilirken kullanılan framework’ler güncel ve tanınmış olmalıdır. Böylelikle ortaya çıkan IDOR zafiyetlerinin düzeltilmesi durumunda hızlı aksiyon almak mümkün olacaktır. IDOR zafiyetinin önüne geçilmesinde en etken rol oynayan yöntem budur.

<ul style="list-style-type:square;">
  <li> Geliştiriciler, anahtarlar veya dosya adları gibi özel nesne referanslarını görüntülemekten kaçınmalıdır. </li>
  <li> Parametrelerin doğrulanması düzgün bir şekilde uygulanmalıdır. </li>
  <li> Başvurulan tüm nesnelerin doğrulanması yapılmalıdır. </li>
  <li> Belirteçler, yalnızca kullanıcıyla eşleştirilecek ve herkese açık olmayacak şekilde oluşturulmalıdır. </li>
</ul>
