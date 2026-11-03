# Hükmün açıklanmasının geri bırakılması (HAGB): beyan, zarar giderme, kanun yolu

## Büyük değişiklik — önce bunu oku

Eski YAML'ın adı "HAGB Kabul Beyanı" idi ve iki temel iddiası artık **yanlış**:

| Eski iddia | Güncel durum | Kanıt |
|---|---|---|
| "HAGB için sanığın kabulü şarttır (CMK 231/6)" | **Kabul şartı 7499 s. Kanunla kaldırıldı.** 1.6.2024 ve sonrasında verilen HAGB kararlarında sanığın kabulü aranmaz; **1.6.2024'ten önce verilen** HAGB kararlarında kabul şartı aranmaya devam eder (7499 geçici m.6/2-d). | Yargıtay 3. CD E.2024/23139 K.2025/15851 (27.05.2025) — tam metin okundu; `legal_get_statute_article` 5271 m.231/6 güncel metinde kabul cümlesi yok |
| "HAGB'ye yalnız itiraz edilebilir, istinaf/temyiz edilemez" | **HAGB kararına karşı istinaf** yolu açık (272/3 saklı); BAM ya da Yargıtay ilk derece sıfatıyla verdiyse temyiz; usul ve esas yönünden incelenir (CMK 231/12). | `legal_get_statute_article` 5271 m.231/12 (Değişik: 2/3/2024-7499/15; 16/7/2026-7589/15) ; 7499 geçici m.6: kanun yolu değişikliği 1/6/2024 ve sonrası HAGB kararlarına uygulanır |

Madde 7589 s. Kanunla (RG 31.07.2026) yeniden yazıldı; güncel metni her seferinde çek.

**Sonuç:** "HAGB kabul dilekçesi" artık rutin bir zorunluluk değildir. Bu dosya üç işe yarar:
1. **HAGB talebi / beyanı** (sanık lehe hüküm olarak HAGB istiyor; zarar giderme beyanı ve şartların varlığı),
2. **HAGB istemiyorum beyanı** — 1.6.2024'ten önce verilmiş kararlarda hukuki sonuç doğurur; sonrasında yalnız beyan niteliğindedir ve sanığı korumaz `[incele]`,
3. **HAGB kararına karşı istinaf** (beraat isteyen sanık için asıl yol) — istinaf dilekçesinin gövdesi `kanun-yollari-dilekce` becerisine aittir; burada süre ve yol belirlenir.

## Şartlar ve sonuçlar (CMK 231)
- Hükmolunan ceza **iki yıl veya daha az hapis ya da adli para cezası** (231/5).
- Sanığın daha önce kasıtlı suçtan mahkûm olmaması; yeniden suç işlemeyeceği kanaati; **zararın tamamen giderilmesi** (231/6-a, b, c).
- Zarar derhal giderilemiyorsa **denetim süresince aylık taksitlerle** ödeme koşuluyla HAGB verilebilir (231/9).
- HAGB verilen hükümde hapis ertelenemez, seçenek yaptırıma çevrilemez (231/7).
- **Beş yıl denetim süresi**; bu sürede kasıtlı suç nedeniyle yeniden HAGB verilemez; bir yılı aşmayan denetimli serbestlik yükümlülükleri; dava zamanaşımı durur (231/8).
- Denetim süresi kurallara uygun geçerse hüküm ortadan kalkar, **davanın düşmesi** kararı verilir (231/10); ihlalde hüküm açıklanır ya da yeni hüküm kurulur, buna itiraz edilebilir (231/11).
- HAGB kararı özel sisteme kaydedilir; yalnız soruşturma/kovuşturma bağlantılı amaçla kullanılır (231/13) — "sabıka kaydına hiç işlenmez" demek yanlış, **adli sicilden ayrı bir kayıttır**.
- İşkence, eziyet ve kamu görevlisinin Anayasa m.17 kapsamında kötü muamele sayılan suçlarında HAGB **uygulanmaz** (231/14).
- HAGB kararı memuriyet, avukatlık gibi mesleklerde ayrı sonuçlar doğurabilir (ör. 7571 ile Av.K. 135'te HAGB disiplin sebebi sayıldı). Kullanıcının mesleğini sor `[incele]`.

## Süre
- HAGB kararına karşı istinaf: **iki hafta**, hükmün gerekçesiyle tebliğinden (CMK 273/1) → `legal_calculate_deadline(kural_kodu: "cmk_appeal")`.
- 1.6.2024'ten önce verilmiş HAGB kararı: eski rejimde itiraz yolu (CMK 268 — güncel metin iki hafta); hangi sürenin uygulanacağını karar tarihine göre belirle `[incele]`.
- HAGB beyanı/talebi: hükümden önce, esas hakkında savunma ile birlikte.

## Görüşme soruları
1. Mahkeme, esas no, sanık, suç `[___]`
2. Hüküm verildi mi? Verildiyse tarihi, HAGB kararı var mı, gerekçeli karar ne zaman tebliğ edildi?
3. Sanık HAGB istiyor mu, yoksa beraat için kanun yoluna mı gitmek istiyor?
4. Mağdurun ya da kamunun zararı var mı; giderildi mi; taksit planı mümkün mü?
5. Sanığın önceki kasıtlı suçtan mahkûmiyeti var mı? Başka HAGB denetim süresi devam ediyor mu?
6. Sanığın mesleği (kamu görevlisi, avukat, öğretmen, güvenlik görevlisi vb.)?

## soorgla adımları
```
legal_get_statute_article law_no: "5271" article_no: "231" | "273" | "272"
legal_search_official_gazette query: "Ceza Muhakemesi Kanunu" document_type: "kanun" search_in: "title" sort_by: "date_desc"
legal_search_cases mahkeme: "yargitay"
    sorgu: "7499 sayılı Kanun sonrası hükmün açıklanmasının geri bırakılması kararına karşı istinaf incelemesi"
    tarih_baslangic: "2024-06-01"
legal_get_case_document belge_id: <seçilen karar> # karar tarihinin 1.6.2024 öncesi/sonrası olduğuna dikkat
```

## Dilekçe iskeleti — HAGB talebi ve zarar giderme beyanı
```
[İL] [N]. ASLİYE CEZA MAHKEMESİNE
Esas No : [___]
SANIK : [___] MÜDAFİİ: [___]
SUÇ : [___]
KONU : Öncelikle beraat talebimiz saklı kalmak kaydıyla, mahkûmiyet hâlinde CMK 231 uyarınca
          hükmün açıklanmasının geri bırakılması talebimiz ve zarar giderme beyanımızdır.
AÇIKLAMALAR
1. Beraat talebimiz [esas savunmaya atıf].
2. Sanık daha önce kasıtlı bir suçtan mahkûm olmamıştır (adli sicil kaydı [___]).
3. Zarar [tarih] tarihinde [tutar/şekil] ile giderilmiştir / denetim süresince aylık taksitlerle
   giderilmesi taahhüt edilmektedir (CMK 231/6-c, 231/9).
4. Sanığın kişilik özellikleri ve duruşmadaki tutumu yeniden suç işlemeyeceğini göstermektedir.
HUKUKİ NEDENLER: CMK m.231 [MCP'den çekilmiş]
SONUÇ VE İSTEM : Öncelikle BERAATE; aksi kanaatte HAGB kararı verilmesine karar verilmesini talep ederiz.
```

## Sık hatalar
- 🔴 "Kabul etmezsen HAGB verilemez" diye müvekkile güvence vermek (1.6.2024 sonrası kararlarda yanlış).
- 🔴 HAGB kararına itiraz dilekçesi yazmak; 1.6.2024 sonrası kararlarda yol **istinaf**tır.
- "Sabıka kaydına işlenmez, hiçbir sonucu yok" demek — ayrı sistemde kayıtlıdır; meslek mevzuatında sonuç doğurabilir.
- Zarar gidermeyi şart olarak anlatıp taksit imkânını (231/9) atlamak.
- 231/14 istisnalarını kontrol etmemek.
