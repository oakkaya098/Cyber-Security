<h1 align=center> HeartBleed Zafiyeti Nedir? </h1>

OpenSSL’in kütüphanesinde bulunan güvenlik açığından ortaya çıkan bir zafiyettir. 
Bu zafiyet sömürüldüğünde Server veya Client üzerinde anlık 64kb’lık Bellek alanına yetkisiz şekilde erişim yapılabilmektedir. 
Bu sayede sunucunun RAM bellekleri üzerinde yer alan şifrelenmiş olduğu söylenen verilerin tamamı okunabilmektedir.

Bu veriler;
<ul>
  <li> Şifreler </li>

  <li> Anlık Mesajlaşmalar </li>

  <li> Private Key'ler </li>

  <li> Kullanıcı Adları </li>

  <li> E-Mailler </li>

  <li> X.509 Sertifikaları </li>
</ul>

Güvenli iletişim için verilerin şifrelenmiş olarak gönderilip-alınmasını sağlayan OpenSSL, iletişim sırasında verinin doğru bir şekilde alındığını doğrulamak için verileri geri yansıtan bir “HeartBeat(Kalp Atışı)” mesajı gönderir.
<p></p>

Saldırgan ise bu zafiyetin bulunduğu Server&Client’e 1KB’lık bir veri gönderir ama Server&Client’in kontrol etmesi ve verileri geri yansıtması yani “HeartBeat” işlemi yapması gereken 64KB veri olduğunu söyleyerek kandırır. 
Bunun üzerine sistem, saldırgana 64KB boyutunda veri geri yansıtır.

<h2> HeartBleed Zafiyeti Nasıl Sömürülür? </h2>

Bir site veya sunucu üzerinde bu açıklığın olup olmadığını test eden basit Nmap scripti şu şekildedir;

<b> nmap -p <PortNo> --script ssl-heartbleed.nse <IPAdresi> </b>

Ayrıca Shodan gibi Siber İstihbarat sağlayan siteler üzerinden belirli filtreler birleştirilerek yapılan aramalarda bu zafiyete sahip olan OpenSSL kullanan IP adresleri bile bulunabilir.

<b> Adım 1 </b>

![1-1](https://github.com/oakkaya098/Cyber-Security/assets/152402130/6fbb5035-2343-432d-8e65-af424cb4072b)

<b> Adım 2 </b>

![2](https://github.com/oakkaya098/Cyber-Security/assets/152402130/90e93e3d-a1b7-4a00-9642-97adbf6e2ad1)

<b> Adım 3 </b>

![3 1](https://github.com/oakkaya098/Cyber-Security/assets/152402130/96a7f728-c337-4eb8-ac61-c30b98f5a174)

<b> Adım 4 </b>

![4](https://github.com/oakkaya098/Cyber-Security/assets/152402130/f70943eb-0d3d-4b61-b617-cff10c7f4415)

<b> Adım 5 </b>

Zafiyeti sömürdüğümüz zaman 64KB’lık bir veriye erişebilmiş&okuyabilmiş olduk. 
Diğer ekran görüntüsünde ise bir “.bin” uzantılı dosya oluşturup bu verileri oraya yazdığı bilgisini görüyoruz.

![5 1](https://github.com/oakkaya098/Cyber-Security/assets/152402130/c924872d-23d5-4492-a66d-32e0b105534f)

<b> Adım 6 </b>

“Strings” komutu ile bu “.bin” dosyasını inceleyerek daha sonradan da verilere erişebiliriz.

![6](https://github.com/oakkaya098/Cyber-Security/assets/152402130/677b2819-ba49-4cb8-8922-19c9aae04b1c)
