<h1 align="center"> XML Parserlar ve XML External Entity (XXE) İnjection </h1>

<h2> XML External Entity İnjection (XXE) Nedir? </h2>

Kullanıcıdan alınan XML belgesi parse edilirken araya kendi döküman, entity tanımlarımızı yerleştirmemizle “Arbitrary File Read”, 
“Command Execution” gibi kritik zaafiyetler elde edebildiğimiz bir güvenlik açığıdır.

![XXE-1](https://github.com/oakkaya098/Cyber-Security/assets/152402130/019f7b35-5f97-42be-9544-d0f8c4dc0ab3)


<h2> XXE güvenlik açığı sayesinde aşağıdaki saldırılar gerçekleştirilebilir: </h2>

<ul>

  <li> SSRF (sunucu taraflı istek sahteciliği) </li>

  <li> DDOS </li>

  <li> Sunucudan Dosya Okuma </li>

  <li> RCE </li>
  
</ul>

<h2> XML Nedir? </h2>

XML (Extensible Markup Language), hem insanlar hem bilgi işlem sistemleri tarafından kolayca okunabilecek dokümanlar oluşturmaya yarayan bir işaretleme dilidir. 
Bu özelliği ile veri saklamanın yanında farklı sistemler arasında veri alışverişi yapmaya yarayan bir ara format görevi de görür.

<h2> XML’in Özellikleri & Kuralları Nelerdir? </h2>

![XXE-2](https://github.com/oakkaya098/Cyber-Security/assets/152402130/6897f4f6-4870-45d5-9328-29cde928d0c3)


<ul> 

  <li> Bütün XML dökümanlarının bir kök elemanı vardır. Bu kök elemanı diğer bütün elemanları kapsar. Yukarıdaki örnekte <note> bir kök elemanıdır. </li>

  <li> XML etiketleri büyük-küçük harf’e duyarlıdır. Örneğin <isim> ve <İsim> etiketleri XML’e göre birbirinden farklıdır. 
    Bu nedenle açılış ve kapanış etiketlerinin tamamen aynı biçimde yazıldığına dikkat edilmelidir. </li>

  <li> Bütün XML elemanlarının kapanma etiketi olmalıdır. Örneğin </isim>, </soyisim> vb. </li>

  <li> XML belgelerinde, <b> < " ' & > </b> karakterleri etiket tanımlamak haricinde kullanılmaz. Bu karakterleri kullanmanız gerekiyorsa CDATA ile kullanabilirsiniz. 
    Aşağıda CDATA’nın örnek bir kullanımı gösterilmiştir. </li>

</ul>

<h2> Document Type Definition (DTD) Nedir? </h2>

Bir XML belgesinin hangi etiketleri içerebileceği, etiketlerin sahip olabileceği özellikleri, 
hangi elemanların diğer hangi elemanları içerebileceği gibi dil yapısı bilgileri o uygulama için geliştirilmiş olan DTD adlandırılan belge tanımlama dosyasında belirtilir.

DTD’ler, XML belgesinin içerisinde (internal) tanımlanabileceği gibi başka bir kaynak (external) üzerinden de dahil edilebilir. 
Harici bir kaynağa erişim sağlamak için XML’in desteklendiği SYSTEM niteliğini kullanıyoruz. SYSTEM niteliği, HTTP ve FILE gibi protokolleri desteklemektedir.

Aşağıdaki resimlerde internal ve external dtd’lerin nasıl tamınlanabileceği gösterilmiştir.

![XXE-3](https://github.com/oakkaya098/Cyber-Security/assets/152402130/89217a75-e1e6-4ff4-806c-e72ffd215836)


![XXE-4](https://github.com/oakkaya098/Cyber-Security/assets/152402130/3033c127-09eb-48c8-a259-6bfedf9969c9)


Aşağıdaki XML belgesini incelediğimizde;

<ul>

  <li> Note adında bir döküman tanımının olduğunu ve bu döküman tanımının içerisinde isim adında bir entity tanımlandığını görüyoruz. </li>

  <li> Entity’leri programlama dillerindeki değişkenler olarak düşünebiliriz. Aşağıdaki entity tanımında isim değişkeninin içerisine “Sefa” değerinin atıldığını görüyoruz. </li>

  <li> <email> etikeninin olduğu satıra baktığımızda, daha demin tanımlamış olduğumuz entity’nin çağırıldığını görüyoruz. 
    XML parser tarafından aşağıdaki XML belgesi parse edildiğinde &isim; değişkeninin olduğu yere Sefa değeri yazılacaktır. </li>

</ul>

![XXE-5](https://github.com/oakkaya098/Cyber-Security/assets/152402130/c87fb0b3-04c6-42d8-ac76-4b46a56dc616)


Temel anlamda XML’in ne olduğunu anladığımıza göre XXE zafiyetinin nasıl sömürülebileceğine geçebiliriz.

<h2> XXE Zafiyeti Senaryo </h2>

Aşağıdaki form’u doldurup, BurpSuite ile sunucuya giden isteği yakalıyoruz.

![XXE-6](https://github.com/oakkaya098/Cyber-Security/assets/152402130/51fb4698-c476-4ed7-b0da-60b1da3b712c)


BurpSuite ile yakaladığımız isteği incelediğimizde. Sunucuya bir XML belgesi gönderildiğini görüyoruz. 
Gönderilen XML’e baktığımızda kullanıcıdan alınan email bilgisinin ekrana bastırıldığını görüyoruz. Bu da akıllara XSS’i getiriyor.

Email değerini XSS payload’ı ile değiştirip sunucuya istek yaptığımızda XSS’in çalışmadığını görürüz. 
Bunun sebebi XML’in kurallarında da belirttiğimiz gibi < " ' & >gibi karakterleri kullanamıyor olmamızdır. XML belgesinde gönderilen değer ile XSS yapmak için CDATA kulllanılmalıdır.

![XXE-7](https://github.com/oakkaya098/Cyber-Security/assets/152402130/1dd5f848-62bd-40ce-a5e4-fec45b65acf8)


Kendimizin bir döküman tanımı oluşturabilip oluşuramayacağını anlamak için gönderilen XML üzerinde bir döküman tanımı yapıp sunucuya öyle istekte bulunuyoruz.

Kullanıcıdan alınan email değerinin ekrana basıldığını gördüğümüzden dolayı &isim;‘i email etiketinde çağırıyoruz.

![XXE-8](https://github.com/oakkaya098/Cyber-Security/assets/152402130/52b65142-4bad-4335-b41e-168ed807e577)


Sunucudan dönen yanıtta Sefa’yı görebildiğimize göre döküman tanımı yapabiliyoruz.

![XXE-9](https://github.com/oakkaya098/Cyber-Security/assets/152402130/e2df45a7-21b1-42b5-adcf-c60df2518364)


Kendi döküman tanımımızı yapabildiğimizi öğrendikten sonra bize bir sürü yeni özellik açılıyor.

Döküman tanımını external bir şekilde yapabileceğimizi yukarıda bahsetmiştik. Aynı şekilde entity tanımını da external bir şekilde yapabiliriz. 
Bu sayede sistemden istediğimiz dosyayı okuyup kendi oluşturduğumuz entity’e aktarıp bunu da ekrana bastırta biliriz.

Aşağıdaki XML dosyası;

<ul>

  <li> Sunucudaki gizliDosya.txt isimli dosyayı okuyup bu dosyanın içeriğini, oku isimli değişkene kaydedecek. </li>

  <li> &oku; sayesinde de bu dosyanın içeriğini ekrana bastırılacak. </li>
  
</ul>

![XXE-10](https://github.com/oakkaya098/Cyber-Security/assets/152402130/557266e3-a784-4c36-b37e-55495c88cdfa)


Aşağıdaki yanıtı incelediğimizde, gizliDosya.txt dosyasının içeriğini görebiliyoruz.

![XXE-11](https://github.com/oakkaya098/Cyber-Security/assets/152402130/53124a6e-6eb6-4188-a335-737bad24ce1f)


<b> Sonuç : </b>

Yukarıdaki saldırının geçekleşmesinin sebebi kullanıcıdan alınan değerin tekrar ekrana bastırılmasıydı.

Kodda ufak bir değişiklik yaparak kullanıcıdan alınan input’un ekrana basılmamasını sağlıyoruz.

<h2> XXE Güvenlik Açığının Oluşmasını Engellemek İçin Alınacak Önlemler Nelerdir? </h2>

<ul>

  <li> Tüm XML parser ve kütüphaneler güncellenmeli ve yamaları yüklenmelidir. </li>

  <li> Uygulamada bulunan tüm XML parser’ların XML External Entity özelliğinin kapatılmalıdır. </li>

  <li> Uygulamanın ihtiyaç duymadığı ya da kullanmak istemediği potansiyel olarak tehlikeli XML özellikleri devre dışı bırakılmalıdır. </li>

  <li> XML yerine JSON gibi daha az karmaşık veri biçimlerini kullanabilirsiniz. </li>
  
</ul>
