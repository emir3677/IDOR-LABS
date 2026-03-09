Bu laboratuvar, diğer kullanıcıların parolasını yetkisiz bir şekilde değiştirmeye yol açan Güvensiz Doğrudan Nesne Referansları (IDOR) güvenlik açığı içerir.

Laboratuvarı tamamlamak için "admin" kullanıcısının parolasını, parola değiştirme uç noktasındaki IDOR zafiyetini istismar ederek değiştirin ve hesabına giriş yapın.

"admin" isimli kullanıcının telefon numarası nedir? (Cevap Formatı: 000-000-0000)

<img width="1920" height="920" alt="Screenshot_2026-03-10_01_42_21" src="https://github.com/user-attachments/assets/d98b0e51-1ce9-4a50-bc00-ffabd62435ad" />

Verilmiş olan adresimize girdiğimizde karşımıza çıkan site bu şekilde görünüyor.

Verilmiş olan kullanıcı adı ve şifremizi test test olarak yazıp login oluyoruz.


<img width="1920" height="920" alt="Screenshot_2026-03-10_01_44_14" src="https://github.com/user-attachments/assets/3d30841e-55ca-4c5a-ba97-cb855e8e544b" />

Giriş yaptıktan sonra kaynak kod incelememizde confirm butonuna odaklanarak <input class="form-control" type="hidden" name="user_id" value="2"> kod bloğunu görüyoruz.

Manipülasyon ve Sömürü (Manipulation & Exploitation):
Saldırı senaryosu kapsamında şu adımlar uygulanmıştır:

 Tarayıcı geliştirici araçları kullanılarak user_id parametresinin value değeri "1" olarak değiştirilmiştir.

"Enter your new password" alanına yeni bir şifre girilmiştir.

"Confirm" butonuna basılarak istek gönderilmiştir

<img width="1920" height="920" alt="Screenshot_2026-03-10_01_48_11" src="https://github.com/user-attachments/assets/0c3a72fe-cc5a-41b4-a301-9e847849e429" />

Hedef Belirleme: Sistemdeki en yetkili kullanıcı olan Admin (ID: 1) hedef olarak seçilmiştir.

Parametre Manipülasyonu: Geliştirici araçları (Inspect) kullanılarak, formdaki gizli giriş alanı (hidden input) şu şekilde manipüle edilmiştir:

    Orijinal: <input type="hidden" name="user_id" value="2"> (Kendi ID'miz)

    Manipüle Edilmiş: <input type="hidden" name="user_id" value="1"> (Admin ID'si)

Yetkisiz İşlem: "Enter your new password" alanına saldırgan tarafından belirlenen yeni bir şifre girilmiş ve "Confirm" butonuna basılmıştır.

Sonuç: Sunucu, işlemi yapan kişinin gerçekten ID 1 olup olmadığını kontrol etmediği için, Admin kullanıcısının şifresini saldırganın girdiği yeni şifre ile başarıyla güncellemiştir.
Sistemden çıkış yapıyoruz ve kullanıcı adı admin yazıp belirlemiş olduğumuz şifreyi(25) yazıp tekrar login oluyoruz.


<img width="1920" height="920" alt="Screenshot_2026-03-10_01_51_30" src="https://github.com/user-attachments/assets/a8d4fc1b-941f-45fb-83d1-1c79ab1cc345" />

Böylelikle ekranda gördüğümüz adminin telefon numarasına ulaşmış oluyoruz.



