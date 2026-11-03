# Sütun şablonları

Hazır şemalar başlangıç noktasıdır, kontrol listesi değildir. İşlemin pay alım sözleşmesindeki beyan ve tekeffüller, bilgi talep listesi ve kullanıcının soruları neyin önemli olduğunu belirler. Sütun türleri ve durumlar → `tablolu-inceleme-akisi.md` §2-3.

Şablonlardaki hiçbir sütun bir tutar, oran ya da süre **sınırı** içermez; eşikler kullanıcıdan alınır, kanuni sınırlar gerektiğinde soorgla'dan çekilir.

Upstream `ma-diligence-columns.md` uyarlamasıdır; ABD'ye özgü sütunlar (sigorta türleri, MFN'nin ABD anlamı, FAR/DFARS, BAA) çıkarıldı, Türk uygulamasındaki karşılıklar eklendi.

---

## 1. Şirket satın alma — durum tespiti, standart sözleşme seti

```yaml
sema:
  ad: "Durum tespiti — standart sözleşme seti"
  satir: belge
  sutunlar:
    - {id: karsi_taraf, etiket: "Karşı taraf", tur: birebir, soru: "Hedef şirket dışındaki tarafın unvanı, belgede yazdığı gibi."}
    - {id: sozlesme_turu, etiket: "Sözleşme türü", tur: secim,
       secenekler: [hizmet, satis_tedarik, bayilik_distributorluk, acentelik, lisans_alinan, lisans_verilen, kira, eser_insaat, kredi_finansman, kefalet_garanti, gizlilik, ortak_girisim_adi_ortaklik, pay_sahipleri, is_sozlesmesi, kamu_sozlesmesi, diger],
       soru: "Bu ne tür bir sözleşme?"}
    - {id: imza_yururluk, etiket: "İmza / yürürlük tarihi", tur: tarih, soru: "Sözleşme hangi tarihte imzalandı ya da yürürlüğe girdi?"}
    - {id: sure, etiket: "Süre", tur: sure, soru: "İlk sözleşme süresi ne kadar? Belirsiz süreli mi?"}
    - {id: yenileme, etiket: "Kendiliğinden yenileme", tur: secim, secenekler: [yok, yillik, belirli_sure, belirsiz_sureye_doner], soru: "Sözleşme kendiliğinden uzuyor mu, hangi döngüyle?"}
    - {id: hakli_sebepsiz_fesih, etiket: "Haklı sebep olmadan fesih", tur: secim, secenekler: [yok, iki_taraf, yalniz_hedef, yalniz_karsi_taraf], soru: "Taraflardan biri sebep göstermeden feshedebilir mi?"}
    - {id: fesih_bildirim_suresi, etiket: "Fesih bildirim süresi", tur: sure, soru: "Fesih için ne kadar önceden bildirim gerekiyor?"}
    - {id: bildirim_sekli, etiket: "Bildirim şekli", tur: birebir, soru: "Fesih ve temerrüt bildirimleri hangi yolla yapılır (noter, iadeli taahhütlü, KEP, e-posta)?"}
    - {id: kontrol_degisikligi, etiket: "Kontrol değişikliği", tur: secim,
       secenekler: [sessiz, onay_gerekli, onay_hakli_sebepsiz_esirgenemez, kendiliginden_sona_erme, yalniz_bildirim, karsi_tarafa_fesih_hakki],
       soru: "Hedef şirketin ortaklık yapısı ya da yönetim kontrolü değişirse ne olur?"}
    - {id: devir, etiket: "Sözleşmenin devri", tur: secim,
       secenekler: [sessiz, yazili_onay_gerekli, onay_hakli_sebepsiz_esirgenemez, serbest, grup_sirketlerine_serbest, devredilemez],
       soru: "Hedef şirket sözleşmeyi ya da alacaklarını devredebilir mi, hangi koşulla?"}
    - {id: munhasirlik, etiket: "Münhasırlık / rekabet yasağı", tur: secim,
       secenekler: [yok, munhasir_tedarikci, munhasir_musteri, bolge_munhasirligi, rekabet_yasagi, calisan_ayartmama, en_iyi_kosul],
       soru: "Taraflardan birinin rakiplerle çalışması ya da başkalarıyla sözleşme yapması kısıtlanıyor mu?"}
    - {id: sorumluluk_siniri, etiket: "Sorumluluk sınırı", tur: tutar, soru: "Sorumluluk bir tutarla ya da bedelin katıyla sınırlanmış mı?"}
    - {id: cezai_sart, etiket: "Cezai şart", tur: birebir, soru: "Cezai şart var mı; hangi ihlalde, ne tutarda ya da nasıl hesaplanıyor?"}
    - {id: tazmin, etiket: "Tazmin (üçüncü kişi talepleri)", tur: secim, secenekler: [yok, karsilikli, hedef_tazmin_eder, karsi_taraf_tazmin_eder, yalniz_fikri_mulkiyet, yalniz_ucuncu_kisi_talepleri], soru: "Kim kimi, hangi zararlar için tazmin ediyor?"}
    - {id: teminat, etiket: "Teminat", tur: birebir, soru: "Teminat mektubu, kefalet, rehin, ipotek ya da depozito var mı?"}
    - {id: asgari_alim, etiket: "Asgari alım / hacim taahhüdü", tur: tutar, soru: "Asgari alım, hacim ya da harcama taahhüdü var mı?"}
    - {id: doviz, etiket: "Bedelin para birimi", tur: birebir, soru: "Bedel hangi para biriminde ya da dövize endeksli mi?"}
    - {id: fikri_mulkiyet, etiket: "Fikri mülkiyet", tur: secim, secenekler: [herkes_kendi, hedefe_ait, karsi_tarafa_ait, ortak, yalniz_lisans, sessiz], soru: "Sözleşme kapsamında üretilen ya da kullanılan fikri mülkiyet kime ait?"}
    - {id: kisisel_veri, etiket: "Kişisel veri", tur: secim, secenekler: [yok, veri_isleme_maddesi_var, ayri_veri_isleme_sozlesmesi, yurt_disina_aktarim_var, sessiz_ama_veri_isleniyor], soru: "Sözleşme kişisel veri işlenmesini ya da aktarımını düzenliyor mu?"}
    - {id: gizlilik_suresi, etiket: "Gizlilik süresi", tur: sure, soru: "Gizlilik yükümlülüğü sona ermeden sonra ne kadar sürüyor?"}
    - {id: uygulanacak_hukuk, etiket: "Uygulanacak hukuk", tur: birebir, soru: "Hangi ülke hukuku uygulanır?"}
    - {id: uyusmazlik, etiket: "Uyuşmazlık çözümü", tur: secim, secenekler: [mahkeme_yetki_sozlesmesi, mahkeme_sessiz, tahkim_istac, tahkim_icc, tahkim_diger, once_arabuluculuk, sessiz], soru: "Uyuşmazlık nerede, nasıl çözülür?"}
    - {id: imza_tam, etiket: "İmza ve ekler tam mı", tur: secim, secenekler: [tam, imza_eksik, ek_eksik, paraf_eksik, okunamadi], soru: "Belge tüm taraflarca imzalanmış ve atıf yapılan ekler mevcut mu?"}
```

**Hızlı ilk geçiş (6 sütun):** karşı taraf, imza/yürürlük, süre, kontrol değişikliği, devir, haklı sebep olmadan fesih. Erken soruların çoğunu cevaplar; işlem ekibi öncelikleri belirleyince şema genişletilir.

**Sütunların hukuki çerçevesi** (değerlendirme alan becerisinde; burada yalnız neye bakıldığı):
- Sözleşmenin devri üç taraflı anlaşma ya da kalan tarafın önceden izni/sonradan onayıyla olur; geçerliliği devredilen sözleşmenin şekline bağlıdır — TBK m.205 `[soorgla]`. **Pay devri** sözleşme devri değildir; hedef şirket taraf olarak kalır, bu yüzden pay alımında asıl sütun **kontrol değişikliği**dir. **Malvarlığı / işletme devrinde** ise sözleşmeler tek tek devredilir ve devralan bildirim/ilandan itibaren borçlardan sorumlu olur, önceki borçlu iki yıl müteselsilen sorumlu kalır — TBK m.202 `[soorgla]`.
- Tacirler arasında temerrüt, fesih ve dönme ihbarlarının şekli TTK m.18/3'te sayılır (noter, taahhütlü mektup, telgraf, güvenli elektronik imzalı KEP) `[soorgla]` → `bildirim_sekli` sütunu bu yüzden vardır.
- Yetki sözleşmesi yalnız tacirler veya kamu tüzel kişileri arasında yapılabilir — HMK m.17 `[soorgla]`; tüketici ya da tacir olmayan karşı tarafta yetki maddesi `belirsiz` işaretlenir.
- Hâkim aşırı cezai şartı kendiliğinden indirir — TBK m.182/3 `[soorgla]`; tacir borçlu için TTK m.22 istisnası → `sozlesme-incelemesi-tbk` `[model bilgisi — doğrulayın]`.
- Hedef şirket lisanslı bir sektördeyse (enerji, finansal kiralama/faktoring, sermaye piyasası, bankacılık, telekom) kontrol değişikliği sözleşmeden bağımsız olarak **kurul iznine** tabi olabilir; ayrı bir `sektor_izni` sütunu ekle ve dayanağı `legal_search_statute_semantic` ile çek (ör. 6361 m.11 `[soorgla]`). Yargıtay 11. HD, kontrol değişikliği sonucu veren pay devrinde EPDK onayının araştırılmamasını bozma sebebi saymıştır `[soorgla]` (E.2024/3398 K.2024/6583, 19.09.2024 — tam metin okundu).
- Birleşme ve devralmalarda Rekabet Kurulu izni → 4054 m.7 `[soorgla]`; izin eşikleri tebliğdedir, beceriye yazılmaz → `sirketler-ticaret`.

### İşlem türüne göre ek sütunlar
- **Teknoloji / yazılım:** kaynak kod yediemini, açık kaynak kısıtları, veri ve model eğitim hakları, API erişimi → değerlendirme `fikri-mulkiyet-bilisim`.
- **Kamu sözleşmesi yüklenicisi:** sözleşme devri için idare izni, alt yüklenici onayı, yasaklılık beyanı → `kamu-ihale`, `hakedis`.
- **Lisanslı sektör:** `sektor_izni`, lisans devri, faaliyet izni koşulları.
- **Gayrimenkul ağırlıklı:** tapu kaydı, şerhler, ipotek → `gayrimenkul-insaat`.

## 2. Kira portföyü

```yaml
sema:
  ad: "Kira portföyü"
  satir: belge
  sutunlar:
    - {id: tasinmaz, etiket: "Taşınmaz / adres", tur: birebir, soru: "Kiralananın adresi ya da ada/parsel bilgisi."}
    - {id: taraf_rolu, etiket: "Müvekkilin rolü", tur: secim, secenekler: [kiraci, kiraya_veren], soru: "Müvekkil bu sözleşmede kiracı mı kiraya veren mi?"}
    - {id: karsi_taraf, etiket: "Karşı taraf", tur: birebir, soru: "Diğer tarafın adı/unvanı."}
    - {id: kullanim, etiket: "Kullanım", tur: secim, secenekler: [konut, catili_isyeri, arsa_acik_alan, avm_magaza, depo, diger], soru: "Kiralanan ne amaçla kullanılıyor?"}
    - {id: baslangic, etiket: "Başlangıç", tur: tarih, soru: "Kira başlangıç tarihi."}
    - {id: sure, etiket: "Süre", tur: sure, soru: "Kira süresi."}
    - {id: bedel, etiket: "Güncel aylık bedel", tur: tutar, soru: "Belgedeki aylık kira bedeli ve para birimi."}
    - {id: artis_maddesi, etiket: "Artış maddesi", tur: birebir, soru: "Kira bedelinin nasıl artacağını düzenleyen madde."}
    - {id: doviz, etiket: "Dövizli bedel", tur: secim, secenekler: [hayir, doviz, dovize_endeksli], soru: "Bedel dövizle ya da dövize endeksli mi?"}
    - {id: depozito, etiket: "Güvence (depozito)", tur: tutar, soru: "Güvence bedeli ne kadar ve nasıl tutuluyor?"}
    - {id: devir_alt_kira, etiket: "Devir / alt kira", tur: secim, secenekler: [sessiz, yasak, yazili_onayla, serbest], soru: "Kiracı kira ilişkisini devredebilir ya da alt kiraya verebilir mi?"}
    - {id: tahliye_taahhudu, etiket: "Tahliye taahhüdü", tur: secim, secenekler: [yok, var_tarihli, var_tarihsiz, belirsiz], soru: "Ayrı ya da sözleşme içinde tahliye taahhüdü var mı?"}
    - {id: fesih_bildirimi, etiket: "Fesih / uzama bildirimi", tur: birebir, soru: "Süre sonunda fesih ya da uzama için bildirim kuralı."}
    - {id: tadilat, etiket: "Tadilat ve iyileştirme", tur: birebir, soru: "Kiracının tadilat yapma hakkı ve masrafların kime ait olduğu."}
    - {id: aidat_vergi, etiket: "Aidat, vergi, sigorta", tur: birebir, soru: "Aidat, emlak vergisi, DASK ve sigorta kime ait?"}
    - {id: sonraki_kritik_tarih, etiket: "Sonraki kritik tarih", tur: tarih, soru: "Artış dönemi, süre sonu ya da bildirim son günü — hangisi en yakın?"}
```

- Kira ilişkisinin devri kiraya verenin yazılı rızasına bağlıdır; işyeri kiralarında haklı sebep olmadıkça rıza esirgenemez ve devreden kiracı en fazla iki yıl müteselsil sorumlu kalır — TBK m.323 `[soorgla]`.
- Konut ve çatılı işyerinde belirli süreli sözleşme, kiracı süre bitiminden en az on beş gün önce bildirmezse bir yıl uzar; kiraya veren süre bitimine dayanarak sona erdiremez — TBK m.347 `[soorgla]`. `sonraki_kritik_tarih` hesaplanırken son gün `legal_check_holiday` ile kontrol edilir ve `[doğrula]` alır.
- Artış maddesinin geçerliliği, kira tespiti, tahliye ve güncel bedel hesabı → `../../kira-hukuku/SKILL.md`. Tabloda yalnız madde birebir alınır; `legal_calculate_cpi_change` ile kaba bir "TÜFE'ye göre bugünkü bedel" sütunu eklenebilir ama TBK m.344'ün on iki aylık ortalama kipi araçta yoktur → `[doğrula]`.

## 3. İş sözleşmeleri seti (durum tespiti ya da iç denetim)

Sütunlar: çalışan (adı yerine **sicil no ya da takma kod** — KVKK m.4 ölçülülük), unvan, işe giriş, sözleşme türü (belirli/belirsiz/kısmi/çağrı), deneme süresi, ücret ve para birimi, fazla çalışmanın ücrete dahil olduğu maddesi, rekabet yasağı (süre, yer, konu — `birebir`), cezai şart, eğitim gideri iadesi, kontrol değişikliğine bağlı ödeme (`birebir`), gizlilik, buluş/eser devri, fesih bildirim süresi, imza tam mı.
Değerlendirme → `../../is-hukuku/references/is-sozlesmesi-denetimi.md`, `../../is-hukuku/references/ise-alim-ve-rekabet-yasagi.md`. Sağlık verisi, sendika üyeliği gibi özel nitelikli veriler tabloya alınmaz.

## 4. Veri işleme ve aktarım sözleşmeleri

Sütunlar: karşı taraf ve rolü (veri sorumlusu / veri işleyen), işlenen veri kategorileri, özel nitelikli veri var mı, amaç, yurt dışına aktarım ve dayanağı (standart sözleşme, taahhütname, yeterlilik), alt işleyen izni, güvenlik tedbirleri maddesi, ihlal bildirim süresi (`birebir`), denetim hakkı, sözleşme sonunda silme/iade.
Değerlendirme ve süreler → `../../kvkk/SKILL.md` (veri işleme sözleşmesi ve standart sözleşme referansları). Standart sözleşmenin Kurula bildirim yükümlülüğü gibi süreler tabloya yazılmaz, `kvkk` becerisi soorgla'dan çeker.

## 5. Bayilik / distribütörlük ağı

Sütunlar: bayi, bölge, münhasırlık türü, süre ve yenileme, asgari alım/satış hedefi, fiyat belirleme (yeniden satış fiyatı tespiti var mı — `birebir`), internet satışı kısıtı, rekabet yasağı ve sözleşme sonrası süresi, portföy (denkleştirme) tazminatı feragati, stok geri alımı, fesih sebepleri, cezai şart.
Değerlendirme → `../../sozlesme-incelemesi-tbk/references/distributorluk-bayilik-acentelik.md`; dikey anlaşmaların rekabet hukuku yönü → `../../sirketler-ticaret/references/rekabet-hukuku-4054.md`.
