<h1 align="center"> SQL İnjection Zafiyetleri </h1>

<h2> SQL Nedir? </h2>

SQL (Structured Query Language), Yapılandırılmış Sorgu Dili anlamına gelir. Bu dil temel olarak ilişkisel veritabanı ile etkileşim için geliştirilmiştir. 
<b>Gerekli verilere erişme, veri ekleme, veritabanını değiştirme</b> veya sorgu amacıyla kullanılan SQL; Microsoft SQL Server, Oracle, IBM DB2 ve MySQL gibi ilişkisel veritabanları için komut ve kontrol dilidir.

<h2> SQL İnjection Nedir? </h2>

SQL Injection ya da SQLi denen siber saldırı türü, web sayfası ve web uygulaması güvenlik önlemlerini atlamayı mümkün kılan bir korsanlık tekniğidir. 
Bu saldırı tekniğini kullanarak, saldırgan bir SQL veritabanının içeriğini ele geçirebilir, değiştirebilir ve silebilir.

<h2> SQL İnjection Türleri </h2>

En popüler saldırı türü olan bant içi (In-band) SQL injectionları aynı iletişim kanalını kullanır ve iki şekilde gerçekleşir:
<ul style="list-style-type=square;">

<li> <b> Hata tabanlı (Error-based) : </b> Hata tabanlı SQL injection tekniği, uygulama veritabanı sunucuları tarafından atılan hata mesajlarına dayanır.
  Saldırganlar, hangi sorguların hata mesajları aldığını test ederek, veritabanı yapısına dayalı olarak hedeflenen SQL injectionları oluşturabilir. </li>
  
<li> <b> Union-based : </b> Bir uygulama SQL enjeksiyonuna karşı savunmasız olduğunda ve uygulamanın yanıtları bir sorgu için sonuçları döndürdüğünde, saldırganlar uygulama veritabanının tablolarından veri almak için UNION anahtar sözcüğünü kullanır. </li>
  
</ul>

<b>Inferential (Çıkarımsal)</b> SQL injectionu, Blind SQL injection saldırısı olarak da bilinir. Bu saldırıda, bir veri yükü gönderdikten sonra, saldırgan veritabanının veri yapısını belirlemek için davranışı ve yanıtları gözlemler. İki türde görülür:

<ul>
  
  <li> <b> Boole tabanlı : </b> Saldırganlar, uygulamayı DOĞRU veya YANLIŞ’ın farklı sonuçlarını döndürmeye zorlayan SQL sorguları göndererek, belirli yüklerin meşru sonuçlar döndürüp döndürmediğini anlayabilir. </li>

  <li> <b> Time-based : </b> Zamana dayalı olarak adlandırabileceğimiz bu yöntem, veritabanından yanıt vermeden önce belirli süre beklemesini isteyen SQL sorguları gönderir.
    Zamana dayalı SQL injection saldırısı, genellikle bir uygulama genel hata mesajları verdiğinde kullanılır. Bu teknik, veritabanını belirli bir süre beklemeye zorlar.
    Yanıt süresi, saldırganın sorguyu DOĞRU veya YANLIŞ olarak belirlemesine yardımcı olur. </li>
</ul>

Her iki durumda da, saldırganların verileri karakter karakter numaralandırması gerektiği düşünüldüğünde, Inferential SQL enjeksiyon saldırı yöntemleri oldukça zorludur.

<b> Out-of-band (Bant Dışı) </b> SQL injection saldırıları en az kullanılan SQL injection tekniğidir. Bant dışı SQL injection saldırısı, uygulamanın verileri herhangi bir protokol (HTTP, DNS veya SMB) aracılığıyla iletmesini ister.

<h2> SQL İnjection Nasıl Tespit Edilir? </h2>

SQL injection güvenlik açıklarını tespit etmek için uygulamanıza veya web sitenize saldırılar başlatmanız önerilir.
Bu açıkları bulmak için manuel test ve otomatik test olmak üzere iki teknik kullanılır.
Manuel testte, uygulama geliştirme sırasında, SQL injectionu güvenlik açığının tespit edilmesine yardımcı olan bir dizi test söz konusudur.

Otomatik test için SQLMap gibi çeşitli araçlar bulunmaktadır. Genellikle bu araçlar, kullanımda olan veritabanı türünü belirlemek için sitenizi inceler ve sorgular oluşturur. 
Keşfedilen bazı güvenlik açıklarının kaldırılmasına yardımcı olabilecek hata düzeltme özelliği de içerirler.

<h2> SQL İnjection Nasıl Önlenir? </h2>

Bir SQL enjeksiyon saldırısını önlemenin ilk adımı, hangi uygulamaların savunmasız olduğunu belirlemektir.
Gerçek şu ki bir SQL veritabanıyla etkileşime giren herhangi bir web sitesi risk altındadır.

SQL enjeksiyonunu önlemek için dinamik sorgulara izin vermemeniz ya da kötü niyetli SQL içeren, kullanıcı tarafından sağlanan girdilerin sorgunun mantığını etkilemesini önlemeniz gerekir.

Ek olarak SQL enjeksiyonu saldırılarını önlemeye yönelik en bilinen önerileri şu şekilde sıralayabiliriz:

<ul>

  <li> <b> Parametreli Sorgular : </b> Parametreli sorgu, parametrelerin yer tutucu olarak kullanıldığı ve yürütme zamanında sağlandığı bir sorgudur. 
    Bu sorgu türünde, parametrelerin veri türleri önceden tanımlanır ve bazı durumlarda varsayılan değerler de ayarlanır.
    Bunu yapmak, SQL enjeksiyon sorgularının başarısız olmasına neden olur. </li>

  <li> <b> Saklı Prosedürler (Stored Procedures): </b> Saklı prosedürler, uygulamadan çağrılan veritabanında tanımlanan ve saklanan SQL ifadeleridir. 
    Saklı prosedürler, herhangi bir dinamik SQL üretimi içermeyen parametrelerle önceden oluşturulmuş SQL ifadeleridir. 
    Saklı yordamlar da denen bu prosedürleri ayarlamak için geliştiricilerin, gerekli girdiler için parametrelerle SQL ifadeleri oluşturması gerekir. 
    Saklı yordamlar ve parametreli sorgular arasındaki fark, saklı yordamların veritabanı içinde tanımlanması ve saklanması, ancak uygulamadan çağrılmasıdır. 
    Ayrıca, saklı yordamlar bazı DBMS’lerde (varsayılan olarak mevcut değildir) yürütme hakları gerektirdiğinden, kullanıcı erişimi vermek yerine en az ayrıcalığa sahip ayrı bir hesap oluşturmak önemlidir. </li>

  <li> <b> İzin Verilenler Listesi Giriş Doğrulaması (Allowlist Input Validation): </b> İzin verilenler listesi girdi doğrulaması, harici girdileri bilinen, onaylanmış bir dizi girdiye karşı kontrol eder ve eşleşmeyen girdilerde başarısız olur. 
    Bu, yalnızca bağlama değişkenlerine izin verilmeyen durumlarda kullanılmalıdır. İzin verilenler listesi giriş doğrulaması, girişi sorguya iletilmeden önce algılamak için bir yedekleme seçeneği de olabilir. </li>
</ul>
