Bu laboratuvar, başka kullanıcıların hesabından para transfer etmye yol açan Güvensiz Doğrudan Nesne Referansları (IDOR) güvenlik açığı içerir.
Laboratuvarı tamamlamak için para transferi gerçekleştiren uç noktada bulunan IDOR zafiyetini istismar ederek "User 2" isimli kullanıcıdan kendi hesabınıza("User 1") para transfer edin.
Kullanıcı hesabına para geldiğinde görünen transfer numarası nedir?

<img width="1920" height="920" alt="Screenshot_2026-03-10_01_31_47" src="https://github.com/user-attachments/assets/15230948-a671-4c15-8d20-748b6481ecc9" />

Verilmiş olan siteye giriş yapıyoruz.


<img width="1920" height="920" alt="Screenshot_2026-03-10_01_33_57" src="https://github.com/user-attachments/assets/3ff81f99-4b58-4630-97f0-2ec7132f5864" />

Kaynak kodu incelediğimde <input class="form-control" type="hidden" name="sender_id" value="1"> Buradaki value="1" değeri, paranın hangi hesaptan çıkacağını belirleyen parametredir.

<img width="1920" height="920" alt="Screenshot_2026-03-10_01_36_11" src="https://github.com/user-attachments/assets/55252066-dc04-47d7-9453-123f7b73d83f" />

Manipülasyon: HTML kaynak kodu üzerinden value="1" olan değer value="2" olarak değiştirilmiştir.


<img width="1920" height="920" alt="Screenshot_2026-03-10_01_38_20" src="https://github.com/user-attachments/assets/4ece2f82-bb19-4d08-8d1f-d34c9b7d6301" />

Gönderici ID Değişimi: Gizli input alanındaki sender_id değeri "2" olarak ayarlanmıştır.

Alıcı Belirleme: Receiver ID kısmına "1" (kendi hesabımız) yazılmıştır.

Tutar: Transfer tutarı olarak "888" birim girdik ve transfer işlemi gerçekleşti.

Ekranda gördüğümüz banka hesap numarası sorumuzun çözümü oluyor.
