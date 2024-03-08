<h1 align=center> Open Authorization (OAuth) Nedir? </h1>
Open Authorization (OAuth), çevrimiçi servisler ve uygulamalar arasında güvenli ve yetkilendirilmiş erişim sağlamak için kullanılan bir kimlik doğrulama ve yetkilendirme protokolüdür. 
OAuth, kullanıcıların başka bir uygulamayı veya servisi, kimlik bilgilerini (kullanıcı adı ve parola gibi) doğrudan paylaşmadan erişmelerini sağlar.
OAuth, birçok çevrimiçi hizmette ve platformda kullanılan standart bir yetkilendirme protokolüdür. 
Özellikle, sosyal medya platformları, bulut hizmet sağlayıcıları ve diğer web uygulamaları tarafından benimsenmiştir.
<p></p>

OAuth, genellikle 4 rol içerir:

<ul> 
  
  <li> <b> Kullanıcı (Resource Owner) : </b> Kullanıcı, kendi verilerine erişimi kontrol eden ve uygulamalara erişim izni verebilen kişidir. </li>

  <li> <b> Uygulama (Client) : </b> Üçüncü taraf uygulama veya servis, kullanıcının verilerine erişmek için OAuth protokolünü kullanır. </li>

  <li> <b> Yetkilendirme Sunucusu (Authorization Server) : </b> Yetkilendirme sunucusu, kullanıcının kimlik doğrulamasını ve yetkilendirilmesini yönetir ve erişim belirteçlerini sağlar. </li>

  <li> <b> Kaynak Sunucu (Resource Server) : </b> Kullanıcının verilerini barındıran sunucu, erişim belirteçlerini doğrular ve istemci uygulamalara veriye erişim izni sağlar. </li>

</ul>

OAuth'un ana kullanım senaryoları şunlardır:

<ul>
  <li> <b> Üçüncü Taraf Uygulama Entegrasyonu : </b> Kullanıcılar, bir üçüncü taraf uygulamanın belirli kaynaklarına erişim izni verebilirler. Örneğin, bir kullanıcı, bir sosyal medya platformunda başka bir uygulamanın hesap bilgilerini kullanarak oturum açmasına olanak tanıyan bir uygulamaya erişim izni verebilir. </li>

  <li> <b> API Yetkilendirme : </b> OAuth, bir API'nin belirli kaynaklarına erişim yetkilendirme için yaygın olarak kullanılır. Kullanıcılar, bir uygulamanın API'sine erişmek için OAuth token'larını kullanırlar ve bu token'lar, kullanıcının API'ye erişim iznini belirtir. </li>

  <li> <b> Tek Oturum Açma (Single Sign-On - SSO) : </b> OAuth, tek oturum açma işlemlerinde de kullanılabilir. Bir uygulama, kullanıcının diğer uygulamalara erişim izni almak için OAuth protokolünü kullanabilir ve kullanıcı, tek bir oturum açma işlemiyle birden fazla uygulamaya erişebilir. </li>
</ul>
