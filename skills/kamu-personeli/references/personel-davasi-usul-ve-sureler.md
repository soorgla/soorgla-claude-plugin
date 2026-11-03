# Personel işlemlerine karşı başvuru, dava yolu ve süreler

## Ne zaman kullanılır
- Her soru tipinin son adımı: "dava açabilir miyim, süre ne zaman doluyor, önce idareye mi başvurayım, yürütmeyi durdurma isteyebilir miyim?"
- Memurun idareden bir işlem talep etmesi (özlük hakkı, ödeme, göreve başlatılma) ve sessizlik.

**Sınır:** dava dilekçesinin metni → `../../idare-davalari-imar/references/idari-dava-dilekcesi.md` (İYUK m.3 zorunlu unsurları orada). İstinaf/temyiz → `../../kanun-yollari-dilekce/references/idari-istinaf-temyiz.md`. Bu dosya süre tablosunu, yolu ve devir özetini üretir.

---

## Süre tablosu

| Adım | Süre | Başlangıç | Dayanak |
|---|---|---|---|
| İptal / tam yargı davası (idare mahkemesi) | **60 gün** (özel kanunda ayrı süre yoksa) | Yazılı bildirimi izleyen gün | 2577 m.7/1-2 |
| İdareden işlem isteme; cevapsızlık | **30 gün** içinde cevap yoksa ret sayılır; 30 günün bitiminden itibaren dava süresi işler; kesin olmayan cevapta bekleme başvurudan itibaren **4 ayı** geçemez | Başvuru | 2577 m.10/2 |
| Üst makama başvuru (dava açmadan önce) | Dava süresi içinde yapılır, **işleyen süreyi durdurur**; **30 gün** cevapsızlık ret; ret ya da zımni retle süre kaldığı yerden işler (geçen süre hesaba katılır) | Başvuru | 2577 m.11 |
| Disiplin cezasına itiraz (disiplin kurulu / YDK) | **7 gün** | Tebliğ | 657 m.135 |
| 4483 soruşturma izni kararına itiraz | **10 gün** (dava değil, kesin karar) | Tebliğ | 4483 m.9 |
| İstinaf / temyiz | → `kanun-yollari-dilekce` | Tebliğ | 2577 m.45-46 (7589 ile değişti) |

**Eski bilgi uyarısı:** İYUK m.10 ve m.11'deki cevap süreleri **7331 sayılı Kanunla (RG 14.07.2021) altmış günden otuz güne** indirildi; m.10'daki azami bekleme altı aydan dört aya indi. 2021 öncesi kaynaklar ve eski şablonlar "60 gün cevapsızlık" der — bayattır. soorgla madde tarihçesi 2015'te kaldığı için bu değişikliği göstermez.

**İtiraz ile dava ilişkisi (disiplin):** 657 m.135 itirazı idari başvuru yoludur; itiraz edildiyse dava süresinin itiraz kararının tebliğinden mi başlayacağı, itiraz edilmeden doğrudan dava açılıp açılamayacağı içtihatla belirlenir `[incele]`. Güvenli yol: itiraz süresini (7 gün) kaçırmamak ve itiraz kararının tebliğinden itibaren 60 günü hesaplamak; itiraz merciinin 30 günlük karar süresini (m.135/3) aşması hâlinde İYUK m.10-11 kurallarını uygulamak. İtirazın zorunlu olup olmadığı ve sürenin başlangıcı konusunda içtihadı kesin bilgi gibi yazma: `legal_search_cases` (`mahkeme: "danistay"`, `sorgu: "disiplin cezasına itiraz edilmeden açılan dava süre 657 m.135"`) ile güncel kararı ara, tam metnini oku; bulamazsan `[ARAŞTIRMA GEREKLİ: disiplin itirazı ve dava süresi]` yaz ve güvenli yolu öner. Başvuru mercii ve süresi gösterilmeden tebliğ edilen işlem dava süresini başlatmaz (Anayasa m.40/2).

`legal_calculate_deadline` dava açma (`iyuk_lawsuit`), zımni ret (`iyuk_implicit_rejection_application`, `iyuk_implicit_rejection_waiting`), istinaf/temyiz (`iyuk_appeal`, `iyuk_cassation`) sürelerini hesaplar; sonucu madde metniyle karşılaştır. Kodu olmayan süreleri elle hesapla, son günü `legal_check_holiday` ile kontrol et, `[doğrula]`.

---

## Görev, tek hâkim ve kanun yolu (7589 sonrası)

- Personel işlemleri **idare mahkemesinde** görülür; Danıştay ilk derece görevi istisnaidir (ör. 7075 m.11/2'deki hâkim/savcılar).
- 7589 (RG 31.07.2026) ile 2576 m.7/1 yeniden yazıldı. **Tek hâkimle** görülenler arasında: parasal sınırı aşmayan iptal ve tam yargı davaları; **kamu görevlileri hakkındaki geçici görevlendirme, yolluk, lojman ve izin işlemleri**; **kamu görevlilerine verilen uyarma cezası**. Parasal sınırı metinden çek, beceriye yazma.
- 7589 ile 2577 m.46'ya eklenen ikinci fıkra: BİM'in kaldırma üzerine yeniden verdiği kararlar 30 gün içinde temyiz edilebilir; ancak **tek hâkimle görülen davalarda** temyiz yolu yoktur. Yürürlük: her iki değişiklik yayımı tarihinde (31.07.2026). Geçiş: 2576 m.7 değişiklikleri (tek hâkim) **31.07.2026'dan sonra açılan davalara** uygulanır; 2577 m.46 değişiklikleri bu tarihten sonra **BİM'lerce verilen kararlara** uygulanır, öncekilere eski hükümler.
- **Yetkili mahkeme:** kamu görevlileriyle ilgili davalarda yetki kuralı İYUK'ta özel olarak düzenlenir (görev yeri esası): atama ve nakilde yeni ya da eski görev yeri; görevine son verme, emeklilik ve görevden uzaklaştırmada son görev yeri; ilişiği kesmeyen disiplin cezaları ile özlük ve parasal haklarda görevli bulunulan yer idare mahkemesi (2577 m.33).
- **Yürütmenin durdurulması:** telafisi güç veya imkânsız zarar **ve** idari işlemin açıkça hukuka aykırı olması koşulları birlikte aranır; gerekçeli istenir; atama, nakil, görev/unvan değişikliği ve görevlendirmeler "uygulanmakla etkisi tükenecek işlem" sayılmaz, yani savunma alınmadan YD verilmez; YD kararına tebliğden itibaren 7 gün içinde bir kez itiraz (2577 m.27/2, 27/7). Personel işlerinde güçlü zarar argümanları: il dışı atama (aile, sağlık, çocuğun eğitimi), görevden uzaklaştırma, çıkarma, aylıktan kesinti.

---

## Kontrol listesi — dava öncesi

1. İşlem **kesin ve yürütülmesi gereken** bir işlem mi (hazırlık işlemi, görüş, soruşturma oluru genellikle değil) `[incele]`?
2. Tebliğ tarihi ve şekli (e-Devlet/KEP/elden) — tablo.
3. Önce idari başvuru yolu var mı (657 m.135 itiraz)? İsteğe bağlı üst makam başvurusu (İYUK m.11) süreyi durdurur — yararı ve riski.
4. İptal mi, tam yargı mı, ikisi birlikte mi (mali kayıp: kesilen aylık, ödenmeyen yolluk)?
5. Hasım: işlemi yapan idare (bakanlık, belediye, üniversite); OHAL dosyasında son kurum.
6. Yetkili ve görevli mahkeme; tek hâkim mi kurul mu.
7. Yürütmenin durdurulması gerekçesi.
8. Harç: `legal_calculate_court_fee` (idari yargı harç türü tanınmazsa `legal_get_social_parameters`) `[doğrula]`.
9. Devir özeti hazır mı (aşağıda).

## İdareye başvuru iskeleti (İYUK m.10 — özlük hakkı talebi)

```markdown
[TASLAK — gözden geçirin]

[KURUM] [BİRİM] BAŞKANLIĞINA / MÜDÜRLÜĞÜNE

Başvuran : [ad soyad, T.C. kimlik no, unvan, sicil no, görev yeri]
Konu : [kademe ilerlemesinin uygulanması / … ödemesinin yapılması / göreve başlatılmam] talebi

Açıklama : [olgu, tarih, hak doğuran durum, dayanak madde]
Talep : [işlemin yapılması / farkın ödenmesi] ve sonucun tarafıma yazılı olarak bildirilmesi.
Ek : [belgeler]
[tarih, imza]
```
Başvuru tarihini ispatlanabilir biçimde kaydet (evrak kayıt numarası, KEP). 30 gün cevapsızlık → ret; dava süresi işlemeye başlar.

---

## Devir özeti (→ idare-davalari-imar)

```markdown
- Statü / kurum: [memur 4/A | sözleşmeli 4/B | …], [kurum]
- Taraf: davacı [memur], davalı [idare]
- Dava konusu işlem(ler): [tarih, sayı, makam] — tebliğ: [tarih, şekil]
- Önceki başvurular: [657 m.135 itiraz / İYUK m.10-11] — tarih ve sonuç
- Süre tablosu: [son gün, hesap, tatil kontrolü]
- Beş unsur bulguları: yetki · şekil · sebep · konu · maksat (her biri önem işaretli)
- Çekilmiş madde ve karar künyeleri (etiketleriyle)
- Yürütmenin durdurulması: telafisi güç zarar [olgular] + açık hukuka aykırılık [gerekçe]
- Tam yargı kalemi: [kesilen aylık, yolluk, manevi]
- Tek hâkim mi: [evet/hayır — 2576 m.7]
- Açık sorular
```

---

## Sık hatalar
- İYUK m.10-11 cevap süresini eski 60 günle hesaplamak (7331 sonrası 30 gün).
- Üst makama başvurunun süreyi "baştan başlattığını" sanmak (durdurur; geçen süre hesaba katılır).
- Soruşturma oluru ya da savunma istem yazısına dava açmak (hazırlık işlemi) `[incele]`.
- Tek hâkimle görülen uyarma cezası davasında istinaf sonrası temyiz yolunu varsaymak.
- Yürütmenin durdurulmasını gerekçesiz, kalıp cümleyle istemek.
