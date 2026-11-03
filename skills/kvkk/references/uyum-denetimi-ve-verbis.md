# Uyum denetimi, VERBİS, envanter, saklama-imha ve politika güncelliği

## Ne zaman kullanılır
- "KVKK'ya uyumlu muyuz?", "denetime hazırlanıyoruz", "VERBİS kaydı yapmamız gerekiyor mu?", "envanter ve imha politikası lazım".
- Yeni bir Kurul ilke kararı, yönetmelik ya da kanun değişikliği çıktı: "bu bizi etkiler mi?" (upstream reg-gap-analysis).
- Uygulama değişti ama metinler eski kaldı mı? (upstream policy-monitor: aydınlatma metni, çerez bildirimi, VERBİS kaydı, mobil uygulama mağaza beyanı, iç politikalar arasında sapma taraması).

---

## Süreler ve dayanakları

| Konu | Kural | Dayanak |
|---|---|---|
| VERBİS kaydı | Veri işlemeye **başlamadan önce**; Kurul nesnel ölçütlerle istisna getirebilir | 6698 m.16/2 |
| VERBİS bilgi değişikliği | **Derhâl** bildirilir | 6698 m.16/4 |
| Kayıt eşiği ve son kayıt tarihleri | Kurul kararlarıyla belirlenir (çalışan sayısı, yıllık mali bilanço, ana faaliyetin özel nitelikli veri olması) | Kurul 2018/87 (mali bilanço eşiği **2023/1154** ile değiştirildi), 2018/88 ve sonraki uzatma kararları; güncel eşiği son karardan çek |
| Periyodik imha | Saklama-imha politikasındaki aralıkla; kanun dışı silme yükümlülüğü ortaya çıktıktan sonraki ilk periyodik imhada | Silme Yönetmeliği (`24038`) m.11: periyodik imha aralığı politikada belirlenir, **en fazla 6 ay**; politika hazırlama yükümlülüğü olmayan sorumlu yükümlülüğün doğduğu tarihten itibaren **3 ay** içinde siler. Politika zorunluluğu VERBİS'e kayıt yükümlüsü veri sorumlularıyla sınırlı (m.5/1); diğerlerinin silme yükümlülüğü sürer (m.5/3) |
| Kurul kararına uyum | Tebliğden itibaren gecikmeksizin, en geç **30 gün** | 6698 m.15/5 |

---

## Kontrol listesi — uyum denetimi (data_protection.yaml'ın dört süzgeci + tamamlayıcılar)

1. **Envanter**: süreç bazında veri kategorileri, ilgili kişi grupları, amaç, hukuki sebep, alıcılar, yurt dışı, saklama süresi, güvenlik tedbirleri. Envanter yoksa diğer tüm maddeler tahmindir. 🟠
2. **Genel ilkeler** (m.4): hukuka ve dürüstlüğe uygunluk, doğruluk, belirli ve meşru amaç, amaçla sınırlılık ve ölçülülük, gerekli süre kadar saklama.
3. **Hukuki sebep doğru mu?** (süzgeç 2) Açık rızanın gerektiği yerde başka şarta, başka şartın yeterli olduğu yerde açık rızaya dayanılmış mı? Özel nitelikli veride 7499 sonrası m.6/3 şartları ve m.6/4 yeterli önlemler.
4. **Aydınlatma ve açık rıza ayrımı** (süzgeç 1) → `aydinlatma-ve-acik-riza.md`.
5. **VERBİS tutarlılığı** (süzgeç 3): fiilen işlenen veriler, amaçlar, alıcılar, yurt dışı aktarım ve güvenlik tedbirleri VERBİS beyanıyla eşleşiyor mu? Kayıt bildirimi m.16/3'teki unsurları içerir.
6. **Yurt dışı aktarım** (süzgeç 4) → `yurt-disi-aktarim.md`.
7. **Veri güvenliği** (m.12): teknik ve idari tedbirler, iç denetim yükümlülüğü, veri işleyenlerle müşterek sorumluluk. Kurumun "veri güvenliği rehberi" için `[model bilgisi — doğrulayın]`.
8. **Saklama ve imha**: saklama-imha politikası, süreler, periyodik imha kayıtları; silmeme TCK 138 riski taşır.
9. **İlgili kişi başvuru süreci** → `ilgili-kisi-basvurusu.md`.
10. **Veri işleyen sözleşmeleri** → `veri-isleme-sozlesmesi.md`.
11. **İhlal müdahale planı** → `veri-ihlali-bildirimi.md`.
12. **Sektörel ilke kararları**: faaliyet alanına ilişkin RG'de yayımlanmış Kurul ilke kararlarını tara (aşağıdaki liste ve çağrı). Örnekler (bu becerinin yazıldığı tarihte çekilenler):
    - Turizm/otel: konaklama müşterisinin kimlik belgesi fotokopisinin kaydedilmesi — KVK Kurulu 06.11.2025 t. 2025/2120 s. İlke Kararı (RG 09.12.2025)
    - Perakende: sadakat kartı ile doğrulamasız alışveriş — KVK Kurulu 11.02.2026 t. 2026/266 s. Karar (RG 28.02.2026)
    - Site/apartman yönetimi: aidat borçlusu listelerinin ortak alanlara asılması — 18.02.2026 t. 2026/348 s. İlke Kararı (RG 31.03.2026)
    - Kamu tüzel kişileri: kişisel verilerin internette yayımlanması — 01.07.2026 t. 2026/1301 s. İlke Kararı (RG 28.07.2026)
    - İşveren: biyometrik mesai takibi — 2026/921 (RG 02.06.2026); kurumsal e-posta denetimi — 2026/2035 (RG 08.10.2026) → `on-inceleme-ve-etki-degerlendirmesi.md`
    - Kaza mağdurlarının verilerine "hasar danışmanlığı" aracılarının erişimi — 20.05.2026 t. 2026/1095 s. İlke Kararı (RG 01.07.2026)
    - SMS doğrulama kodu ile ticari ileti — 2025/1072 (RG 26.06.2025) → `aydinlatma-ve-acik-riza.md`
    Liste tabandır, güncel değildir: her denetimde RG'yi yeniden tara.
13. **Kamu kurumu** ise: m.18/4 uyarınca para cezası yerine disiplin hükümleri; m.28/2 istisnaları; üst düzey koordinasyon yöneticisi.

## Kontrol listesi — mevzuat/ilke kararı değişikliği açık analizi (upstream reg-gap-analysis)

1. **Uygulanıyor mu?** Sektör, veri türü, kamu/özel, VERBİS yükümlülüğü. Uygulanmıyorsa tek satır: "Uygulanmaz, çünkü …". Yine de belgele.
2. **Ne zaman?** Yayım ve yürürlük tarihi, geçiş hükmü (7499'da 1/6/2024 ve 1/9/2024 gibi).
3. **Ne yeni?** Yalnız farkı çıkar: | # | Gereklilik | Dayanak | Kategori (bildirim/aydınlatma, haklar, güvenlik, veri işleyen, rıza, yönetişim) |
4. **Bugünkü durumla karşılaştır**: | Gereklilik | Bugün ne yapıyoruz | Açık (yok/kısmi/tam) | Kapatma çabası (metin / ürün / tedarikçi / yeni süreç) | Risk |
5. **Önceliklendir**: yaptırımı ve süresi olan → düşük maliyetli metin düzeltmeleri → kalanlar.
6. **Plan**: | Açık | Düzeltme | Sorumlu | Son tarih | Durum | — "açık yok" sonucu da tarihli olarak yazılır.

## Kontrol listesi — metin–uygulama sapması (upstream policy-monitor)

Taranacak yüzeyler: web aydınlatma metni · çerez bildirimi ve tercih paneli · mobil uygulama içi izin ekranları ve mağaza veri beyanları · çağrı merkezi anonsu · işe alım ilanı/aday formu · kamera uyarı levhaları · VERBİS kaydı · saklama-imha politikası · DPA'lar.
Her sapmayı ikiye ayır: **ZORUNLU** (metin uygulamayı yanlış anlatıyor ya da hiç anlatmıyor) / **ÖNERİLEN** (metin sessiz ama çelişki yok). Her biri için mevcut metni alıntıla ve önerilen ifadeyi yaz.

---

## Görüşme soruları

| Alan | Soru |
|---|---|
| Kurum | Sektör, çalışan sayısı, yıllık mali bilanço, ana faaliyet özel nitelikli veri mi, kamu mu? |
| VERBİS | Kayıtlı mı, son güncelleme? İrtibat kişisi? |
| Belgeler | Envanter, aydınlatma metinleri, açık rıza metinleri, saklama-imha politikası, veri güvenliği politikası, DPA'lar, ihlal planı — hangileri var? |
| Sistemler | Veri nerede tutuluyor (yurt içi/dışı, bulut)? |
| Geçmiş | Kurul incelemesi, şikâyet, ihlal bildirimi oldu mu? |
| Değişiklik | Hangi yeni düzenleme ya da ilke kararı soruluyor? |

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "6698" article_no: "4" | "7" | "12" | "16" | "28"
legal_search_official_gazette query: "Kişisel Verileri Koruma Kurulunun" search_in: "title" sort_by: "date_desc" limit: 20
legal_get_official_gazette_document url: "<ilke kararı>"
legal_search_admin_guidance sorgu: "Kişisel Verileri Koruma Kurulunun kararı Veri Sorumluları Siciline kayıt yükümlülüğü istisna" kurum: "Kişisel Verileri Koruma Kurulu" tarih_baslangic: "<son 3 yıl>"
legal_search_statute_semantic sorgu: "kişisel saklama ve imha politikası periyodik imha"
legal_search_statute law_no: "7499" query: "6698" # değiştiren kanun maddeleri
```
Not: 2026-10-31'den beri `kurum: "Kişisel Verileri Koruma Kurulu"` ve `tarih_baslangic`/`tarih_bitis` çalışıyor (karar özetleri ve ilke kararları 2026'ya kadar); eski RG kaynaklı `kurul_karar` kayıtlarında tarih alanı boş olabilir, onlarda sorguya yıl yaz.

---

## Çıktı iskeleti — uyum denetim raporu

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …

# KVKK Uyum Denetimi — [kurum] — [tarih]
## Sonuç
[Genel durum; en kritik 3 açık] Bulgular: [N]🔴 [N]🟠 [N]🟡 [N]🟢

## Bulgular
| # | Alan | Bulgu | Önem | Dayanak | Düzeltme | Sorumlu | Tarih |

## Sektörel ilke kararları
| Karar | Bize etkisi | Durum |

## Düzeltme planı
### Yaptırım riski taşıyan (önce)
### Önerilen
### Kabul edilen riskler (gerekçe ve onaylayan)
```
On satırı aşan bulgu tablosunda kullanıcıya etkileşimli pano öner (ORTAK-KURALLAR.md'de pano kuralı yoksa yalnız teklif et).

---

## Sık hatalar
- VERBİS'i bir kez doldurup değişiklikleri bildirmemek.
- Envanter olmadan aydınlatma metni yazmak.
- Saklama sürelerini "süresiz" bırakmak; imha kaydı tutmamak.
- Sektörel ilke kararlarını taramamak.
- VERBİS eşiğini ya da ceza tutarını hafızadan yazmak.
