<h1 align=center> Public Key Infrastructure (PKI) Nedir? </h1>
PKI kısaca HTTPS’teki Authenticity için kullanılan dijital sertifikaların üretilmesi, dağıtılması ve kimlik doğrulaması aşamasında kullanılabilmesi için gerekli altyapıyı sağlar.
<p></p>

PKI’da, CA (Certificate Authority) adı verilen üçüncü parti güvenilir kuruluşlar güvensiz ağ (internet) üzerinde iletişimde bulunmak isteyen bütün partiler (istemci, sunucu) için dijital sertifikalar üretirler. 
Bu sertifikaların içerisine sertifikanın verildiği partilerin Public Key'i konur. 
Bu noktadan sonra bir parti iletişimde bulunduğu bütün partilere kendi sertifikasını göndererek karşı taraf ile Public Key'ini paylaşılmış olur.
<p></p>

Güvensiz ağ üzerinden aldığı sertifikanın gerçekten beyan edilen partiye ait olup olmadığını doğrulamak isteyen istemci aşağıdaki şekildeki gibi sertifika üzerindeki imzaları hiyerarşi içerisinde en yukarı kök sertifikaya kadar takip eder.

