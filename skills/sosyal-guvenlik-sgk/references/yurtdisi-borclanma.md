# Yurt dışı hizmet, borçlanma ve ikili sosyal güvenlik sözleşmeleri

**Ne zaman kullanılır:** yurt dışında geçen sürelerin 3201 sayılı Kanun ile borçlanılması, Türkiye'nin taraf olduğu ikili sosyal güvenlik sözleşmeleri kapsamında hizmet birleştirme ve kısmi aylık, bunların emeklilik tarihine etkisi.

Bu alan yabancı unsurludur: karşı ülkenin mevzuatı hakkında emin cevap verme (ORTAK-KURALLAR.md §2).

**MCP notu:** 3201 numarasını 1937 tarihli Emniyet Teşkilat Kanunu da taşıyor. `legal_get_statute_article` (`law_no: "3201"`, `law_type: "Kanun"`) yurt dışı borçlanma kanununu (`statute_id 39996`) döndürür, Emniyet kanunu `other_candidates`'ta gelir; yine de yanıttaki başlığın "Yurt Dışında Bulunan Türk Vatandaşlarının …" olduğunu kontrol et.

---

## Süre tablosu

| Süre | Dayanak | Not |
|---|---|---|
| Borçlanma bedelinin ödenmesi: tebliğden itibaren **3 ay** | 3201 m.4 | Eski referanstaki "3201 m.5 ödeme süresi" atfı yanlıştı; doğru madde m.4. Yurt içi borçlanmadaki 1 aylık süreyle (5510 m.41) karıştırma. 🔴 |
| Kuruma karşı dava | 7036 m.4/1 | Önce Kuruma başvuru; 60 gün cevapsızlık = ret. |

`legal_calculate_deadline` bu süreleri hesaplamaz; elle hesapla, `[doğrula]`.

---

## Kontrol listesi

### 1. Kanun mu, sözleşme mi?
- Borçlanma yalnızca 3201'e göre mi yapılacak, yoksa ilgili ülke ile yapılmış **ikili sosyal güvenlik sözleşmesi** de uygulanacak mı? Sözleşmeler çoğu zaman hizmet birleştirme ve kısmi aylık imkânı verir; kısmi aylık alanların sonradan borçlanması 3201 m.9 ve geçici m.9'da ayrıca düzenlenmiş. `[incele]`
- Sözleşmenin varlığını ve metnini `legal_search_statute_semantic` / `legal_search_official_gazette` ile ara (sözleşmeler kanunla onaylanır ve Resmî Gazete'de yayımlanır). Bulunamazsa ülke ve sözleşme varlığını `[model bilgisi — doğrulayın]` diye işaretle.

### 2. Yurt dışı hizmetin ispatı
- Belgeler: yabancı sigorta kurumundan hizmet belgesi, işveren belgeleri, ev kadınlığı süreleri için ikamet belgesi.
- Apostil ya da konsolosluk onayı, yeminli tercüme `[doğrula]`.
- Sosyal güvenlik sözleşmesi olan ülkelerde hizmet bilgileri ve aylık işlemleri irtibat kurumları arasında sözleşmeye özgü formülerlerle yürür (SGK'nın "Kurumsal / Dokümanlar / Yurtdışı / Formüler" sayfası); hangi belgenin kişiden istendiği ülkeye ve sözleşmeye göre değişir — yurt dışı borçlanma genelgesini (`legal_search_admin_guidance` `kurum: "Sosyal Güvenlik Kurumu"`, `sorgu: "yurtdışı borçlanma belgeler sözleşmeli ülke"`) ve ilgili sözleşmeyi çek `[doğrula]`.

### 3. Borçlanma statüsü ve tutarı
- Borçlanılan süre hangi statüde sayılır? Yönetmelik, yurt dışı borçlanma sürelerini 4/1-b kapsamında geçmiş sigortalılık süresi sayan bir kural içeriyor; kişinin Türkiye'deki sigortalılık durumuna göre istisnalar var. Somut durumda statüyü `[incele]`; 4/1-b sayılması aylık bağlamada prim borcu yokluğu şartını (5510 m.28) gündeme getirir. 🟠
- Günlük borçlanma tutarı asgari ve azami prime esas kazanç aralığında seçilir → asgari ücreti `legal_get_social_parameters` ile çek; üst sınır katı 5510 m.82'den. Borç, seçilen günlük kazanç üzerinden **tek oranla** hesaplanır; oranı 3201 m.4'ten çek (alt sınırı farklı belirleme yetkisi Cumhurbaşkanında). Tebliğden itibaren 3 ay içinde ödenmezse yeniden başvuru gerekir.

### 4. Emeklilik tarihine etkisi
- Borçlanılan süre sigorta başlangıç tarihini geriye çeker: Türkiye'de sigortalılık varsa ilk giriş tarihinden, yoksa **borcun tamamen ödendiği tarihten** geriye götürülür; birden fazla borçlanmada başlangıç en son borcun ödendiği tarihten toplam gün kadar geri gider. Eski referanstaki "3201 m.6 başlangıç kuralı" atfı yanlıştı; doğru madde m.5 (m.6 aylık bağlanma ve başlangıcı).
- Bu, 08.09.1999 öncesi girişli sayılma ve EYT (5510 geçici m.95) açısından sonuç doğurabilir → `emeklilik-ve-borclanma.md`. 🟠
- Aylık bağlanması yazılı istek tarihini takip eden ay başından başlar (3201 m.6).
- Yurt dışında ikamet ederken aylık ve yurt içinde/yurt dışında yeniden çalışma hâlinde aylığın durumu (3201 m.6 son fıkraları) `[incele]`.

### 5. Yargı yolu
- SGK'nın borçlanma ya da emeklilik talebini reddetmesi → 7036 m.4 başvurusu, sonra iş mahkemesi; temyiz Yargıtay 10. HD (2147 ve 3201 kaynaklı davalar).

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "3201" law_type: "Kanun" article_no: "<4 | 5 | 6 | 9>" # başlığı kontrol et
legal_search_statute_semantic sorgu: "<konu>" mevzuat_no: "3201" # konu araması
legal_search_statute_semantic sorgu: "yurtdışında geçen sürelerin borçlandırılması yönetmelik <konu>"
legal_search_statute_versions query: "yurt dışında geçen süreler borçlanma" # eski metinler
legal_get_statute_article law_no: "5510" article_no: "41" | "82" # yurt içi borçlanma ve kazanç sınırları
legal_search_statute_semantic sorgu: "Türkiye ile [ülke] arasında sosyal güvenlik sözleşmesi"
legal_search_official_gazette query: "[ülke] sosyal güvenlik sözleşmesinin onaylanmasının uygun bulunduğuna dair kanun"
legal_search_cases mahkeme: "yargitay" daire: "10. Hukuk Dairesi"
    sorgu: "<ör. yurt dışı borçlanması sigorta başlangıç tarihinin geriye çekilmesi>"
legal_get_case_document belge_id: "<seçilen karar>"
legal_get_social_parameters tur: "asgari_ucret_brut"
```
Ek kaynak: `IKILI_SSK_SOZLESME` takma filtresi gerçek mevzuat numarası değildir; karşılığı yukarıdaki semantik ve Resmî Gazete aramalarıdır.

---

## Görüşme soruları

1. Yurt dışında çalışılan ülke(ler) ve dönemler?
2. Türkiye'de ilk sigorta giriş tarihi var mı?
3. Ev kadınlığı ya da işsizlik süresi var mı?
4. Şu anda Türkiye'de mi, yurt dışında mı ikamet ediliyor; çifte vatandaşlık?
5. Elde hangi belgeler var (yabancı kurum hizmet belgesi, onaylar)?
6. Daha önce borçlanma başvurusu yapıldı mı, sonucu? Kısmi aylık alınıyor mu?
7. Hedef: emeklilik tarihi mi, aylık tutarı mı?

## Çıktı iskeleti

```markdown
## Yurt dışı borçlanma değerlendirmesi: [kişi] — [tarih]
### Sonuç
### Uygulanacak rejim (3201 / ikili sözleşme / kısmi aylık)
### Hizmet ve belge durumu
| Ülke | Dönem | Belge | Onay | Durum |
### Borçlanma statüsü ve tahmini tutar [doğrula]
### Ödeme süresi (tebliğden 3 ay) ve sonuçları
### Emeklilik tarihine etkisi [doğrula — SGK hizmet dökümü ile]
### Eksik bilgi
```

## Sık hatalar

- 🔴 3 aylık ödeme süresini kaçırmak ya da yurt içi borçlanmadaki 1 ayla karıştırmak.
- 🔴 Başlığı kontrol etmeden 3201 maddesi alıntılamak (aynı numaralı Emniyet Teşkilat Kanunu var).
- 🟠 Borçlanmanın 4/1-b sayılmasının prim borcu şartına etkisini atlamak.
- 🟡 İkili sözleşmenin varlığını kontrol etmeden yalnız 3201 ile cevap vermek.

---
