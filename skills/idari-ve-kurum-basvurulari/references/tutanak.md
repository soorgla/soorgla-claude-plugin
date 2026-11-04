# Tutanak (olay, tespit, teslim-tesellüm, toplantı)

Bir olayın, durumun ya da işlemin birden fazla kişi tarafından görüldüğünü ve kayda geçirildiğini gösteren belge. Kamu görevlisi, işyeri yöneticisi ya da site yönetimi gibi kişilerce tutulabilir. Süreye bağlı değildir ama **olaya en yakın zamanda** tutulması ispat değerini artırır.

**Bu beceride en önemli kural:** tutanağa yalnızca kullanıcının **gördüğünü/yaptığını söylediği** olgular yazılır. Model olgu tamamlamaz, yorum katmaz, "tespit edilmiştir" diye görülmemiş bir şeyi kayda geçirmez. Eksik olgu `[___]` kalır.

---

## Hukuki çerçeve (dikkat)

- Genel bir "tutanak kanunu" yoktur; tutanağın şekli ve ispat gücü **hangi alanda** kullanılacağına göre değişir. Kullanıcıya sor: iş hukuku (işçinin devamsızlığı, disiplin), idari denetim (imar, zabıta), kamu malı teslimi, kaza, toplantı?
  - İşyerinde devamsızlık/disiplin tutanağı → `is-hukuku` becerisi (`../../is-hukuku/references/ic-sorusturma.md`, `../../is-hukuku/references/fesih-oncesi-kontrol.md`) — tutanak oradaki usulle uyumlu olmalı.
  - İmar, zabıta, vergi yoklama gibi kanunla düzenlenmiş tespit tutanakları → ilgili özel mevzuatın zorunlu unsurları çekilmeden yazma `[incele]`.
  - Kolluk ve suç tespiti → kapsam dışı; yalnızca işaret.
- Kamu görevlisinin düzenlediği tutanakta **gerçeğe aykırı içerik** ceza sorumluluğu doğurabilir.  Bu yüzden metne yorum değil olgu yaz.
- Elektronik ortamda hazırlanan **rapor veya benzeri belge** sorumlu yetkililerce güvenli e-imzayla imzalanır; fiziksel ortamda son sayfa imzalanır, önceki sayfalar imzalanır ya da paraflanır. Kamu idaresi tutanağı bu kurala tabidir. 
- "En az iki imza" kuralı eski YAML'dan gelir; genel bir yasal zorunluluk olarak **yazma**. İspat açısından birden fazla tanık önerilir. Tutanağın türüne özgü mevzuat (ör. iş hukukunda devamsızlık tutanağı, tebligat, vergi yoklama) imza sayısı ya da şekil öngörebilir: tutanak türünü belirleyip `legal_search_statute_semantic` ile "<tür> tutanağı imza" araması yap; hüküm bulursan ona uy, bulamazsan "genel bir asgari imza sayısı doğrulanmadı" diye not düş. 

## Zorunlu unsurlar (eski şablondan; özel mevzuat yoksa iyi uygulama)

1. Başlık: türüne göre büyük harf, ortalı ("OLAY TUTANAĞI", "DURUM TESPİT TUTANAĞI", "TESLİM TESELLÜM TUTANAĞI", "TOPLANTI TUTANAĞI").
2. Giriş: **tarih, saat, yer** (açık adres) ve tutanağı düzenleyenlerin ad-soyad, unvanı; varsa muhatap.
3. Gelişme: olgusal, kronolojik, edilgen ve resmî dil ("görülmüştür", "beyan etmiştir", "teslim alınmıştır"); ölçülebilir veriler (adet, metre, seri no, marka/model, saat); muhatabın beyanı tırnak içinde, kendi sözleriyle.
4. Teslim-tesellümde: malzemenin cinsi, adedi, seri numarası, durumu (sağlam/arızalı).
5. Tarih: kamu idaresinin tutanağında tarih metnin bitiminde de yer alabilir. 
6. Sonuç: tutanağın kaç nüsha düzenlendiği, okunduğu, imzalandığı; **imzadan kaçınan** olursa bunun ayrıca kaydı.
7. İmzalar: düzenleyenler, tanıklar, muhatap.

## Görüşme soruları (eski `data_schema` alanlarından)

| Alan | Soru |
|---|---|
| `minute_type` | Tutanağın türü ve ne için kullanılacağı (iş, idari denetim, teslim, kaza, toplantı)? |
| `date_time` | Olayın/işlemin tarihi ve saati? Tutanak aynı anda mı tutuluyor, sonradan mı? |
| `location` | Açık yer/adres? |
| `participants` | Düzenleyenler, tanıklar ve muhatap: ad-soyad, unvan? |
| `incident_details` | Ne gördünüz, ne oldu? (kendi gözlemleriniz; duyduklarınızı ayrı söyleyin) |
| `evidence_items` | Fotoğraf, video, malzeme listesi, seri numaraları? |
| (yeni) | Muhatap bir beyanda bulundu mu? İmzalamayı kabul etti mi? |
| (yeni) | Kaç nüsha? |
| `conclusion_statement` | (Standart kapanış kullanılır.) |

## soorgla çağrıları

```
legal_get_statute_article  law_no: "2646"  law_type: "21"  article_no: "17"      # kamu idaresinde imza/paraf kuralı
legal_search_statute_semantic  sorgu: "<alan> tespit tutanağı düzenlenmesi zorunlu unsurlar"   # ör. imar, zabıta, vergi yoklama
legal_search_cases  mahkeme: "yargitay"  sorgu: "<ör. işçinin imzadan kaçındığı devamsızlık tutanağının ispat gücü>"  tarih_baslangic: "<son 3 yıl>"
```

## Belge iskeleti

```markdown
                         [TUTANAĞIN TÜRÜ — BÜYÜK HARF]

[gg.aa.yyyy] tarihinde saat [__:__] sularında, [açık adres / yer] adresinde, aşağıda adı soyadı ve unvanı
yazılı [düzenleyenler] tarafından işbu tutanak düzenlenmiştir.

OLAY / TESPİT KONUSU:
[Kronolojik, olgusal anlatım. Ölçülebilir veriler. Muhatabın beyanı: "…"]

TESPİT EDİLEN / TESLİM ALINAN MADDELER:
| Sıra | Cinsi | Adet | Seri no / marka-model | Durumu |
|---|---|---|---|---|

İşbu tutanak [___] nüsha olarak mahallinde düzenlenmiş, okunmuş ve doğruluğu anlaşılarak birlikte imza altına
alınmıştır. [Muhatap … tutanağı imzalamaktan kaçınmıştır.]

DÜZENLEYENLER                     TANIKLAR                     MUHATAP / TESLİM ALAN
[Ad SOYAD — unvan — imza]         [Ad SOYAD — imza]            [Ad SOYAD — imza]
```

## Sık hatalar

- 🔴 Görülmemiş bir olguyu "tespit edilmiştir" diye yazmak; olay sonrası duyulanı gözlem gibi kaydetmek.
- 🟠 Saat ve açık yer olmadan tutanak.
- 🟠 Muhatabın imzadan kaçınmasını kayda geçirmemek.
- 🟡 Yorum ve sıfat ("saygısızca", "kasten") kullanmak.

---

