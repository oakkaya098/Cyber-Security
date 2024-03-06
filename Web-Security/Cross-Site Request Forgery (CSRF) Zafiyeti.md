<h1 align="center"> CSRF (Cross-Site Request Forgery) </h1>

<h2> CSRF Nedir? </h2>

<b> CSRF (Cross Site Request Forgery) </b> herhangi bir web uygulamasında oturum açmış bir kullanıcının oturumunu kullanarak kullanıcının istekleri dışında işlemler yapılmasıdır.

Uygulamaya giden isteklerin hangi kaynaktan ve nasıl gönderildiğinin kontrol edilmeyen sistemlerde bu zafiyet meydana gelir. Saldırganların kullanıcının oturumuna erişebilmeleri için sadece phising saldırılarına gerek yoktur kullanıcının zararlı bağlantıya tıklaması yeterlidir.

Yani günün sonunda saldırgan, son kullanıcının haberi olmadan onun kullandığı uygulamaya farklı işlemler ile müdahale edebilir.

<br>
Aşağıdaki örnek, web sitesi sahiplerine yorum yapmak için kullanılan basit bir HTML formu içermektedir.

![CSRF-1](https://github.com/oakkaya098/Cyber-Security/assets/152402130/d891f125-b9aa-4cc5-8096-fd9f1225c3d8)


Daha sonra blogları görüntüle dediğimizde “deneme2” olarak açtığım bloğun eklenmiş olduğunu görüyoruz.

![CSRF-2](https://github.com/oakkaya098/Cyber-Security/assets/152402130/f710d408-d782-43ba-944b-86f17d61ced7)


Şimdi en basit yöntem ile HTML injection kullanarak sistemdeki CSRF zafiyetini exploit edebiliriz

Bizden blog mesajı istediği girdi alanına yukarıdaki html form kodlarını ekledik ve en aşağı satıra javascript ile bir event yerleştirdik. Eventin görevi fare her konu üzerine geldiğinde kendi kendine başlık3 adında bir blog daha açacak.

![CSRF-3](https://github.com/oakkaya098/Cyber-Security/assets/152402130/ffb572cd-c1ff-4d70-ba71-07a1bcd13977)


Yukarıda görüldüğü üzere italik metin parametresi arasına javascript kodumuzu ekledik.
Bu kısımdaki gerçekleştirilen işlem ise fare her “Zafiyet yaratacak başlığımız burada”  başlığına geldiğinde tıklanmasına gerek kalmadan sistemde form ID değeri f olan formu post isteği ile yollayacak.
Böylelikle sürekli başlık3 adında yeni blog oluşacak.

![CSRF-4](https://github.com/oakkaya098/Cyber-Security/assets/152402130/73f4e4ce-bf72-427c-860b-98ed74e6075b)


Blog başlığı üzerine gelindiğinde aşağıda görüldüğü gibi sisteme post metodu ile isteği yolluyor.

![CSRF-5](https://github.com/oakkaya098/Cyber-Security/assets/152402130/7c3b774d-ad0b-4c25-8dcf-2ce92db27639)


Blogları görüntülediğimizde yine üzerine geldiğimizde aynı şekilde post metodu ile istek yapıyor.

![CSRF-6](https://github.com/oakkaya098/Cyber-Security/assets/152402130/323f5635-5771-413c-bbc6-b9a4d03cbfb2)


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

![CSRF-7](https://github.com/oakkaya098/Cyber-Security/assets/152402130/ae5b836a-e18c-4ae2-81dc-c49ae57f393e)


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

![CSRF-8](https://github.com/oakkaya098/Cyber-Security/assets/152402130/ecff9331-f0b6-4e7a-b361-736e681f4cd7)


Daha önce iki farklı cookie’nin tutulduğunu söylemiştim bu 2 farklı cookie aşağıdaki gibi saklanmaktadır.

![CSRF-9](https://github.com/oakkaya098/Cyber-Security/assets/152402130/a5588469-f22e-4b2e-9d02-685846c521b0)


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

![CSRF-10](https://github.com/oakkaya098/Cyber-Security/assets/152402130/e4f28564-7f4e-422a-ab69-f95129b15b89)


Saldırganlar aşağıda görüldüğü üzere submit adresine gönderilen çerezleri kontrol edebilir ve izleyebilir bir hale geldi.

![CSRF-11](https://github.com/oakkaya098/Cyber-Security/assets/152402130/9081f4ea-d965-4dfd-84c1-b859cc973df0)


Tüm subdomainleri kontrol etmek güvenliği tam olarak sağlamaz çünkü;

<ul>

  <li> Herhangi bir subdomainde bulunan XSS zafiyetinden yararlanılabilir. Örnek vermek gerekirse aşağıdaki payload yardımıyla CSRF zafiyeti tetiklenebilir. </li>

  <li> Çerezler meta tagleri kullanarak oluşturulup kullanılabildiği için meta taglari yardımıyla zafiyet yine tetiklenebilir. </li>
  
</ul>
