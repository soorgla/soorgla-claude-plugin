# OHAL / KHK ile kamu görevinden çıkarma ve iade (kısa)

## Ne zaman kullanılır
- 2016-2018 olağanüstü hal döneminde KHK ile kamu görevinden çıkarılan kişinin OHAL İşlemleri İnceleme Komisyonu kararı, ardından açılan dava, iade sonrası haklar.
- İade edilen personelin atanması, göreve başlama süresi, mali haklar.

Bu dosya **kısa bir yönlendirme**dir: dosyaların büyük bölümü yargı aşamasındadır; esas analiz idari dava (iptal) ve AYM/AİHM sürecidir. Ceza yargılaması boyutu (örgüt üyeliği) → `../../ceza-ve-infaz-dilekce/SKILL.md`; AYM/AİHM → `../../aym-aihm-basvuru/SKILL.md`; idari dava dilekçesi → `../../idare-davalari-imar/references/idari-dava-dilekcesi.md`.

**Komisyonun güncel durumu:** Komisyon kanunun yürürlüğünden itibaren iki yıl görev yapar; Cumhurbaşkanı süreyi bitiminden itibaren **birer yıllık** sürelerle uzatabilir (7075 m.3/1). Son uzatma kararını ve Komisyonun 2026'da görevde olup olmadığını kesin bilgi gibi yazma: `legal_search_official_gazette` (`query: "Olağanüstü Hal İşlemleri İnceleme Komisyonu görev süresi"`, `document_type: "cumhurbaşkanı kararı"`, `sort_by: "date_desc"`) ile ara; bulamazsan `[ARAŞTIRMA GEREKLİ: Komisyonun güncel görev süresi]` yaz ve kullanıcıdan resmî duyuruyu iste. Başvuru süresi kaçmışsa (KHK'nın yayımından ya da başvuru alma tarihinden itibaren 60 gün, m.7/3) başvuru işleme alınmaz.

---

## Kurallar ve dayanakları

| Konu | Kural | Dayanak |
|---|---|---|
| Komisyon kararına karşı dava | HSK'nın belirlediği **Ankara idare mahkemelerinde**, ilgilinin **en son görev yaptığı kurum** aleyhine iptal davası; Cumhurbaşkanlığı ve Komisyon hasım gösterilmez | 7075 m.11/1 |
| Hâkim/savcılar (667 KHK m.3, 6749 m.3) | Kararın kesinleşmesinden itibaren **60 gün** içinde ilk derece olarak **Danıştay**'da dava | 7075 m.11/2 |
| Dava süresi (genel) | Özel süre yoksa 2577 m.7 — 60 gün | `[incele]` |
| Başvurunun kabulü | Karar kadronun bulunduğu kuruma (öğretim elemanında YÖK'e) bildirilir; eski kadro veya pozisyona atanma esas; kurumlar 30 gün içinde atama | 7075 m.10/1 |
| Göreve başlama | Atama emrinin tebliğini takip eden **10 gün** içinde göreve başlamayanın atanma hakkı düşer | 7075 m.10/1 🔴 |
| Mali haklar | Çıkarılma tarihini takip eden aybaşından göreve başlama tarihine kadar mali ve sosyal haklar ödenir | 7075 m.10/1 |
| AYM iptalleri | m.10/1'in bazı cümleleri (E.2018/159 K.2019/93; E.2018/137 K.2022/86) ve m.10/A iptal edildi | |
| 657 m.125/E-l | Terör örgütleriyle eylem birliği, yardım, propaganda → çıkarma cezası (KHK-676, 7070) | 657 m.125/E-l |

---

## Kontrol listesi
1. İşlem: KHK eki liste mi, Komisyon ret kararı mı, iade sonrası atama mı?
2. Komisyon kararının tebliğ tarihi → dava süresi; doğru mahkeme (Ankara, HSK'nın belirlediği) ve doğru hasım (son kurum).
3. İade edildiyse: atama emrinin tebliği → 10 gün içinde göreve başlama 🔴.
4. Mali haklar hesabı (aybaşı kuralı); ödenmeyen kalemler için idareye başvuru (İYUK m.10).
5. Paralel ceza davası sonucu (beraat/kovuşturmaya yer olmadığı) ve etkisi `[incele]`.
6. AYM bireysel başvuru ve AİHM süreleri → `aym-aihm-basvuru`.
7. Emsal: `legal_search_cases` (`sorgu: "OHAL İşlemleri İnceleme Komisyonu kararı iptal kamu görevinden çıkarma"`, `mahkeme: "danistay"` ve `"bam"`); 2026 tarihli kararlarda Danıştay **5. Daire** OHAL/KHK kaynaklı uyuşmazlıklara (ör. iade sonrası tazminat davalarında yetki) bakıyor; KHK ile çıkarmadan doğan maddi/manevi zarar davalarında da Ankara özel yetkili idare mahkemeleri yetkili, iade sonrası ödenmeyen mali haklarda ise İYUK m.33 kuralları uygulanıyor. İstinaf dairesini (Ankara BİM) kararın künyesinden oku, sabitleme.

## soorgla çağrıları
```
legal_list_statute_articles statute_id: 39527 include_content: true # 7075 (law_no 7075 bir üniversite yönetmeliğiyle çakışıyor)
legal_search_cases sorgu: "OHAL İşlemleri İnceleme Komisyonu başvurunun reddi iptal" mahkeme: "bam" tarih_baslangic: "<3 yıl önce>"
legal_search_cases sorgu: "<aynı>" mahkeme: "danistay"
legal_search_cases sorgu: "kanun hükmünde kararname ile kamu görevinden çıkarma" mahkeme: "anayasa"
```

**Araç uyarısı:** `law_no: "7075"` iki kayda çözülüyor (OHAL Komisyonu Kanunu ve Galatasaray Üniversitesi yönetmeliği); `statute_id: 39527` ya da `law_type: "Kanun"` ver.

## Sık hatalar
- Komisyon kararına karşı Komisyonu ya da Cumhurbaşkanlığını hasım göstermek.
- İade sonrası 10 günlük göreve başlama süresini kaçırmak.
- Daireyi eski YAML'dan sabitlemek.
