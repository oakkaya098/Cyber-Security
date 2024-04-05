<h1 align=center > OS Command Injection Nedir? </h1>
Command Injection, saldırganın zafiyetli uygulamayı çalıştıran sunucuda işletim sistemi (OS) komutları yürütmesine, genellikle uygulamanın ve tüm verilerin tamamen tehlikeye girmesine izin veren bir web güvenlik açığıdır.
Uygulamaların, sistem komutlarını yürütmek için system() veya exec() gibi kabuk fonksiyonlarını çağırırken kullandıkları parametreleri düzgün bir şekilde doğrulayamadığı ve sanitize edemediği durumlarda ortaya çıkar.

<h2> Tespiti ve İstismarı </h2>

<ul> 

  <li> <b> Doğrudan Komut Enjeksiyonu : </b> İlk olarak saldırgan, uygulamanın doğrudan kullanıcı tarafından girilen verileri komuta argüman olarak ileterek bir sistem komutu çağırdığını keşfeder. Daha sonra beklenen
  argümanların bir parçası olarak zararlı komutu girer. Böylece uygulama, orijinal komutu ve hemen ardından zararlı komutu yürütür.
<p></p>
     </li> 
  <ul type=disc>
    <li> Saldırgan, uygulamanın bir komutu yürütmek için istemci girdisini kullandığını keşfeder. </li>
    <li> İstemci girdisinin bir parçası olarak zararlı komutu uygulamaya gönderir. </li>
    <li> Son olarak da zararlı komutu yürüten uygulamanın davranışını gözlemler. </li>
  </ul>
<p></p>
    <li> <b> Dolaylı Komut Enjeksiyonu : </b> Bu komut enjeksiyonu örneği, savunmasız uygulamaya ek komutun, bir dosya veya ortam değişkeni aracılığıyla dolaylı olarak gönderilmesiyle oluşur. 
      İlk olarak saldırgan, uygulamanın -dosya veya ortam değişkeni gibi- harici kaynaktan gelen verileri kullanarak bir sistem komutu çağırdığını keşfeder. 
      Daha sonra zararlı bir komut eklemek için dış kaynağın içeriğini değiştirir. Ardından, uygulamayı orijinal komutla birlikte zararlı komutu yürütmeye zorlar.
</li> 
     <p></p>
     
  <ul type=disc>
    <li> Saldırgan, uygulamanın komut yürütmek için harici bir kaynakta depolanan verileri kullandığını keşfeder. </li>
    <li> Dış kaynağı kötü amaçlı komut içerecek şekilde düzenler. </li>
    <li> Uygulamanın orijinal komutu yürütmesini bekler ya da uygulamayı buna zorlar. </li>
    <li> Son olarak, uygulamanın enjekte edilen komutu yürüttüğünü doğrular. </li>
  </ul>
<p>  </p>
</ul>
  <ul type=disc>
    <li> <b> Kör Komut Enjeksiyonu : </b>OS komut enjeksiyonunun bir türü de kör komut enjeksiyonudur. Bu, uygulamanın HTTP yanıtındaki komuttan çıktı döndürmediği anlamına gelir. 
      Bu zafiyetten faydalanmak için "zaman gecikmesi (time delay)", "çıktı yönlendirme" gibi farklı teknikler gereklidir. </li>
  </ul>
  

  
</ul>
