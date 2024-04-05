<h1 align=center> Man-In-The-Middle (MITM) Nedir? </h1>

![Ortadaki-Adam-MITM-Saldirisi-Nedir](https://github.com/oakkaya098/Cyber-Security/assets/152402130/860bbed2-31c8-438b-bc5f-76d84a5ab81d)

Ortadaki adam (MITM) saldırısı, saldırganların gizlice dinleyerek veya meşru bir katılımcı gibi davranarak mevcut bir konuşmayı veya veri aktarımını engellediği bir tür siber saldırıdır. Kurbana, standart bir bilgi alışverişi
yapılıyormuş gibi görünecek ancak saldırgan kendilerini konuşmanın veya veri aktarımının "ortasına" sokarak, bilgileri sessizce ele geçirebilir.

Bir <b> MITM </b> saldırısının amacı, kimlik hırsızlığı veya yasa dışı fon transferleri gibi başka suçları işlemek için kullanılabilecek banka hesap bilgileri, kredi kartı numaraları veya oturum açma kimlik bilgileri gibi
gizli verileri almaktır. MITM saldırıları gerçek zamanlı olarak gerçekleştirildiğinden, genellikle çok geç olana kadar fark edilmezler.

<h2> Ortadaki Adam Saldırısının İki Aşaması </h2>

Başarılı bir MITM saldırısı, iki özel aşamadan oluşur: Müdahale ve Şifre Çözme
 
 <h2> Müdahale </h2>
 
  
 Müdahale, saldırganın, hedeflenen hedefe ulaşmadan önce sahte bir ağla araya girerek kurbanın meşru ağına müdahale etmesini içerir. 
  Durdurma aşaması, esasen saldırganın kendilerini "ortadaki adam" olarak nasıl yerleştirdiğidir. Saldırganlar bunu sıklıkla, halka açık bir alanda parola gerektirmeyen sahte bir Wi-Fi etkin noktası oluşturarak yaparlar. 
  Bir kurban etkin noktaya bağlanırsa, saldırgan gerçekleştirdiği tüm çevrimiçi veri alışverişlerine erişim kazanır. 
  <ul type=disc> 
  <p></p>
    
<li> <b> IP Spoofing : </b> Wi-Fi bağlantılı her cihazın, ağa bağlı bilgisayarların ve cihazların nasıl iletişim kurduğunun merkezinde yer alan bir internet protokolü (IP) adresi vardır. IP sahtekarlığı, kurbanın
bilgisayar sisteminin kimliğine bürünmek için bir saldırganın IP paketlerini değiştirmesini içerir. Kurban, o sisteme bağlı bir URL'ye erişmeye çalıştığında, bilmeden bunun yerine saldırganın web sitesine gönderilir.</li>

<li> <b> ARP Spoofing: </b> Adres Çözümleme Protokolü (ARP) sahtekarlığı ile saldırgan, MAC adresini kurbanın meşru IP adresiyle ilişkilendirmek için sahte ARP mesajları kullanır. 
  Saldırgan, MAC adresini gerçek bir IP adresine bağlayarak, ana bilgisayar IP adresine gönderilen tüm verilere erişim elde eder. </li>

  <li> <b> DNS Spoofing: </b> DNS önbellek zehirlenmesi olarak da bilinen Etki Alanı Adı Sunucusu (DNS) sahtekarlığı, bir saldırganın kurbanın web trafiğini amaçlanan web sitesine çok benzeyen sahte bir web sitesine yönlendirmek için DNS sunucusunu değiştirmesini içerir. 
    Kurban, hesabı olduğuna inandığı bir hesapta oturum açarsa, saldırganlar kişisel verilere ve diğer bilgilere erişebilir. </li>
  
  </ul>

  <h2> Şifre Çözme </h2>
  
Bir MITM saldırısı müdahalede durmaz. Saldırgan, kurbanın şifrelenmiş verilerine eriştikten sonra, saldırganın okuyabilmesi ve kullanabilmesi için şifresinin çözülmesi gerekir. 
Kullanıcıyı veya uygulamayı uyarmadan kurbanın verilerinin şifresini çözmek için bir dizi yöntem kullanılabilir:

<ul type=disc>

  <li> <b> HTTPS Spoofing: </b> HTTPS sızdırma, tarayıcınızı belirli bir web sitesinin güvenli ve güvenilir olmadığı halde güvenilir olduğunu düşünmesi için kandırmak için kullanılan bir yöntemdir. 
    Bir kurban güvenli bir siteye bağlanmaya çalıştığında, tarayıcılarına sahte bir sertifika gönderilir ve bu da onları saldırganın kötü niyetli web sitesine yönlendirir. 
    Bu, saldırganın, kurbanın o sitede paylaştığı tüm verilere erişmesini sağlar. </li>

  <li> <b> SSL Hijacking: </b> URL’de “HTTP” ile belirtilen, güvenli olmayan bir web sitesine her bağlandığınızda, sunucunuz sizi otomatik olarak o sitenin güvenli HTTPS sürümüne yönlendirir. 
    SSL ele geçirme ile saldırgan, yeniden yönlendirmeyi engellemek için kendi bilgisayarını ve sunucusunu kullanır ve kullanıcının bilgisayarı ile sunucusu arasında geçen herhangi bir bilgiyi kesintiye uğratmasına olanak tanır. 
    Bu, kullanıcının oturumları sırasında kullandığı tüm hassas bilgilere erişmelerini sağlar. </li>

  <li> <b> SSL Stripping: </b> SSL Stripping, saldırganın bir kullanıcı ile bir web sitesi arasındaki bağlantıyı kesmesini içerir. 
    Bu, bir kullanıcının güvenli HTTPS bağlantısını web sitesinin güvenli olmayan bir HTTP sürümüne indirgeyerek yapılır. 
    Bu, kullanıcıyı güvenli olmayan siteye bağlarken, saldırgan güvenli siteyle bağlantısını sürdürür ve kullanıcının etkinliğini saldırgan tarafından şifrelenmemiş bir biçimde görünür hale getirir. </li>
  
</ul>

</ul>
