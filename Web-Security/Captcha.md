<h1 align=center> Captcha Nedir? </h1>

CAPTCHA (İnsan ve Bilgisayar Ayrımı Amaçlı Tam Otomatik Genel Turing Testi), sorgulama-yanıt doğrulaması olarak bilinen bir güvenlik önlemidir. 
CAPTCHA spam ve şifre çözme koruması sağlanmasına yardımcı olur. 
Bunun için sizden basit bir testi yanıtlamanızı isteyerek şifre korumalı bir hesaba girmeye çalışan bir bilgisayar değil insan olduğunuzu kanıtlamanızı sağlar.

<h2> Güvenilir Olarak CAPTCHA Yapılandırılması </h2>

Form gönderme işlemlerinde otomatize araç kullanımlarının ve  saldırılarının önüne geçilmesi adına CAPTCHA kullanımı genel bir güvenlik önlemi olarak kullanılmaktadır. 
CAPTCHA’ların yanlış yapılandırılması nedeniyle siteler form alanlarında kaba kuvvet saldırıları, SMS ve mail flood saldırıları gibi hizmet kaynaklarının gereksiz kullanılmasına ve bütünlüğün bozulmasına neden olmaktadır.

<h2> Doğru Bir CAPTCHA Nasıl Yapılandırılır? </h2>

Örnek bir giriş formunu ele alırsak işleyiş kabaca şöyledir;

<ul>

  <li> Kullanıcı giriş bilgilerini doldurur, CAPTCHA’yı doldurur ve formu gönderir. Arka planda eğer CAPTCHA doğru çözülmüş ise sonraki kontrol adımına (kullanıcı adı ve parola kontrolü gibi) geçer ve süreç ilerler. </li>

  <li> Eğer CAPTCHA bilgisi yanlış ise tekrar bir CAPTCHA oluşturulup süreç başa döner. </li>
  
</ul>

<h2> Güvenilir Olarak Yapılandırılmayan CAPTCHA </h2>

CAPTCHA kullanımı otomatize işlemlerin yapılmasının engellenmesi, kötü niyetli kişilerin otomatize araç kullanmasını zorlaştırmak amacıyla kullanılmaktadır. 
Güvenilir olarak yapılandırılmayan CAPTCHA kullanımları alınan güvenliği geçersiz kılmaktadır.

<h2> CAPTCHA Değerinin Metinsel İfadeye Çevrilebilmesi </h2>

Bir form alanı geldiği zaman gelen CAPTCHA değeri metinsel ifadeye çevrilip sanki CAPTCHA yokmuş gibi otomatize bir şekilde işlem yapılabilmektedir.

<p></p>

![CD-1](https://github.com/oakkaya098/Cyber-Security/assets/152402130/280b129f-383f-48f6-9344-887af26d6ad3)

Örnek olarak karşımıza gelen bu CAPTCHA değerinin metinsel karşılığını tesseract aracıyla çevirebiliriz.

<p>  </p>

![CG-2](https://github.com/oakkaya098/Cyber-Security/assets/152402130/2edc1bde-3f3a-4b92-9201-27829bbb2d46)

Matematiksel işlemler ile elen CAPTCHA değerlerinde ise aynı şekilde sayıları ve işlem değerini alıp işlem yapılır.

<h2> CAPTCHA Değerinin Ön Tarafta Kontrol Edilmesi </h2>

Forma alanı doldurulurken CAPTCHA değerinin boş bırakıldığı zaman “CAPTCHA değerinin girilmesi gerekmektedir.” tarzında bir hata ile CAPTCHA değerinin boş bırakılması engellenmiştir.

<p>  </p>

![CG-3](https://github.com/oakkaya098/Cyber-Security/assets/152402130/12538832-b4d7-41c9-aee3-9a6df48ed9a7)

Genelde kontrollerin ön yüz tarafında yanlış yapılandırılma sonucu CAPTCHA kontrolü olmaksızın işlem yapılabilir. En sık karşılaşılan yapılandırma hatası HTML kodlarındaki tarafındaki required parametresidir.

(Required = Form elemanının gönderimini zorunlu tutmak için eklenir. İlk olarak kullanıcı tarafında kontrol edilir. Eğer server tarafında kontrol edilmezse işe yaramaz.) 
Bundan dolayı form gönderme işlemi yapılırken doldurulması gerekmektedir. 
Fakat sunucu tarafında gelen CATPCHA değeri doğru kontrol edilmediğinden Proxy ile araya girip CAPTCHA değerini sunucuya göndermediğimiz zaman bir hata ile karşılaşılmamaktadır. 
CAPTCHA değeri kontrol edilmeden işlem gerçekleştirilebilmektedir.

<p></p>

![CG-4](https://github.com/oakkaya098/Cyber-Security/assets/152402130/6e6ff064-1948-43a4-824f-787901567d01)

Bir diğer yöntem olarak Geliştirici seçeneklerini kullanarak form elamanını Disable edilip kontrolden kaçılır.

<h2> CAPTCHA Değerinin Decode Edilmesi </h2>

En çok karşılaşılan diğer yapılandırma hatası basit algoritmalarla CAPTCHA oluşturulmaya çalışılmasıdır. 
CAPTCHA değeri client tarafında (Javascript vb. dilleri kullanarak) oluşturulduğu zaman kötü niyetli kişiler ilgili algoritmayı kullanarak kendileri otomatize araçlara ek olarak decoder vb. şeklinde araçlar yazarak CAPTCHA korumasını bypass edebilir.

Bu durumda CATPCHA değerinin karışık ve güçlü algoritmalar kullanılarak hazırlanması ve bu işlemin server (back-end) tarafında yapılması gerekmektedir. 
Ek olarak CAPTCHA gösterimi sırasında çeşitli yöntemlerle gösterimi zorlaştırarak görüntü işleme vb. araçların kullanılmasını zor, hatta imkânsız hale getirmek gerekmektedir.

<p></p>

![CG-5](https://github.com/oakkaya098/Cyber-Security/assets/152402130/00c3c216-5ba6-49ef-baa5-538665dd54a9)

<br></br>

![CG-6](https://github.com/oakkaya098/Cyber-Security/assets/152402130/e898c439-330d-4a75-a709-5af48d69bbb6)

<h2> Aynı CAPTCHA Değerinin Sorulması </h2>

Kısıtlı bir kümeden gelen sorular ya da belli bir cevabı olan sorunun CAPTCHA olarak gelmesi de kaba kuvvet saldırılarını engelleyememektedir.

<p></p>

![CG-7](https://github.com/oakkaya098/Cyber-Security/assets/152402130/5c20ea45-2e3a-463b-8c7c-941374d8bbbe)

Belirlenen birkaç farklı soru ve birkaç cevap bulunduğundan dolayı dar bir küme içerisinde kontroller sağlanmaktadır.

<h2> CAPTCHA Değerinin Bir Kez Çözülmesi </h2>

CAPTCHA değerinin bir kez girildikten sonra diğer isteklerde CAPTCHA değerinin yenilenmemesinden dolayı bir kere CAPTCHA değerinin doğru girilmesinin ardından kaba kuvvet saldırısı yapılabilmektedir. 
Buradaki temel sorun oturum anahtarımıza bağlı olarak aynı CAPTCHA değerinin kontrol edilmemesinden kaynaklıdır. Her istek sonrası yeni bir CAPTCHA oluşturulmalıdır.

![CG-8](https://github.com/oakkaya098/Cyber-Security/assets/152402130/b5aedb8b-a4c7-4035-980b-3b257dc46f68)

<ul>

  <li> Gelen CAPTCHA değerleri “Hidden input” girdi noktalarında bulunmamalıdır. </li>

  <li> CAPTCHA doğrulama işlemleri backend tarafta gerçekleştirilmelidir. </li>

  <li> CAPTCHA değerinin metin haline çevrilebilecek kadar basit olmamalıdır. </li>

  <li> Gelen CAPTCHA değerleri tekrar kullanılmamalıdır. </li>
  
</ul>
