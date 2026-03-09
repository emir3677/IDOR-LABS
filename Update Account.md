Bu laboratuvar, diğer kullanıcıların hesap bilgilerini yetkisiz bir şekilde değiştirmeye yol açan Güvensiz Doğrudan Nesne Referansları (IDOR) güvenlik açığı içerir.

Laboratuvarı tamamlamak için "Renee Misson" kullanıcısının hesap bilgilerini değiştirebileceğiniz uç noktadaki IDOR zafiyetini tespit edin. Diğer kullanıcıların hesap bilgilerini görüntüleyin.

"Renee Misson" isimli kullanıcının telefon numarası nedir? (Cevap Formatı: 000-000-0000)
🛡️ Proje: Güvensiz Doğrudan Nesne Referansı (IDOR) Analizi

Bu çalışma, bir web uygulamasının kullanıcı profil yönetim sistemindeki IDOR (Insecure Direct Object Reference) zafiyetinin tespitini ve sömürülmesini içermektedir.
🔍 Zafiyet Analizi

Uygulama, kullanıcı oturumlarını yönetmek ve profil bilgilerini getirmek için istemci tarafındaki HTTP Cookie değerlerine güvenmektedir.
id parametresinin sunucu tarafında yetkilendirme kontrolüne (Authorization Check) tabi tutulmaması, bir kullanıcının sadece bu değeri değiştirerek diğer kullanıcıların hassas verilerine
erişmesine olanak tanımaktadır.

Verilmiş olan siteye girdiğimizde karşımıza farklı bir kullanıcının bilgilieri çıkıyor.


<img width="1920" height="920" alt="Screenshot_2026-03-10_02_05_42" src="https://github.com/user-attachments/assets/130209ae-7591-47c8-bddb-c64c2063eddb" />

🛠️ İzlenen Adımlar (PoC)

  İsteğin Yakalanması: Tarayıcı geliştirici araçları (Network sekmesi) kullanılarak profil güncelleme isteği incelenmiştir.(Save) butonuna tıklayarak post metodunu yakalıyoruz.

  
<img width="1920" height="920" alt="Screenshot_2026-03-10_02_06_37" src="https://github.com/user-attachments/assets/5e90d54c-b254-46a2-a68a-db62a1370d3c" />

Parametre Tespiti: HTTP isteklerinde Cookie: id=1 parametresinin kullanıcı kimliğini tanımladığı tespit edilmiştir.

<img width="1920" height="920" alt="Screenshot_2026-03-10_02_08_24" src="https://github.com/user-attachments/assets/2f823501-2264-40e0-b61c-b35aacc713c3" />

Manipülasyon: Tarayıcının Storage (Depolama) sekmesi üzerinden id değeri 2 olarak değiştirilerek sunucuya yeni bir istek gönderilmiştir.

<img width="1920" height="920" alt="Screenshot_2026-03-10_02_09_28" src="https://github.com/user-attachments/assets/2a232699-8042-4684-bb50-9e6508a0afde" />

Gördüğümüz üzere kullanıcı değişti fakat aradığımız kişi olmadığı için tarayıcının Storage (Depolama) sekmesi üzerinden id değeri 3 olarak değiştirilerek sunucuya yeni bir istek gönderidik.

<img width="1920" height="920" alt="Screenshot_2026-03-10_02_11_08" src="https://github.com/user-attachments/assets/6fe6f39b-0b0a-4637-a9e6-401eb2587e97" />

Erişim ve Veri Sızıntısı: Sunucu, yetki kontrolü yapmadan id=3 değerine sahip olan "Renee Misson" isimli kullanıcının telefon numarası ve adres gibi kişisel bilgilerini (PII) döndürmüştür.








