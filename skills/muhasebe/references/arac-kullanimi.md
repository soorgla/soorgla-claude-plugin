# `legal_calculate_tax` kullanımı

Tek hesap aracı. Çağrı biçimi:

```json
{ "hesap": "<hesap adı>", "<hesap adı>": { ... }, "tarih": "YYYY-AA-GG" }
```

- `hesap` sabit listeden seçilir (26 hesap; liste ve her hesabın alanları aracın şemasında). Eş ad kullanma: bordro/maaş için `ucret`.
- Girdiler, hesabın **kendi adını taşıyan alanda** verilir (ör. `"hesap": "damga", "damga": { ... }`). Eski `girdi` alanı artık kabul edilmez. Eksik alanda araç hata vermez; o hesabın istediği alanları (`gereken_alanlar`) döndürür. Sayıları sayı olarak gönder ("1.000,5" gibi metin değil).
- Listede olmayan `hesap` değeri araç tarafından reddedilir; geçerli değerler şemadaki listedir.
- `tarih` hangi dönemin tarifesi ve oranının kullanılacağını belirler. Verilmezse bugün kullanılır ve `uyarilar` alanında yazılır.

## Yanıt alanları

| Alan | İçerik | Çıktıda nereye |
|---|---|---|
| `sonuc` | Asıl tutarlar | Sonuç paragrafı ve hesap tablosu |
| `ara_degerler` | Girdiler, dilimler, aylar, dönemler | Hesap tablosu |
| `formul` | Kullanılan formül | Hesap tablosunun altı |
| `dayanak` | Madde, tebliğ, CB kararı | Dayanak bölümü (etiketle) |
| `parametre` | Okunan tablo, dönem, kaynak | Dayanak bölümünde "parametre: …" |
| `uyarilar` | Varsayımlar, kontrol edilmeyen şartlar, boş dönemler | Uyarılar bölümüne **hepsi** |

Kaynakta "İKİNCİL" yazıyorsa o değer resmî metinden henüz okunmamıştır: `[doğrula]`.

## Hesaplar

Alanların tam listesi araçtan gelir; aşağıdaki tablo hangi işte hangi hesabın çağrılacağını gösterir.

| `hesap` | Ne zaman | Temel alanlar |
|---|---|---|
| `had` | Bir vergi hadi, oranı ya da tutarı (fatura sınırı, yemek istisnası, amortisman sınırı, SGK oranı…) | `kod` ya da `ara` (sözcük) |
| `damga` | Kâğıt bazında damga vergisi | `sira` ya da `ara`; `tutar`, `nusha` |
| `gecikme_zammi` | 6183 m.51, vadesinde ödenmeyen amme alacağı | `tutar`, `vade`, `odeme` |
| `gecikme_faizi` | VUK 112/3, ikmalen / re'sen tarhiyatta | `tutar`, `vade`, `odeme` (bitiş) |
| `pismanlik_zammi` | VUK 371 ile beyan | `tutar`, `vade`, `odeme` |
| `tecil_faizi` | 6183 m.48 | `tutar`, `baslangic`, `odeme`, `basvuru` |
| `vergi_cezasi` | Vergi ziyaı, usulsüzlük, özel usulsüzlük; tekerrür | `tur` ve türe göre alanlar |
| `ucret` | Brütten nete, netten brüte (ay ay), işveren maliyeti | `mod`, `ay` / `yil` / `aylar`, `brut` ya da `net`; isteğe bağlı `prim_gun`, `sgk_istisna`, `gelir_vergisi_istisna` |
| `sgk_gecikme` | 5510 m.89 SGK gecikme cezası ve zammı | `tutar`, `vade`, `odeme` |
| `fatura_kirilim` | KDV dahil/hariç, tevkifat, stopaj, net | `tutar`, `tutar_turu`, `kdv_orani`, `tevkifat`, `alici` (yapım işi), `belge` |
| `binek_oto` | Binek otomobil gider ve amortisman sınırları | `iktisap_tarihi`, `bedel`, `otv`, `kdv`, … |
| `kira_geliri` | Yıllık kira geliri beyanı | `yil`, `konut`, `isyeri`, `gider_yontemi` |
| `mtv` | Motorlu taşıtlar vergisi | `tarife`, `grup`, `olcu`, `model_yili`, `deger` |
| `emlak` | Emlak vergisi | `tur`, `deger`, `buyuksehir`, `onceki_deger` |
| `degerli_konut` | Değerli konut vergisi | `deger` |
| `veraset` | Veraset ve intikal vergisi | `deger`, `tur`, `istisna` |
| `kkdf` | KKDF kesintisi | `islem`, `odeme_sekli`, `tutar` |
| `otv` | ÖTV (I) ve (III) listeleri | `kalem`, `miktar` |
| `amortisman` | Amortisman tablosu | `maliyet`, `sira` / `ara` / `omur`, `yontem`, `aktife_giris`, `binek` |
| `yeniden_degerleme` | VUK mük.298/Ç | `yil`, `maliyet`, `birikmis_amortisman`, `aktife_giris_yili` |
| `kurumlar` | Kurumlar ve asgari kurumlar vergisi | `yil`, `matrah`, `ihracat_matrahi`, `uretim_matrahi`, `ticari_bilanco_kari`, `kkeg`, `asgari_dusulecek` |
| `kur_farki_reeskont` | Senet reeskontu ya da döviz değerleme | `mod`, … |
| `smmm_ucret` | SM/SMMM/YMM asgari ücret tarifesi | `ara`, `il`, `isci`; kademeli hesapta `sayfa`, `sira`, `tutar` |

**Henüz yok:** `otv` (II) taşıt ve (IV) GTİP listeleri (gümrükle iş bölümü), `enflasyon_duzeltmesi` (endeks ve kapsam kararı). Bu işlerde madde ve tebliğden elle kur, `[doğrula]`.

**Bu araçta değil:** dava ve icra harcı → `legal_calculate_court_fee`; kıdem, ihbar ve işçilik alacakları → `legal_calculate_employment_claims`; kur → `legal_get_exchange_rate`; TÜFE değişimi → `legal_calculate_cpi_change`; süre → `legal_calculate_deadline`.

## Bilinen sınırlar

- **SGK gecikme:** DİBS serisi SGK sayfasından alındı; 2025-03 oranı yok, Nisan 2025'te başlayan dönem hata döndürür.
- **ÖTV:** ÜFE ile otomatik güncellenip RG'de yayımlanmayan dönemlerde tutar verilmez.
- **Damga:** (2) sayılı tablodaki istisnalar kontrol edilmez; uyarıda yazar.
- **Ücret:** teşvikler (5510 m.81 dışındakiler), engellilik indirimi ve birden çok işveren durumu yalnız alanların izin verdiği kadar hesaplanır; araç uyarısını oku.
