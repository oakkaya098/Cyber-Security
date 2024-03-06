<h1 align="center"> CSRF (Cross-Site Request Forgery) </h1>

<h2> CSRF Nedir? </h2>

<b> CSRF (Cross Site Request Forgery) </b> herhangi bir web uygulamasında oturum açmış bir kullanıcının oturumunu kullanarak kullanıcının istekleri dışında işlemler yapılmasıdır.

Uygulamaya giden isteklerin hangi kaynaktan ve nasıl gönderildiğinin kontrol edilmeyen sistemlerde bu zafiyet meydana gelir. Saldırganların kullanıcının oturumuna erişebilmeleri için sadece phising saldırılarına gerek yoktur kullanıcının zararlı bağlantıya tıklaması yeterlidir.

Yani günün sonunda saldırgan, son kullanıcının haberi olmadan onun kullandığı uygulamaya farklı işlemler ile müdahale edebilir.

<br>
Aşağıdaki örnek, web sitesi sahiplerine yorum yapmak için kullanılan basit bir HTML formu içermektedir.

![CSRF-1](https://github.com/oakkaya098/Cyber-Security/assets/152402130/d891f125-b9aa-4cc5-8096-fd9f1225c3d8)


Daha sonra blogları görüntüle dediğimizde “deneme2” olarak açtığım bloğun eklenmiş olduğunu görüyoruz.

![CSRF-2](https://github.com/oakkaya098/Web-Security/assets/152402130/dd4e532a-a894-4a63-87ce-5c9bb8370f95)

Şimdi en basit yöntem ile HTML injection kullanarak sistemdeki CSRF zafiyetini exploit edebiliriz

Bizden blog mesajı istediği girdi alanına yukarıdaki html form kodlarını ekledik ve en aşağı satıra javascript ile bir event yerleştirdik. Eventin görevi fare her konu üzerine geldiğinde kendi kendine başlık3 adında bir blog daha açacak.

![CSRF-3](https://github.com/oakkaya098/Web-Security/assets/152402130/250a06c4-207a-4482-82a0-2f7138961834)

Yukarıda görüldüğü üzere italik metin parametresi arasına javascript kodumuzu ekledik.
Bu kısımdaki gerçekleştirilen işlem ise fare her “Zafiyet yaratacak başlığımız burada”  başlığına geldiğinde tıklanmasına gerek kalmadan sistemde form ID değeri f olan formu post isteği ile yollayacak.
Böylelikle sürekli başlık3 adında yeni blog oluşacak.

![CSRF-4](https://github.com/oakkaya098/Web-Security/assets/152402130/e3fedec2-da8d-4cc4-9b3b-887d4885356c)

Blog başlığı üzerine gelindiğinde aşağıda görüldüğü gibi sisteme post metodu ile isteği yolluyor.

![CSRF-5](https://github.com/oakkaya098/Web-Security/assets/152402130/0fbb05f6-1f0b-4ae3-8113-ae4c2ed47f21)

Blogları görüntülediğimizde yine üzerine geldiğimizde aynı şekilde post metodu ile istek yapıyor.

![CSRF-6](https://github.com/oakkaya098/Web-Security/assets/152402130/cb0d75b3-e3ba-49a2-bcd5-b670a99560de)

Burada token güvenliğinin sağlanmamasından, girdi alanının kontrol edilmemesinden kaynaklı CSRF zafiyetini istismar edebilir hale geliyoruz.  
Mağdurlar bloğu ziyaret etmek istediğinde blog eklemek yerine oturumlarını çalabilecek daha tehlikeli kodlar çalıştırılabilir.

<h2> CSRF Zafiyetinin Önlenmesi </h2>

<b> CSRF </b> zafiyetinin hem kullanıcı hem sistem tarafında alınabileceği önlemleri vardır.

<h2> Kullanıcı Tarafındaki Önlemler </h2>

<ul style="list-style-type=square">

  <li> En önemli ve sürekli ifade edilen önlemlerden bir tanesi olan kaynağın güvenliği doğrulanmamış bağlantılara tıklamamak gerekmektedir. 
    Kimden geldiğinden emin olamadığınız maillerdeki bağlantılara tıklamayınız. </li>

  <li> Bağlantıları zararlı analiz platformlarında taratarak ve domaini kontrol ederek giriş sağlayınız. </li>

  <li> Ön belleğe verileri düzenli olarak temizleyiniz. (çerez, site verileri) </li>
  
</ul>

<h2> Sistem Tarafındaki Önlemler </h2>

<ul>

  <li> Kullanıcıların gerçekleştirdiği talepler POST metodu ile alınmalıdır. </li>

  <li> Kullanıcıya özel olarak üretilmiş tokenler ile CSRF in önüne geçilmiş olur. 
    Bu token her işlemde tekrar üretilir ve formda saklanır böylelikle saldırganın bu tokeni tahmin etmesi imkansız hale gelir. 
    Bu kısımda önemli olan şey ise token üretirken doğru bir patern ve güvenilir kriptografi yöntemleri kullanılmasıdır. Birden fazla token yöntemi oluşturma yöntemi vardır. </li>
</ul>

<h2> CSRF Token Nedir? </h2>

İlk olarak ifade etmek gerekirse CSRF zafiyetinin önlenmesi açısından en önemli ve popüler yöntemdir.  
CSRF Token yöntemi temelde benzersiz ve gizli bir değer alarak formlara gömülen ve bu sayede kullanıcının başarıyla oturum açma işleminden sonra oluşturulan değerdir. 
Bu değer patern yöntemlerine göre farklı şekillerde saklanabilir. Aşağıda bununla ilgili örnek eklenmiştir.

![CSRF-7](https://github.com/oakkaya098/Web-Security/assets/152402130/fed69cd9-5c9f-4fe6-a4c5-a57e550c6d21)

<h1> Token Patern Yöntemleri <br> <br>
1.CSRF Synchronizer Token Pattern Yöntemi
</h1>

Her istek için gizli ve benzersiz değer yani token tüm formlara gömülür ve sunucu tarafında işlem yapılır. Genel olarak kullanılan token yöntemidir. 
Bir giriş formunda post isteği ile kimlik bilgileri gönderilir, kullanıcı başarıyla oturum açarsa benzersiz bir oturum kimliği ve token oluşturulur. 
Oluşturulan token istemci tarafında çerezlerde saklanır, aynı zamanda sunucu tarafında da tutulur.

<h2> Özellikleri </h2>

<ul>

  <li> Her oturum için özel ve benzersizdir. </li>

  <li> Yüksek karakter sayısı ile rastgele değer alarak tahmin edilerek bypass edilmesinin önüne geçilir. </li>

  <li> Doğrulama işleminde başarısız olunduğunda işlem reddedilir. </li>
  
</ul>

<h2> 2.Double Submit Cookie Pattern Yöntemi </h2>

<b> Çift Çerez Gönderme Yöntemi </b> hem çerezde hemde istek parametresinde rastgele bir değer gönderme olarak tanımlanabilir. 
Kullanıcıların oturum açma talebi sistemde doğrulandığında sistem istemci tarafında oturum ID si oluşturur ve çerezlere kaydeder. 
Bunun yanında token oluşturur ve kullanıcının makinesinde ayrı bir çerez olarak saklar. Sunucunun bu çerezi kaydetmesi gerekmez. Çerezler httponly olarak etiketlenemez.

Bu çerez, istemcilerin buna erişmesi gerektiği için HttpOnly olarak ayarlanamaz, sunucu bu oturum için oluşturulan belirteç kaydına sahip değildir.

Ardından kullanıcı güvenli bir form gönderdiğinde bu token girdi alanlarına gömülür.

Sunucu, form parametresi olarak gönderilen tokeni, çerez değerine bakarak doğrular ve tamamlanacak işlemi yetkilendirir. Çapraz kökenli bir saldırgan, aynı kökenden gelen ilkeye göre sunucudan gönderilen verileri okuyamaz veya çerez değerlerini değiştiremez.

Aşağıda Double Submit Cookie Pattern Yönteminin çalışma mantığı ile ilgili şema eklenmiştir.

![CSRF-8](https://github.com/oakkaya098/Web-Security/assets/152402130/45682c97-9374-4045-a1d6-aa29c74ff2de)

Daha önce iki farklı cookie’nin tutulduğunu söylemiştim bu 2 farklı cookie aşağıdaki gibi saklanmaktadır.

![CSRF-9](https://github.com/oakkaya098/Web-Security/assets/152402130/4cf50f7c-364a-49e8-87c9-137229228656)

<h2> İki Pattern Yönteminin Karşılaştırılması </h2>

İki yöntemde de tasarım ve güvenlik sorunları mevcuttur. Two Cookie pattern yöntemi  Synchronizer Token Pattern  yönteminden daha hafif ve kullanışlıdır.

<h2> Double Submit Cookie Pattern Yönteminin Bypass Edilmesi </h2>

Bu yöntemin ne olduğunu yukarda anlatmıştık. Şimdi ise bu yöntemin nasıl bypass edilebileceğine değinelim.

<h2> Çerez Tespiti </h2>

Eğer saldırgan CSRF çerezlerini ayarlayabilirse bypass işlemini gerçekleştirebilir. Çerez tespitinin birden fazla yolu vardır bunlar;

<ul>

  <li> Subdomainleri exploit etme. </li>

  <li> Ortadaki adam saldırısı ile HTTP bağlantıların takibi </li>
  
</ul>

<h2> Subdomainleri Exploit Etme </h2>

İlk atak vektörümüz kötü amaçlarla subdomainlerin kullanılmasıdır. Örneğin example.com domaininin bir subdomainini saldırganların ele geçirdiğini varsayalım. Bu durumda saldırganlar aslında ana domain için çerezleri ayarlayabilir ve bu durumda sunucu tarafında “set cookie” değerini yanıtlayabilir ve kabul edebilirler.

Bu çerezlerin yanıtlanması için belli bir sayfa kullanılır aşağıda görüldüğü üzere submit sayfası ile işlem yapıyor.

![CSRF-10](https://github.com/oakkaya098/Web-Security/assets/152402130/9cf4b06f-7534-4a2d-92ad-fc80e387aa2b)

Saldırganlar aşağıda görüldüğü üzere submit adresine gönderilen çerezleri kontrol edebilir ve izleyebilir bir hale geldi.

![CSRF-11](https://github.com/oakkaya098/Web-Security/assets/152402130/4daf85ea-2062-461c-ac20-292e30771a9e)

Tüm subdomainleri kontrol etmek güvenliği tam olarak sağlamaz çünkü;

<ul>

  <li> Herhangi bir subdomainde bulunan XSS zafiyetinden yararlanılabilir. Örnek vermek gerekirse aşağıdaki payload yardımıyla CSRF zafiyeti tetiklenebilir. </li>

  <li> Çerezler meta tagleri kullanarak oluşturulup kullanılabildiği için meta taglari yardımıyla zafiyet yine tetiklenebilir. </li>
  
</ul>
