# İstekli — doküman incelemesi, itiraz ve teklif hazırlama (aşama 2)

Dokümanı EKAP'tan indiren istekli olabilecek için: "Bu dokümanda bana engel bir aykırılık var mı, varsa süresinde nasıl itiraz ederim; yoksa teklifimi nasıl elenmeyecek şekilde hazırlarım?" Liste **örnek idari şartnamenin (İKN 2026/1998683) madde sırasıyla** kuruldu; başka dosyada aynı madde numaralarını ara (tip idari şartname yapısı aynıdır).

- **İstekli ne yapmalı:** açıklama talebi ve doküman şikâyeti **iki ayrı yoldur, sıra değildir**: açıklama talebi şikâyet süresini durdurmaz. Belirsizlikte açıklama talebi; aykırılık şüphesinde şikâyeti süresinde ver, gerekirse açıklama talebini paralel yap. Aynı anda teklifi "şartname düzeltilmezse" senaryosuna göre hazırla.
- **İdare neye dikkat:** aynı iddiaya gerekçeli cevap verebilecek mi? (`idare-hazirlik.md`)

---

## 0. Önce süre

- [ ] **İlk ilan tarihi**, doküman indirme tarihi ve ihale tarihi — üçü de zorunlu sorulur. Doküman şikâyeti: indirmeden itibaren 10 gün **ve** ihale tarihinden en geç 3 iş günü önce, hangisi önceyse. **İlana yansıyan hususlarda** (benzer iş tanımı, iş deneyimi oranı, yeterlik kriterleri, kalite belgeleri) süre indirmeden değil **ilk ilan tarihinden** işler; ilan eskiyse süre indirmeden önce dolmuş olabilir 🔴. `legal_calculate_deadline` `kik_complaint_before_tender` canlı ve 10 günü doğru döndürür; 3 iş günü sınırını hesaplamaz, onu `legal_check_holiday` ile elle say `[incele]`.
- [ ] Örnek: ihale 10.12.2026 (Perşembe). İhale günü sayılmadan geriye üç iş günü (09.12, 08.12, 07.12) sayılınca son gün **07.12.2026 Pazartesi**; 07.12 ve 10.12 iş günü. Son günün dahil olup olmadığı KİK uygulamasıyla teyit edilmeli `[incele]`. İndirme tarihi bilinmiyor `[OLGU GEREKLİ]`.
- [ ] Açıklama talebi: ihale tarihinden 20 gün öncesine kadar yazılı (4734 m.29; örnek m.13.1). Açıklama talebi şikâyet süresini **durdurmaz, uzatmaz**: 4734 m.55'te böyle bir hüküm yok; dokümana yönelik şikâyet süresi dokümanın alındığı (ilana yansıyanda ilk ilan) tarihte başlar. Çıktıda iki son günü **birlikte** göster: "Doküman şikâyeti son günü: … · Açıklama talebi son günü: …".
- [ ] Şikâyet → itirazen şikâyet zinciri, bedel ve dilekçe → `../../ihale-sikayet/SKILL.md`.

## 1. Madde 2-5: iş, tür, kapsam

- [ ] Tür hizmet mi, gerçekte mal mı? (kalem listesindeki parça değişimleri). Tür yanlışsa Mal Yönetmeliği kuralları (yerli malı, numune) gündeme gelir `[incele]`.
- [ ] "2 Kısım (31 Kalem)" (m.2.1-ç) ile "işin tamamı için teklif" (m.20.1) çelişkisi → açıklama talebi konusu 🟡.
- [ ] **Teknik şartname okunabildi mi?** Örnekte taranmış PDF, metin çıkmadı: teknik şartnameye dayanan her değerlendirme **varsayım**dır. OCR'lı metin ya da okunabilir sürüm iste; okunmadan "teknik şartnamede marka yönlendirmesi yok" deme 🟠.

## 2. Madde 7: katılım ve yeterlik

- [ ] 7.3.1 iş deneyimi: son 5 yıl, tek sözleşme, oran (örnek %25). Mevzuat aralığı %25-50 → oran yönünden itiraz zayıf.
- [ ] 7.3.1.1 **benzer iş**: kendi belgen tanıma giriyor mu? Girmiyorsa iddia: tanım ihale konusu işten dar / tek firmayı işaret ediyor / aynı teçhizat ve uzmanlığı gerektiren işleri dışlıyor (Hizmet Yön. m.28/1 rekabet ilkesi; m.3/1-a tanım; 4734 m.5). Emsal: KİK 2025/UH.I-296 — dar benzer iş, ihalenin iptali; KİK 2026/UH.I-567 — benzer iş ihale konusu üç ana kalemden yalnız birini kapsıyor, iptal. **Emsal uygulanabilirlik ölçütü:** bu emsaller yalnız tanım ihale konusu işten **dar** olduğunda işler. Tanım ihale konusuyla **aynı ya da daha genişse** (ör. "tren teker tornası ağır bakım işleri, torna bakım işleri" — ihale konusuyla aynı, ikinci ibareyle daha geniş) uygulanmaz; asıl soru belgenin tanıma girip girmediğidir → açıklama talebi `[incele]`. İddiaya **somut alternatif tanım** öner (ör. "her türlü raylı sistem aracı bakım tezgâhı ve CNC takım tezgâhı bakım-onarım işleri") — itirazen şikâyette yeni iddia eklenemediği için ilk şikâyette eksiksiz yaz.
- [ ] Belgede ihale konusu ya da benzer iş dışındaki işlerin tutarı sayılmaz; birden çok belge toplanmaz.
- [ ] Ortağın belgesi: %50'den fazla hisse + temsil yetkisi, en az bir yıl; ilk ilandan sonra düzenlenmiş ortaklık tespit belgesi.
- [ ] 7.3.3 kalite belgeleri: ISO 27001, ISO 20000-1, CE, ECM, üretici yetki belgesi — işle bağlantısı yoksa orantısızlık iddiası (m.28/1) 🟠. Yetki belgesi tek üreticiye (örnekte RAFAMET ve HOESCH tezgâhları var; "1 adet üreticiden" ibaresi hangisi?) bağlanıyorsa rekabet iddiası 🔴 `[incele]`. Yurt dışı belgede apostil ve yeminli tercüme (m.7.7.4-7.7.5) — süre ve maliyet planla.
- [ ] 7.2 ekonomik-mali yeterlik boş (bilanço ve ciro istenmemiş) ✅. İstenseydi: `bilanco_kontrol`, `is_hacmi_kontrol`; araç yoksa Hizmet Yön. m.35-36 ile elle.

## 3. Madde 16-18: iş ortaklığı, konsorsiyum, alt yüklenici

- [ ] Belgen yetmiyorsa iş ortaklığı kur: pilot %70 / diğer %10 / toplam %30. Alt yüklenici yasak (m.18.1) — ortak olmayan uzmanın belgesi kullanılamaz.

## 4. Madde 19-25: teklif ve fiyata dahil giderler

- [ ] Birim fiyat teklif: her kalemin birim fiyatı × miktar; aritmetik hata teklifi değerlendirme dışı bıraktırır.
- [ ] Teklif fiyatına dahil: KİK payı, damga vergileri, nakliye vb. (m.25.3.1). KİK payı eşiğini `legal_get_social_parameters` `ihale_kik_payi_sozlesme_esigi` ile çek.
- [ ] **İşçilik satırı varsa** (personele dayalı olmasa bile): her satır, sözleşme gideri ve genel gider dahil asgari işçilik maliyetinin altında olamaz; altındaysa teklif değerlendirme dışı. Personele dayalı işte de aynı sonuç (78.29). Hesap → `personel-calistirma-ve-fiyat-farki.md` §2.
- [ ] Fiyat farkı yok (m.43): 6 aylık sürede girdi artışı riskini fiyata koy; yalnız mücbir sebep / idareden kaynaklı süre uzatımında esaslara göre fiyat farkı var.

## 5. Madde 24, 26-27: geçerlilik ve geçici teminat

- [ ] Teklif geçerlilik 90 gün; geçici teminat teklif bedelinin en az %3'ü; mektup geçerlilik tarihi şartnamedeki tarihten önce olamaz (örnek 08.04.2027). Eksik teminat ilk oturumda eler (4734 m.37/2).
- [ ] Nakit teminat istekli hesabından ve ihale saatinden önce yatırılmalı; makbuz EKAP'a yüklenmeli (m.27.5) `[kullanıcı verdi]`.

## 6. İş deneyimi güncelleme

- [ ] 4734 kapsamındaki işte: işin **ihale tarihi** ayından bir önceki ayın Yİ-ÜFE'si → ilk ilan ayından bir önceki ayın endeksi; 4734 dışı işte: **sözleşme** ayından bir önceki ay; alt yüklenici belgesinde yüklenici-alt yüklenici sözleşme tarihi; yabancı para birimi için önce TCMB kuru.
- [ ] Hesap: `legal_calculate_tender` `hesap: "tutar_guncelle"`, `belge: "is_deneyim_4734"` ya da `"is_deneyim_diger"`. Araç yoksa: güncel tutar = belge tutarı × E(ilan−1) / E(esas ay); endeksi kullanıcıdan ya da TÜİK'ten iste, sonucu `[incele]` işaretle. Güncel tutar ≥ teklif bedeli × oran mı?
- [ ] Teklif bedelini düşürmek oranı da düşürür (oran **teklif edilen bedel** üzerinden) — ama sınır değer altına düşme ve aşırı düşük riskiyle birlikte düşün (`degerlendirme-sinir-deger.md`).

## 7. Madde 33: en avantajlı teklif ve yerli avantajı

- [ ] Örnek: en düşük fiyat; **%15 yerli istekli avantajı** (m.33.3.1) — yabancı istekli ya da yabancı ortaklı iş ortaklığıysan teklifin karşılaştırmada %15 artırılmış sayılır. Eşitlikte Hizmet Yön. m.63 kriterleri.

---

## Karar: açıklama talebi mi, şikâyet mi, yalnız fiyata yansıtma mı?

| Durum | Öneri |
|---|---|
| Belirsizlik, çelişki (kısım ibaresi, "torna bakım işleri" kapsamı) | Açıklama talebi (20 gün öncesine kadar) |
| Belgen tanıma girmiyor ve tanım ihale konusundan dar / tek firmaya işaret ediyor | Doküman şikâyeti (süre ilk ilandan!) → `ihale-sikayet`; açıklama talebi paralel yapılabilir, süreyi durdurmaz |
| Belgen tanıma girmiyor ama tanım ihale konusuyla aynı ya da daha geniş | "Dar tanım" emsalleri uygulanmaz; iddia zayıf 🟡 — kapsam belirsizse açıklama talebi |
| Orantısız kalite/yetki belgesi seni dışlıyor | Doküman şikâyeti; somut gerekçe ve emsal |
| Ceza oranı, fiyat farkı yokluğu, garanti süresi | Hukuka aykırı değilse ticari risk: fiyata yansıt |

## Görüşme soruları

1. İlk ilan hangi tarihte yayımlandı, dokümanı hangi tarihte indirdiniz?
2. Elinizdeki iş deneyim belgesinin konusu, tarihi, tutarı, düzenleyeni? 4734 kapsamında mı?
3. 7.3.3'teki belgelerden hangileri yok? Üretici yetki belgesi alınabilir mi?
4. Teknik şartnamenin okunabilir metni var mı?
5. Teklifinizde işçilik payı ne kadar, kaç personel çalışacak?
