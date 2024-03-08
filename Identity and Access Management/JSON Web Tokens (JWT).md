<h1 align=center> JSON Web Tokens (JWT) Nedir? </h1>

JSON Web Token (JWT), bir kullanıcı veya cihazın bir web uygulamasına veya servisine güvenli bir şekilde kimlik bilgilerini temsil etmek için kullanılan bir standarttır. 
JWT, JSON formatında verileri taşır ve bu verileri dijital olarak imzalar. JWT, aynı zamanda bilgiyi şifrelemek için de kullanılabilir. 
Genellikle, kullanıcı kimliği, yetkilendirme bilgileri ve diğer talep bağlamı bilgileri gibi verileri barındırır.
<p></p>

Bir JWT, üç bölümden oluşur:

<ul> 
  <li> <b> Header (Başlık) : </b> JWT'nin türünü ve kullandığı algoritmayı belirtir. </li>

  <li> <b> Payload (İçerik) : </b> Gerçek verileri içerir. Bu, kimlik bilgileri, kullanıcı id'si gibi bilgileri içerebilir. 
    JSON formatında veriler bu kısımda yer alır. </li>

  <li> <b> Signature (İmza) : </b> Başlık ve içeriği birleştirerek oluşturulan dijital imzadır. 
    Bu, JWT'nin değiştirilmediğini ve güvenilir olduğunu doğrulamak için kullanılır. </li>
</ul>
<p></p>


JSON Web Token (JWT), web uygulamaları ve servislerinde kullanıcı kimlik doğrulaması ve yetkilendirme için kullanılan bir standarttır. 
JWT'ler, özellikle aşağıdaki senaryolarda yaygın olarak kullanılır:

<ul>
  <li> <b> Kimlik Doğrulama (Authentication) : </b> Kullanıcıların kimliklerini doğrulamak için JWT'ler kullanılır. 
    Kullanıcı oturum açtığında veya kimlik sağlayıcısından (örneğin, OAuth sağlayıcısı) bir token aldığında, bu JWT, kullanıcının kimliğini temsil eder. 
    Web uygulamaları ve servisler, bu JWT'yi kullanarak kullanıcının kimliğini doğrularlar. </li>

  <li> <b> Yetkilendirme (Authorization) : </b> JWT'ler, kullanıcılara belirli kaynaklara veya işlevlere erişim izni vermek için kullanılır. 
    JWT içeriği, kullanıcının erişim izinleri veya rolleri gibi yetkilendirme bilgilerini içerebilir. 
    Web uygulamaları ve servisler, bu JWT'yi kullanarak kullanıcının erişim yetkisini belirlerler. </li>

  <li> <b> API Güvenliği : </b> API'lerde, kullanıcı kimlik doğrulaması ve yetkilendirme için JWT'ler yaygın olarak kullanılır. 
    Kullanıcılar, API'ye istek yaparken JWT'lerini gönderirler ve API, bu JWT'yi kullanarak kullanıcıyı doğrular ve yetkilendirir. </li>

  <li> <b> Tek Oturum Açma (Single Sign-On - SSO) : </b> JWT'ler, birden fazla uygulama veya servis arasında tek oturum açma işlemlerinde kullanılabilir. 
    Kullanıcı bir uygulamaya oturum açtığında, bu uygulama JWT'yi kullanarak diğer uygulamalara erişim izni alabilir. </li>
</ul>
<p></p>

JWT'ler, verilerin taşınması ve güvenliği için hafif, taşınabilir ve güvenilir bir yöntem sağlar. 
Ayrıca, JSON formatında olduğu için, modern web teknolojileriyle uyumludur ve farklı platformlar arasında kolayca taşınabilirler. 
Bu nedenle, JWT'ler, kimlik doğrulama ve yetkilendirme için tercih edilen bir standarttır.
