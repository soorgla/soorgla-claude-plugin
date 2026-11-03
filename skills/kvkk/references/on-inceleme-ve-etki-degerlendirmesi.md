# Yeni faaliyetin ön incelemesi ve etki değerlendirmesi

## Ne zaman kullanılır
- "Bu özelliği yapabilir miyiz?", "yüz tanıma ile giriş kuracağız", "çalışanların e-postalarını inceleyeceğiz", "müşteri verisini yapay zekâ modeline vereceğiz", "konum takibi", "yeni CRM/tedarikçi".
- Etki değerlendirmesi (upstream'de PIA/DPIA) isteniyor.

KVKK'da GDPR m.35 gibi **genel bir zorunlu etki değerlendirmesi hükmü yoktur**. `[model bilgisi — doğrulayın]` Yine de yüksek riskli faaliyetlerde (özel nitelikli veri, çalışan izleme, profil çıkarma, yeni teknoloji, çocuk verisi) yazılı bir değerlendirme, m.4 ölçülülük ilkesini ve m.12 tedbirlerini ispat için en iyi araçtır ve Kurul ilke kararları bu türden bir ölçülülük değerlendirmesi beklemektedir. Sektörel mevzuat ayrıca risk analizi isteyebilir `[incele]`.

---

## Adım 1 — Hızlı sınıflama (upstream use-case-triage)

Dört sonuçtan biri:
- **DEVAM** — standart tedbirlerle yapılabilir; tek paragraflık dosya notu yaz.
- **DEĞERLENDİRME GEREKİR** — yazılı ön inceleme/etki değerlendirmesi, sonra karar.
- **YÜKSEK RİSK** — özel nitelikli veri, çalışan izleme, büyük ölçekli profil, çocuk verisi, yurt dışı aktarım + yeni teknoloji; avukat ve üst yönetim onayı.
- **DUR** — hukuki sebep yok ya da aydınlatma metniyle/taahhütlerle doğrudan çelişiyor; tasarım değişmeden ilerlenmez. Yol yoksa "yol yok" de.

Önce faaliyeti netleştir (aşağıdaki görüşme soruları). "Yeni özellik" sınıflama için yeterli değildir.

**Uç durumlar (upstream'den):** "anonim" demek DEVAM sonucu doğurmaz — yeniden kimliklendirme riskini sor (m.3/1-b tanımı "başka verilerle eşleştirilerek dahi" der); "zaten benzerini yapıyoruz" değerlendirmeden muaf tutmaz; "pilot" da gerçek veriyle yapılıyorsa aynı kurallara tabidir; "tedarikçi hallediyor" — amaç ve vasıtayı siz belirliyorsanız veri sorumlususunuz; türetilmiş/tahmini veriler (skor, segment) de kişisel veridir.

---

## Kontrol listesi — etki değerlendirmesi

1. **Faaliyetin tanımı**: ne, neden, hangi alanlar (tek tek), yeni toplama mı mevcut verinin yeni amaçla kullanımı mı? Yeni amaç → yeni aydınlatma.
2. **Hukuki sebep** her amaç için (m.5/2, m.6/3). Meşru menfaate dayanılıyorsa denge testi yazılı olmalı: menfaat, zorunluluk, ilgili kişinin temel hak ve özgürlüklerine etki.
3. **Genel ilkeler** (m.4): amaçla bağlantılı, sınırlı, ölçülü; gerekli süre kadar saklama.
4. **Daha az müdahaleci yol var mı?** (kademelilik) — örn. biyometrik yerine kart/şifre; içerik yerine trafik/log denetimi; teknik engelleme (filtre) mümkünse genel denetim hakkı doğmaz.
5. **Çalışan verisi**:
   - Açık rıza, işçi–işveren güç dengesizliği nedeniyle kural olarak birincil dayanak değildir; özgür irade somut olayda ayrıca değerlendirilir.
   - Kurumsal e-posta denetimi: yalnız trafik/log incelemesi de veri işlemedir; iş amaçlı/özel kullanım ayrımı; önceden, somut aydınlatma (genel "e-postalar denetlenebilir" bildirimi yetmez); içerik denetimi yalnız somut şüphede ve iddiayla sınırlı; gizli ve ayrım gözetmeyen izleme hukuka aykırı; erişim yetkisi sınırlı ve kayıtlı; iş ilişkisi bitince hesabın kapatılması. İç soruşturma bağlamı → `../../is-hukuku/references/ic-sorusturma.md`.
   - Biyometrik mesai takibi: biyometrik veri özel niteliklidir; ölçülülük ve alternatif yöntem şartı.
   - Sendika üyeliği özel nitelikli veridir.
6. **Özel nitelikli veri**: m.6/3 şartı + Kurulun yeterli önlemleri.
7. **Otomatik karar ve profil**: münhasıran otomatik analiz kişi aleyhine sonuç doğurabiliyorsa itiraz hakkı (m.11/1-g) için süreç; Kurul araç kiralama sektöründe profilleme sonucu olumsuz karara dikkat çekmiştir.
8. **Yapay zekâ**: eğitim verisi olarak kişisel veri kullanımı ayrı amaçtır; tedarikçinin veriyi kendi modelini eğitmek için kullanması veri işleyen rolünü aşar → `veri-isleme-sozlesmesi.md`. Kurumun üretken yapay zekâ rehberi için `[model bilgisi — doğrulayın]`.
9. **Veri akışı**: toplama → saklama (ülke, şifreleme) → erişim (kim) → aktarım (alıcı, DPA) → saklama süresi ve imha.
10. **Yurt dışı** → `yurt-disi-aktarim.md`.
11. **Aydınlatma metni ve VERBİS tutarlılığı**: yeni veri kategorisi, amaç ya da alıcı varsa metin ve kayıt güncellenmeden başlatma. Doğrudan çelişki = DUR. → `aydinlatma-ve-acik-riza.md`, `uyum-denetimi-ve-verbis.md`.
12. **İlgili kişi hakları**: erişim, düzeltme, silme, itiraz bu yeni veri için işletilebiliyor mu?
13. **Riskler** — somut ve tasarıma bağlı yaz; 2-5 gerçek risk, 15 dolgu risk değil:
    | Kötü | Neden kötü | İyi |
    |---|---|---|
    | "Veri sızıntısı" | Her şeye uyar | "Destek ekibi yönetim panelinden konum geçmişini kayıt tutulmadan görebiliyor; içeriden biri kullanıcıyı izleyebilir" |
    | "KVKK'ya aykırılık" | Döngüsel | "Pazarlama izni olmayanlara da gidiyor, çünkü bu akışta İYS ret kaydı kontrol edilmiyor" |

---

## Görüşme soruları (ürün/İK ekibine — sohbet hâlinde)

| Alan | Soru |
|---|---|
| Ne ve neden | Özellik/süreç nedir, hangi sorunu çözüyor? |
| Veri | Hangi alanlar tek tek? Yeni mi toplanıyor? Özel nitelikli var mı? |
| Kişiler | Müşteri, çalışan, aday, çocuk, ziyaretçi? |
| İşlem | Saklama, analiz, paylaşım, otomatik karar, profil? |
| Erişim | Şirket içinde kim görecek? Log tutuluyor mu? |
| Üçüncü taraflar | Tedarikçi, iş ortağı, analitik; nerede? |
| Süre | Ne kadar saklanacak, nasıl silinecek? |
| Beklenti | Kişi bunun yapıldığını bilse şaşırır mı? Vazgeçme imkânı olmalı mı? |
| Alternatif | Aynı amaca daha az veriyle ulaşılabilir mi? |

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "6698" article_no: "3" | "4" | "5" | "6" | "11" | "12"
legal_search_official_gazette query: "Kişisel Verileri Koruma Kurulunun" search_in: "title" sort_by: "date_desc"
legal_get_official_gazette_document url: "<2026/921 biyometrik; 2026/2035 e-posta denetimi>"
legal_search_admin_guidance sorgu: "Kişisel Verileri Koruma Kurulunun kararı <faaliyet: kamera, konum, biyometrik, profilleme>" kurum: "Kişisel Verileri Koruma Kurulu" tarih_baslangic: "<son 3 yıl>"
legal_search_cases sorgu: "<işyeri kamera / e-posta denetimi / biyometrik> kişisel veri" mahkeme: "anayasa"
legal_search_cases sorgu: "<aynı>" mahkeme: "yargitay" tarih_baslangic: "<son 3 yıl>"
```

---

## Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …

# Etki Değerlendirmesi: [faaliyet]
**Hazırlayan:** … | **Tarih:** … | **Durum:** TASLAK
**Sınıflama:** [DEVAM / DEĞERLENDİRME GEREKİR / YÜKSEK RİSK / DUR] — [tek cümle neden]
**Önceki inceleme:** [var — tarih, sonucu / yok — ilk değerlendirme]

## 1. Faaliyetin tanımı
## 2. Hukuki sebep
| Amaç | Şart (m.5/2-… / m.6/3-…) | Not (denge testi / rıza nasıl alınıyor) |
## 3. Veri akışı (toplama, saklama, erişim, aktarım, saklama süresi)
## 4. Aydınlatma metni ve VERBİS tutarlılığı
| Taahhüt | Tutarlı mı | Not |
## 5. Riskler ve tedbirler
| # | Risk | Olasılık | Etki | Tedbir | Durum (var/planlı/açık) | Sorumlu |
**Kalan risk:** …
## 6. İlgili kişi hakları
| Hak | Kullanılabilir mi | Nasıl |
## 7. Öneri
[ONAY / ŞARTLI ONAY / DEĞİŞİKLİK GEREKLİ / RED]
Şartlar: - [ ] [somut iş — sorumlu — başlamadan önce]
**Onaylayan:** [ad, tarih] (bu beceri onay vermez)
```

---

## Sık hatalar
- Çalışan verisinde açık rızayı ana dayanak yapmak.
- "Anonim" diye değerlendirmeyi atlamak.
- Genel ve soyut riskler yazmak.
- Daha az müdahaleci alternatifleri tartışmamak.
- Aydınlatma metnini güncellemeden yeni amaca başlamak.
- Tedarikçinin veriyi kendi yapay zekâsını eğitmekte kullanmasını gözden kaçırmak.
