# Harç hesabı

Araçlar: `legal_calculate_court_fee` (`harc_turu`, nispi harçta `deger`), maktu tutarlar için `legal_get_social_parameters`.

## Zorunlu girdiler

| Girdi | Neden | Yoksa |
|---|---|---|
| Yargı yeri ve aşama (sulh/asliye/icra/BAM/Yargıtay/Danıştay/AYM, dava açılışı / karar / kanun yolu / icra tahsil) | Harç türü | Sor |
| Dava değeri ya da takip tutarı (TL) | Nispi harç | `[___]`; "değersiz" ise maktu |
| Dava nispi mi maktu mu | Tür seçimi | `[incele]` (alan ve dilekçe becerisi) |
| Döviz alacağıysa dava tarihi kuru | Değerin TL karşılığı | `references/parametre-ve-kur.md` |

## Aracın tanıdığı türler

Araç tanımadığı türde `count: 0` ve `hata: "Bilinmeyen harç türü …"` ile geçerli türlerin listesini döndürür; idari yargı harçları, icra başvurma ve icra peşin harcı tanımlı değildir. Eski sürümler bu durumda `harc_tutari: "0"` veriyordu: sonuçta 0 görürsen bunu "harç yok" diye okuma.

| `harc_turu` | Ne hesaplar | Sınama (31.10.2026) |
|---|---|---|
| `basvurma_sulh` | Sulh mahkemesi başvurma harcı (maktu) | 335,20 |
| `basvurma_asliye` | Asliye / idare mahkemesi başvurma harcı (maktu) | 732,00 |
| `karar_ilam_nispi` | Karar ve ilam harcı, değer × binde oran, alt sınırlı | 100.000 → 6.831,00; 5.000 → 732,00 (alt sınır) |
| `pesin_harc` | Dava açılışında nispi harcın dörtte biri | 100.000 → 1.707,75; 5.000 → 183,00 |
| `dava_masrafi_asliye` | Asliye başvurma + peşin harç toplamı | 100.000 → 2.439,75 |
| `icra_tahsil_haciz_once` | İcra tahsil harcı, hacizden önce ödeme | 100.000 → 4.550,00 |
| `icra_tahsil_haciz_sonra` | İcra tahsil harcı, hacizden sonra | 100.000 → 9.100,00 |
| `icra_tahsil_satis` | İcra tahsil harcı, satış yoluyla | 100.000 → 11.380,00 |

### Tuzaklar

1. **`deger` verilmezse nispi harç sessizce alt sınırı döndürür** (`(0 / 1000) × 68.31 = 732.00`). Nispi harçta değer yoksa hesabı durdur ve değeri sor.
2. **Peşin harç alt sınırı:** 5.000 TL değerde araç 183,00 (alt sınırın dörtte biri) verdi. Peşin harcın da maktu alt sınıra tabi olup olmadığı `[model bilgisi — doğrulayın]`; küçük değerli davalarda sonucu `[doğrula]` ile işaretle.
3. **`pesin_harc` dava peşin harcıdır**, icra peşin harcı değildir.
4. Araç **tarih almaz**; her zaman güncel tarifeyle hesaplar. Geçmiş tarihli dava için tutar uyuşmaz → `[doğrula — dava tarihindeki tarife]`.

## Araçta olmayan harçlar → `legal_get_social_parameters`

Maktu harçlar sosyal parametre kalemlerinde dönemiyle durur (`tur` boş bırakılınca hepsi gelir). 31.10.2026'da görülen `harc_*` kalemleri: `harc_arabuluculuk_karar`, `harc_basvurma_asliye`, `harc_basvurma_aym`, `harc_basvurma_sulh`, `harc_basvurma_ust_mahkeme`, `harc_celse_min_asliye`, `harc_celse_min_sulh`, `harc_haciz_teslim_satis`, `harc_icra_basvurma`, `harc_icra_degersiz`, `harc_icra_idare`, `harc_icranin_tehiri`, `harc_iflas_konkordato`, `harc_ihtiyati_tedbir_haciz`, `harc_ilam_suret`, `harc_istinaf_bam`, `harc_karar_ilam_maktu`, `harc_karar_ilam_min_nispi`, `harc_kesif`, `harc_temyiz_danistay`, `harc_temyiz_red_maktu`, `harc_temyiz_yargitay`, `harc_tic_sicil_gercek_tescil`, `harc_tic_sicil_sahis_tescil`, `harc_tic_sicil_sermaye_tescil`, `harc_vekaletname_suret`. Her kalemin `dayanak` alanı Harçlar Kanunu tarife satırını verir.

Kanun yolu harcı (istinaf/temyiz başvurma) maktu kalemle **birlikte** karar harcının da gerekebileceğini unutma; hangi kalemlerin toplanacağı `[model bilgisi — doğrulayın]`.

## Araçta hiç olmayanlar

| Eksik | Geçici yol |
|---|---|
| İdari yargı nispi harçları, idari dava karar harcı | Maktu kalemler (`harc_basvurma_asliye` "Asliye / İdare") + `[doğrula — Harçlar Kanunu (1) sayılı tarife]` |
| İcra peşin harcı, ilamsız takip başvurma dışındaki nispi icra harçları, ihalenin feshi nispi harcı | `harc_icra_basvurma` maktu + oranı kullanıcıdan/tarife tebliğinden `[doğrula]` |
| Gider avansı, tebligat ve bilirkişi ücreti | Araçta yok; mahkemenin gider avansı tarifesi `[doğrula]` |
| Vekâlet ücreti (AAÜT) | `legal_calculate_attorney_fee` (hüküm tarihindeki tarife, 2020-11-24 ve sonrası tablolar); araç yanıt vermezse ya da hata dönerse: `legal_search_official_gazette` `query: "Avukatlık Asgari Ücret Tarifesi"` `search_in: "title"` `sort_by: "date_desc"` |
| Harçtan muafiyet (ör. işçinin iş davası, adli yardım) | Hukuki değerlendirme; alan becerisi `[incele]` |

## Hesap tablosu iskeleti

| Kalem | Tür kodu | Değer (TL) | Formül (aracın `hesaplama` alanı) | Tutar | Kaynak |
|---|---|---|---|---|---|
| Başvurma harcı | `basvurma_asliye` | — | Maktu | … | [soorgla] |
| Peşin harç | `pesin_harc` | … | Karar ilam harcının 1/4 | … | [soorgla] |
| **Toplam dava açılış harcı** | | | | … `[doğrula]` | |

Değer döviz ise TL karşılığını hangi kurla bulduğunu satıra yaz.

## Teyit eşiği

Dava değeri belirsiz ya da ıslahla artacaksa, döviz alacağıysa, muafiyet iddiası varsa, idari yargı veya icra nispi harcıysa → 🟠 kalem kalem `[doğrula]`; harç tahsil eden mercinin hesabı esastır.

## Örnek çağrılar

```
legal_calculate_court_fee harc_turu: "dava_masrafi_asliye" deger: 100000
legal_calculate_court_fee harc_turu: "icra_tahsil_haciz_once" deger: 100000
legal_get_social_parameters tur: "harc_istinaf_bam"
```
