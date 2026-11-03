# Form kütüphanesi ve EKAP dokümanı

KİK e-formları ve tip şartnameler: nereden bulunur, hangi numara/sürüm, araç yoksa ne yapılır, EKAP dosyaları nasıl okunur.

**Kaynak etiketi:** aşağıdaki tablo KİK'in kendi sitesinden (ihale.gov.tr Mevzuat → e-formlar, `GetEformsAra`) 2026-10-31'de indirilen 148 e-formun künyesinden (EformNo, ad, sürüm, KİK düzenleyici kararı) çıkarıldı. soorgla aracı değildir; her kullanımda `[KİK e-form listesi 2026-10-31 — doğrula]` etiketi taşır. Sürümler KİK kararlarıyla değişir; `legal_get_form` sonucu esas olur.

**Form bankası kimlikleri.** Aynı e-formlar soorgla form bankasında; kimlik `KIK-<EformNo>-<TÜR>` (TÜR: `MAL`, `YAPIM`, `HIZMET`, `DANISMANLIK`), ör. `KIK-KIK112-HIZMET` (e-şikâyet dilekçesi, hizmet). KİK'in "İlgili Doküman" formları `KIK-DOK<id>`, yönetmelik ekleri (tip idari şartname, tip sözleşme, standart formlar) `MEV-<mevzuat_no>-…` kimliğiyle. Aşağıdaki tablodaki numara + ihale türü = form bankası kimliği; çıktıda formu bu kimlikle an.

---

## 1. Araç akışı

1. `legal_search_forms` (`sorgu`, `ihale_turu`: mal / yapim / hizmet / danismanlik, `kategori`) → aday formlar (kimlik, ad, sürüm, karar tarihi/sayısı).
2. `legal_get_form` (`kimlik: "KIK-KIK0xx-<TÜR>"` ya da `MEV-…`, isteğe bağlı `tarih`) → alanlar, açıklamalar, dipnotlar.
3. Araç yanıt vermezse ya da hata dönerse:
   - (a) aşağıdaki tablodan numarayı ve sürümü al, form bankası kimliğini (`KIK-KIK0xx-<TÜR>`) yaz, `[KİK e-form listesi 2026-10-31 — doğrula]` etiketle;
   - (b) formun dayandığı yönetmelik maddesini çek: `legal_search_statute_semantic` ya da `legal_list_statute_articles` (`mevzuat_no` / `law_no`: `"12917"` mal, `"12918"` hizmet, `"12911"` danışmanlık, `"12916"` yapım; `sorgu`: belge adı, ör. "bilanço veya eşdeğer belgeler");
   - (c) kullanıcıdan EKAP'tan indirdiği dokümanı iste (idari şartname + ekleri, standart formlar) — ihaleye özgü düzen her zaman oradan;
   - (d) hiçbiri yoksa formun **adıyla** atıf yap, unsurları 4734 maddesinden kur, numarayı yazma ya da `[doğrula]`.
4. Tip idari şartname madde düzeni (örnek ihalelerde aynı): m.7 katılım ve yeterlik (7.1 belgeler, 7.2 ekonomik-mali, 7.3 mesleki-teknik, 7.4 diğer), m.13 açıklama, m.14 doküman değişikliği, m.22 tekliflerin hazırlanması, m.24 geçerlilik, m.26 geçici teminat, m.27 teminat değerleri, m.29 açılış ve değerlendirme, m.30 açıklık getirme, m.31 aşırı düşük, m.33 EAAT, m.34 karar, m.35 kesinleşen karar, m.36 davet, m.37 kesin teminat, m.43 fiyat farkı, m.45 diğer hususlar. Numaralar dokümana göre kayabilir; atıfı **o ihalenin** şartnamesinden yap.

## 2. E-form tablosu (belgeye göre)

Tür sütunu: KİK listesinde formun hangi tür(ler) altında yayımlandığı. "genel" formlar her tür altında ayrı kayıtla yayımlanır ve form bankasında türe göre ayrı kimlik alır (`KIK-KIK019-MAL`, `KIK-KIK019-HIZMET`); içerik türler arasında farklı olabileceğinden ihalenin türüne ait kimliği kullan.

| Belge | Form | Sürüm / karar | Tür |
|---|---|---|---|
| İhale onay belgesi | KİK001 | V1 · 2024/DK.D-133 | genel |
| Yaklaşık maliyet icmal tablosu | KİK002 | V1 | yapım |
| Teklif türünün belirlenmesi | KİK003 | V1 | yapım |
| İhale ilanı (e-ihale) | KİK004 | **V4 · 02.09.2026 2026/DK.D-278** | genel |
| Ön ilan · düzeltme ilanı · iptal ilanı | KİK005 · KİK006 · KİK007 | V1 | genel |
| Doküman indirmeye ve teklif vermeye davet | KİK008 | V1 | genel |
| Birim fiyat / götürü bedel / karma teklif mektubu | KİK009 · KİK010 · KİK011 | V1 | genel; KİK011 yapım |
| Birim fiyat teklif cetveli | KİK012 (mal-yapım-danışmanlık) · KİK013 (hizmet) | V1 | — |
| İhaleye katılım belgesi | KİK014 | **V10 · 27.02.2026 2026/DK.D-69** | genel |
| İş ortaklığı · konsorsiyum beyannamesi | KİK015 · KİK016 | V1 | genel |
| Tekliflerin açılmasına ilişkin tutanak · tebliği | KİK017 · KİK018 | V1 | genel |
| Son fiyat teklifine davet · e-eksiltmeye davet · numune talebi | KİK019 · KİK020 · KİK021 | V1 | genel |
| Aşırı düşük teklif açıklama talebi | KİK022 | **V4 · 22.10.2025 2025/DK.D-393** | genel |
| Aşırı düşük teklif açıklamasının gönderilmesi | KİK023 | V1 | genel |
| İhale komisyonu kararı | KİK024 (e-ihale) · KİK239 (fiziki) | V1 | genel |
| Kesinleşen ihale kararının tebliği | KİK025 | V1 | genel |
| Bütün tekliflerin reddiyle iptal · iptal kararının tebliği | KİK026 · KİK027 | V1 | genel |
| Sözleşmeye davet | KİK028 (e-ihale) · KİK221 (fiziki) | **V4 / V6 · 17.12.2025 2025/DK.D-465** | genel / yapım |
| Sözleşme belgelerinin EKAP üzerinden gönderilmesi | KİK029 | V1 | genel |
| Belgelerin fiziki olarak sunulması talebi | KİK030 | V1 | genel |
| Bilanço bilgileri · ciro bilgileri · OG ciro | KİK031 · KİK032 · KİK033 | V1 | genel |
| Ortaklık tespit · yurt dışı ortaklık tespit · ortaklık durum | KİK034 · KİK035 · KİK036 | V1 | genel; KİK036 yapım |
| Yerli malı şartı aranan makine-malzeme listesi | KİK037 | V1 | yapım |
| İstisna talebi (3/g) | KİK100 | V1 | hizmet |
| İhalelere katılmaktan yasaklama kararı | KİK101 | V1 | genel |
| Örnek analiz formatı | KİK102 | V1 | yapım |
| Malzemeli yemek sunumu hesap cetveli · örnek öğün menüsü | KİK103 · KİK103.1 | V2 / V1 · 2025/DK.D-393 | hizmet |
| Tek kaynaktan temin tutanağı | KİK104 | V1 | mal-hizmet |
| Maliyet · satış tutarı · maliyet-satış tutarı tespit tutanağı | KİK105 · KİK106 · KİK107 | V1 | genel |
| Stok tespit tutanağı | KİK108 | V1 | yapım |
| Birim fiyat cetveli örneği | KİK109 (mal) · KİK110, KİK111 (hizmet) | V1 | — |
| **E-şikâyet dilekçesi · idare kararı · e-itirazen şikâyet dilekçesi** | **KİK112 · KİK113 · KİK114** | V1 · 2024/DK.D-133 | genel |
| İş bitirme belgesi | KİK115 (mal) · KİK116 (hizmet) · KİK118 (yapım) · KİK127 (danışmanlık) | V1 | — |
| Alt yüklenici iş bitirme | KİK117 (hizmet) · KİK120 (yapım) · KİK131 (danışmanlık) | V1 | — |
| İş durum · denetleme · yönetme belgeleri | KİK119, KİK121-126 (yapım) · KİK128-135 (danışmanlık) | V1 | — |
| Geçici · kesin · avans teminat mektubu | KİK136 · KİK137 · KİK138 | **V5 · 12.03.2026 2026/DK.D-89** | genel |
| Kesin hesap · geçici kabul noksanları teminat mektubu | KİK139 · KİK140 | V3 / V2 · 2026/DK.D-89 | yapım |
| Geçici · kesin · avans kefalet senedi | KİK141 · KİK142 · KİK143 | V5 · 2026/DK.D-89 | genel |
| Kesin hesap · geçici kabul noksanları kefalet senedi | KİK144 · KİK145 | V3 / V2 | yapım |
| Kabul teklif belgesi ve tutanakları | KİK146-149 (yapım) · KİK150-151 (hizmet) · KİK152-153 (danışmanlık) | V1 | → `hakedis` / tür becerisi |
| Fiziki teklif ve ön yeterlik formları (zarf, tutanak, kısa liste, teknik/mali teklif değerlendirme, özgeçmiş, benzer iş tabloları) | KİK200-253 | V1 | danışmanlıkta çoğu → `ihale-danismanlik` |

Listede **olmayanlar** (serbest resmî yazı; `[doğrula — KİK'te form var mı]`): zeyilname, bilgi eksikliğinin tamamlatılması yazısı ve cevabı, KİK'e görüş/bilgi-belge yazısı, ivedi dava dilekçesi.

## 3. Tip şartnameler ve sözleşmeler

Tip idari şartnameler, tip sözleşmeler ve standart formlar **uygulama yönetmeliklerinin ekleridir** (Yapım 12916, Mal 12917, Hizmet 12918, Danışmanlık 12911, Çerçeve Anlaşma 12919). soorgla mevzuat aracında ekler madde olarak yok; KİK sitesinde yönetmelik ekleriyle birlikte `.zip` olarak yayımlanıyor (yerel indirme: `kik_mevzuat/` — depoda değil). Yapım Yönetmeliği'nin KİK kopyası 13.05.2026 değişikliğini içeriyor; mevzuat.gov.tr kopyası daha eski. Form bankasında bu ekler `MEV-<mevzuat_no>-…` kimliğiyle yer alacak; KİK sürümlerinin aynı kimliğe bağlanması henüz kararlaştırılmadı. **Tip şartname adı ve ek numarasını kullanıcının EKAP dokümanından** ya da `legal_get_form` sonucundan al; ezberden "Ek-__" yazma `[doğrula]`.

## 4. EKAP dosyalarını okuma

- EKAP'tan inen `.doc` dosyaları çoğu zaman **gerçek Word değil, Word-HTML**'dir (karakter kümesi ISO-8859-9 / Windows-1254). Tika ve docx okuyucular 422/hata verebilir. Yol: dosyayı HTML olarak aç, `charset` meta etiketine bak, `iso-8859-9` ile çöz, etiketleri ayıkla. Türkçe karakter bozuksa (Ý, Þ, Ð) kodlamayı yanlış seçmişsindir.
- KİK sitesinden inen e-form `.doc` adıyla gelip içi `.docx` (zip) olabilir; önce zip mi diye bak.
- Taranmış PDF (ör. hizmet örneğinde teknik şartname) metin vermez → OCR gerekir; okunamayan sayfayı **Okunan** satırına yaz, içeriğini tahmin etme (ORTAK-KURALLAR.md §10).
- İhale CD'si / doküman seti uzunsa uzun belge protokolü: `../../tablolu-belge-incelemesi/references/uzun-belge-protokolu.md`.
- Örnek dokümanlar yalnız **biçim referansıdır**: içlerindeki kişi adları, imzacılar, idare IBAN'ı, telefon ve e-posta taslağa taşınmaz.
