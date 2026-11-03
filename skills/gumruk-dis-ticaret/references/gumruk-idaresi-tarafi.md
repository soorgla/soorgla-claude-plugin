# Gümrük idaresi (kamu görevlisi) tarafı: ek tahakkuk kararı, itiraz incelemesi, uzlaşma komisyonu

## Ne zaman kullanılır
- Gümrük müdürlüğü görevlisi: muayene ya da sonradan kontrol bulgusu üzerine ek tahakkuk ve ceza kararı düzenleyecek.
- Gümrük ve dış ticaret bölge müdürlüğü: m.242 itirazını inceleyip karar verecek.
- Uzlaşma komisyonu üyesi/sekretaryası: başvuruyu usulden ve esastan değerlendirecek.
- "Bu işlem iptal edilir mi?" — dava riski analizi.

Amaç hukuka uygun işlem kurmak ve dava riskini azaltmaktır; yükümlünün savunmasını kurma. İç değerlendirme ile yükümlüye gidecek yazıyı ayır (ORTAK-KURALLAR.md §1 gönderim yeri kontrolü). Biçim → `../../idari-ve-kurum-basvurulari/references/resmi-yazi-ve-olur.md`.

---

## A. Ek tahakkuk ve ceza kararı düzenlerken

| Kontrol | Dayanak |
|---|---|
| Tebliğ, yükümlülüğün doğduğu tarihten (tescil) itibaren 3 yıl içinde mi? | 4458 m.197/2, m.181/1 |
| Vergi ile vergiye bağlı ceza **aynı zamanda** karara bağlanıp tebliğ ediliyor mu? | m.232/1 |
| Birden fazla beyanname tek kararda birleştirilecekse konu ve yükümlü aynı, bağlılık var mı? | m.232/2 |
| Kararı yetkili amir (gümrük idaresi amiri ya da yardımcısı) mı verdi? | m.232/3 |
| Ceza bendi doğru mu: m.234 (%5 eşiği), 235, 236, 238 (gözetimden çıkarılmış mı), 241 | m.234-241 |
| Dolaylı temsilci muhatap yapılacaksa bilme/bilmesi gereken hâli somutlandı mı? | m.181/2 |
| Laboratuvar tahlili varsa m.243 itiraz hakkı ve 15 gün bildirildi mi? | m.243 |
| Kararda itiraz (15 gün, merci) ve uzlaşma (15 gün) yolu gösterildi mi? | m.242/1, m.244/1 |
| Kaçakçılık şüphesi varsa savcılık bildirimi ve uzlaşma yasağı notu | m.244/2 |
| Yükümlünün geçerli BTB/BMB'si var mı; bağlayıcılığı değerlendirildi mi? | m.9/2 |
| Menşe belgesi reddinde karşı ülke yazısı ve m.198/4 değerlendirmesi kalem bazında yazıldı mı? | m.198/4 |
| Gerekçe somut mu (hangi GTİP, hangi m.27 unsuru, hangi belge)? İlk derece mahkemeleri "yeterli ve açık tespit" içermeyen işlemleri iptal ediyor; Danıştay'ın aynı olaydaki sonucu tam metinde okunmalı `[incele]` | Danıştay 7. D. K.2024/1975 (ilk derece gerekçesi) |

## B. m.242 itirazını incelerken

1. Süre: tebliğden itibaren 15 gün; yanlış makama verilen itiraz süresinde sayılır (m.242/3).
2. **30 gün içinde** karara bağla ve tebliğ et (m.242/2); cevapsız bırakma zımni ret davası ve yargılama gideri riski yaratır.
3. İtirazda uzlaşma talebi de var mı? Uzlaşma talebi itiraz süresini durdurur; uzlaşma sonuçlanmadan itirazı sonuçlandırma `[incele]`.
4. Kısmi kabulde yeniden düzenlenen kararlar için itiraz yolunu yeniden göster (Danıştay 7. D. K.2024/29 olayında yükümlü doğrudan dava açmıştı).
5. Ret kararında: işlemin yapıldığı yerdeki idari yargı mercii ve 30 günlük dava süresi (m.242/4; İYUK m.7).
6. Tahsil: itiraz ödeme süresini keser, karar tebliğiyle yeniden başlar (m.198/2).

## C. Uzlaşma komisyonunda

1. Yetki: tutara göre bölge ya da merkezi komisyon (Yönetmelik m.9; sınır 18.06.2026'da değişti, başvuru tarihindeki metin uygulanır).
2. Kapsam: m.244/1-a, b, c; kaçakçılık bağlantısı yok (m.244/2).
3. Süre: başvuru tebliğden itibaren 15 gün; komisyon azami 30 günde sonuçlandırır (Yönetmelik m.18/1).
4. Görüşme ve tutanak (EK-5); tutanak kesin, dava açılamaz (m.244/4); çalışmalar gizli.
5. Uzlaşılan tutar 1 ayda ödenir, gecikme faizi uygulanır; peşin ödeme indirimi yok (m.244/5-6).

---

## Dava riski özeti (iç değerlendirme iskeleti)

```markdown
## İç değerlendirme — [karar no] — YÜKÜMLÜYE GÖNDERİLMEZ
| Risk | Bulgu | Düzeltme imkânı | Önem |
| Zamanaşımı (m.197/2) | | | 🔴/🟢 |
| Gerekçe ve somut tespit | | | |
| Ceza bendi | | | |
| BTB/BMB, m.198/4 | | | |
| Emsal Danıştay kararları (son 3 yıl) | | | |
### Öneri: kararı koru / kısmen kaldır / uzlaşmaya uygun
```

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "4458" law_type: "Kanun" article_no: "181" | "197" | "198" | "232" | "242" | "244"
legal_get_statute_article law_no: "15261" article_no: "9" | "18"
legal_search_cases mahkeme: "danistay" sorgu: "<uyuşmazlık> gümrük ek tahakkuk iptal" tarih_baslangic: "2023-01-01"
```

---

## Sık hatalar

- 🔴 İtirazı 30 günde sonuçlandırmamak.
- 🟠 Vergi ile cezayı ayrı zamanlarda tebliğ etmek (m.232/1).
- 🟠 Eşya gözetimdeyken m.238/1-a'nın iki kat cezasını uygulamak.
- 🟡 Kararda itiraz ve uzlaşma yolunu göstermemek.

---
