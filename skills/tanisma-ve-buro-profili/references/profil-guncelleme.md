# Profil güncelleme ("profili güncelle", "şu alanı değiştir")

Upstream `customize` uyarlaması: bütün görüşmeyi yeniden yapmadan **tek bir şeyi** değiştirmek.

## Akış

1. **Profili oku.** Yoksa ya da `Rol:` `[DOLDURULACAK]` ise: "Henüz profiliniz yok. Güncelleme var olan profili değiştirmek içindir; önce kısa kurulumu (2 dakika) yapalım mı?" Dosya sistemi yoksa `web-ve-chatgpt.md` §4.

2. **Değiştirilebilir haritayı göster** (kullanıcı neyi değiştireceğini zaten söylediyse bu adımı atla). Her satır güncel değerin tek satırlık özetiyle:
   - **Kim kullanıyor** — rol, kullanıcı türü, avukat irtibatı, staj avukatı
   - **Taraf** — varsayılan ve alan bazında
   - **Uzmanlık** — ana alanlar, bakılmayan alanlar
   - **Yer** — şehir, adliyeler
   - **Üslup** — dil düzeyi, dilekçe biçimi, atıf biçimi, imza bloğu, Word tercihi
   - **Risk iştahı** — tutum ve büroya özgü eşikler
   - **Yükseltme** — kişi, otomatik durumlar
   - **Şablonlar** — sık belgeler, şablon konumu
   - **Elektronik işlemler** — UYAP, UETS, KEP
   - **Bağlantılar** — yeniden kontrol ("bağlantıyı kontrol et")
   - **Alan bölümleri** — İş hukuku, Sözleşme playbook'u (bu bölümler ilgili beceriyle birlikte değiştirilir)
   - **Çıktı tercihleri** — yönlendirme onayı, uzunluk

3. **"Neyi değiştirelim?"** — bölüm seçilebilir ya da serbest cümle ("artık işveren tarafındayım").

4. **Değişikliği yap:** güncel değeri göster → yeni değeri al → **sonucunu söyle** → onay → yaz. Örnekler:
   - *İş hukukunda taraf işçi → işveren:* "`is-hukuku` bundan sonra fesih öncesi kontrolü ve ispat yükünü öne alır; işçi tarafındaki 'süre kaçırma' uyarıları yine kalır. Önceki çıktılar değişmez."
   - *Dil düzeyi hukukçu → çok sade:* "Çıktılarda terimlerin yanına parantez içinde açıklama ve kısa cümle gelir; dilekçe metinlerinin kendisi resmî dilde kalır."
   - *Rol avukat → avukat olmayan:* "Her çıktının ilk satırı 'ARAŞTIRMA NOTUDUR — HUKUKİ TAVSİYE DEĞİLDİR…' olur ve dilekçe, ihtarname, ibraname gibi adımlardan önce 'avukatla gözden geçirdiniz mi?' diye sorarım." (Bu değişiklik büyüktür; kullanıcının gerçekten rolünün değiştiğini teyit et.)
   - *Yeni yükseltme kişisi:* "Karar ağacındaki 'Yükselt' seçeneği bundan sonra [kişi] için özet hazırlar."
   - *İmza bloğuna sicil numarası eklemek:* önce `gizlilik-ve-saklama.md` §2 uyarısı, sonra kullanıcının seçimi.

5. **Tarih:** profilin üstündeki "Son güncelleme" satırını yenile.

6. **Kapanış:** "Tamam. Bir sonraki çıktı bu değişikliği yansıtır. Başka bir şey?"

## Korkuluklar

- **Bölüm silinmez.** Kullanıcı bir şeyi "kaldır" derse değeri `[Kullanılmıyor]` yap ve ne değişeceğini söyle (ör. İş hukuku bölümü kullanılmıyorsa `is-hukuku` işçi sayısını her seferinde sorar).
- **Tutarsızlığı işaretle.** Değişiklik profili kendi içinde çelişkili yapıyorsa (ör. rol "vatandaş" ama dilekçe imza bloğu "Av."; taraf "işveren" ama kullanıcı türü "işçi olarak kendi meselem"; risk "atak" + otomatik yükseltme "her iş") gerilimi göster, hangisinin geçerli olduğunu sor.
- **Korkuluk aşındırma.** Taslak başlığını, kaynak etiketlerini, `[doğrula]`/`[incele]` işaretlerini, sayısal değerlerin araçtan çekilmesini ya da avukat olmayan için "Taslaktır" kapısını kapatma isteği: neyi koruduğunu bir cümleyle açıkla (ör. "`[doğrula]` işareti, temiz görünen ama yanlış bir sürenin dilekçeye girmesini önler"), değiştirme ve `## Notlar` bölümüne "kullanıcı istedi, korkuluk yerinde kaldı — [tarih]" yaz. Stajyerde "staj avukatı onayı" işareti de bu kapsamdadır.
- **Bir seferde bir değişiklik.** Kullanıcı birden çok şey sayarsa sırayla yap; bütün görüşmeyi yeniden sorma.
- **Söylenen hukuki olgu** (eşik, süre) yine ORTAK-KURALLAR.md §6'ya tabidir; profile yazmadan araçtan kontrol et.
- **Müvekkil verisi** güncelleme yoluyla da profile girmez (`gizlilik-ve-saklama.md` §1).

## Başka becerilerden gelen güncelleme

Bir alan becerisi iş sırasında "bunu profile ekleyeyim mi?" diye sorabilir (ör. `sozlesme-incelemesi-tbk` playbook boşluğu, `is-hukuku` işçi sayısı). Kullanıcı açıkça "evet" derse o beceri yalnız kendi bölümüne yazar; genel bölümleri (rol, taraf, üslup) değiştirmesi gerekiyorsa bu beceriye yönlendirir. Sessiz güncelleme yoktur: her yazım kullanıcıya tek satırla bildirilir.
