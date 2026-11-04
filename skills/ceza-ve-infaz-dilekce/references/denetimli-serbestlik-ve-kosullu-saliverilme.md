# Denetimli serbestlik (5275 m.105/A) ve koşullu salıverilme (m.107)

İki ayrı kurum:
- **Denetimli serbestlik tedbiri uygulanarak infaz (105/A):** koşullu salıverilme tarihinden **önceki** son dönemin cezaevi dışında, denetim altında geçirilmesi. **Talep** gerekir.
- **Koşullu salıverilme (107):** kurumdaki infaz süresinin belirli oranı iyi hâlle geçirilince salıverilme; kurum idaresinin raporu üzerine infaz hâkimi karar verir.

## A. Denetimli serbestlik — 105/A

### Şartlar (güncel metin) 
- **Açık ceza infaz kurumunda ya da çocuk eğitimevinde** bulunmak (105/A/1); açık kuruma ayrılma şartları oluştuğu hâlde **iradesi dışında** ayrılamayanlar da yararlanır (105/A/2).
- Koşullu salıverilmeye **bir yıl veya daha az** kalmış olmak (105/A/1).
- **İyi hâl** ve hükümlünün **talebi**; kurum idaresinin değerlendirme raporu.
- **Karar mercii:** hükmün infazına ilişkin işlemleri yapan Cumhuriyet başsavcılığının bulunduğu yer **infaz hâkimi** (105/A/1).
- **Yeni şart (7550, 2025):** koşullu salıverilme tarihine kadar kurumda geçirmesi gereken sürenin **en az onda birini** (beş günden az olmamak üzere) kurumda geçirmiş olmak. **Yalnız 4.6.2025 ve sonrasında işlenen suçlara** uygulanır (5275 geçici m.11). 
- **Uzatılmış süreler (105/A/3):** 0-6 yaş çocuğu olan kadın hükümlü → koşullu salıverilmeye **iki yıl**; ağır hastalık, engellilik ya da **kocama** nedeniyle hayatını yalnız idame ettiremeyen → **üç yıl** (ATK ya da onaylı sağlık kurulu raporu şart).
- **Yararlanamaz:** adli para cezasının ödenmemesi nedeniyle cezası hapse çevrilenler (105/A/4).
- **Yükümlülükler** (kamuya yararlı iş, konut/bölgede denetim, belirli yerlere gitmeme, programa katılma; TCK 191 hükümlülerine tedavi) denetimli serbestlik müdürlüğünce belirlenir (105/A/5).
- Çıkıştan sonra **beş gün** içinde denetimli serbestlik müdürlüğüne başvuru; ihlallerde açık kuruma iade (105/A/6); alt sınırı bir yıl ve üzeri kasıtlı suçtan dava açılırsa iade edilebilir (105/A/7); başvurmayan ya da teslim olmayan hakkında TCK 292-293 (105/A/8).

### Geçiş hükmü — 31.7.2023 ve öncesi suçlar
5275 geçici m.10/6: 31.7.2023 ve öncesinde işlenen suçlarda (sayılan istisnalar hariç) açık kuruma erken ayrılma ve en az **üç ay** açık kurumda kalmış olmak şartıyla denetimli serbestlikten **üç yıl erken** yararlanma. **7571 s. Kanunla (RG 25.12.2025)** istisnalara bazı kasten öldürme (TCK 82/1-d, e, f), deprem kaynaklı öldürme ve cinsel suçlar (102, 103, 104/2-3) eklendi; "tarihi itibarıyla" ibaresi "tarihi ve öncesinde işlenmiş suçlar nedeniyle" oldu; 7. ve 8. fıkralar kaldırıldı. 
Bu hesap karmaşıktır; müddetnameye yansıyıp yansımadığını kontrol et, farkı `[incele]` ile işaretle.

COVID izinleri (geçici m.9) sona erdi; eski YAML'daki "COVID-19 izinlerinin lehe uygulanabilirliği" talebi artık kurulmaz. Eski YAML'daki "671 s. KHK" atfı **kullanılmaz**: infaz rejimine dayanak olarak doğrulanamadı; dilekçede yalnız 5275 ve geçici maddelerine dayan. 

## B. Koşullu salıverilme — 107

- Kurumdaki süreyi **iyi hâlli** geçirmek (107/1).
- Oranlar (107/2): süreli hapiste kural **yarı**; ağırlaştırılmış müebbet 30 yıl, müebbet 24 yıl; 7242 (2020) ile sayılan suçlarda (kasten öldürme, TCK 87/2-d, işkence/eziyet, cinsel suçların bir kısmı, özel hayata karşı suçlar, devlet sırları vb.) **üçte iki**; örgüt suçlarında üçte iki (107/4). 
- Birden fazla cezada üst sınırlar (107/3: süreli hapislerde en fazla 28 yıl vb.).
- 15 yaşını doldurmayan çocuğun kurumda geçirdiği bir gün iki gün sayılır; istisnalar 7593 (2026) ile yeniden yazıldı (107/5). 
- **Mükerrirler (108):** tekerrürde süreli hapiste oran **üçte iki** (108/1-d). **İkinci defa tekerrürde** 7550 ile süreli hapislerde oran **dörtte üç** (108/3) ve 108/2'deki "eklenecek miktar en ağır cezayı geçemez" sınırı uygulanmaz. TCK 102/2, 103, 104/2-3 ve 188 hükümlülerinde süreli hapiste oran dörtte üç (108/9, 7242). 
- **Usul:** kurum idaresinin gerekçeli raporu infaz hâkimliğine verilir; hâkim dosya üzerinden karar verir; **itiraz** açık (107/11). 
- Disiplin cezaları kaldırılmadıkça koşullu salıverilme yapılmaz (5275 m.48/3-b) → `infaz-hakimligi-sikayet-ve-disiplin.md`. 
- Denetim süresi, kurumda geçirilmesi gereken süre kadardır (107/6); ihlalde geri alma (107/12-13); geri alma kararına itiraz (107/15).

## C. Tahmini tarih hesabı (araç)

`legal_estimate_parole_dates` ile hesaplanır. Araç yanıt vermezse ya da hata dönerse tarih **elle hesaplanmaz**; müddetnamedeki tarihler esas alınır ve kullanıcıdan müddetname istenir. Araç müddetname yöntemiyle hesaplar: ceza güne çevrilir (ay 30, yıl 365 gün), oran uygulanır ve günün arta kalanı atılır; kalan sürenin tam yılları giriş tarihine **takvim yılı** olarak eklenir (TCK m.61/6; Yargıtay 1. CD E.2023/8221 K.2024/4058). Kullanıcının müddetnamesiyle tarih farkı çıkarsa önce bu yöntemle karşılaştır; artık yılın bir yıl sayılmaması itiraz konusudur. 

Araç varsa:
- Girdi: her hüküm ayrı `cezalar[]` satırı (`tur`, `yil`/`ay`/`gun`, `suc_tarihi`, `tck_madde` fıkra ve bendiyle: `"102/2"`, `"87/2-d"`; `orgut`, `tmk`, `tekerrur` 0/1/2), `infaz_baslangic`, `mahsup_gun`, gerekiyorsa `dogum_tarihi`, `cinsiyet`, `cocuk_0_6`, `agir_hastalik_raporu`, `adli_paradan_cevrilme`. Bilinmeyen girdi uydurulmaz; eksikse aracın uyarısını aktar.
- Çıktı: `kosullu_saliverilme`, `denetimli_serbestlik_en_erken`, `hakederek_tahliye`, `denetim_suresi_bitis`, kalem kalem oran ve dayanak, `uygulanan_gecis`, `uyarilar`. Uyarıları kısaltmadan aktar; `[doğrulayın]` işaretli olanlar `[doğrula]` etiketi alır.
- **Müddetnameyle karşılaştır:** araç tarihi ile müddetname arasında birkaç günden fazla fark varsa farkın kaynağını ara (oran, mahsup, toplama sınırı, geçiş hükmü, çocukluk günleri). Fark müddetname aleyhineyse itiraz yolu 4675 m.5 → `infaz-hakimligi-sikayet-ve-disiplin.md` `[incele]`.
- Araç kesin tarih vermez: sonucu dilekçeye "tahmini" notuyla aktar; dilekçedeki "İNFAZ SÜRELERİ" satırları **müddetnameden** doldurulur.
- Araç sınırları: 3713 m.17 terör rejimi, koşullu salıverilmenin geri alınması, disiplin cezasının etkisi ve dosyalar arası artık mahsup hesaplanmaz.

### Hükümlü yakınına sade anlatım ("ne zaman çıkar?")
Avukat olmayan kullanıcı (hükümlü yakını) için çıktı:
1. En üstte: "Bu tarihler tahminidir; kesin tarihleri cezaevi ya da Cumhuriyet başsavcılığının hazırladığı **müddetname** gösterir. Müddetnameyi hükümlü cezaevinden, avukatı UYAP'tan alabilir."
2. Üç tarih, sade adlarıyla: **denetimli serbestlikle en erken çıkış** (şartları: iyi hâl, talep, çoğu durumda açık cezaevi), **koşullu salıverilme** (iyi hâl ve infaz hâkimi kararı), **cezanın tamamen bittiği gün**. Her birinin yanında bir cümlelik şart.
3. Tarihi etkileyen ve kullanıcının bilmediği bilgiler `[___]` olarak sorulur (suç tarihi, suç maddesi, tutuklulukta geçen gün).
4. 🔴 Belirsizlik varsa (birden çok dosya, tekerrür, örgüt, çocukken işlenen suç, 2020 ve 2023 geçiş hükümleri): "Bu durumda tarih hesabı karmaşıktır; avukat ya da baro adli yardım bürosu" yönlendirmesi.
5. Kesin söz verme: "şu tarihte çıkar" denmez; "en erken … tarihinde başvurabilir" denir.

## Süre
- 105/A: talep, koşullu salıverilmeye bir yıl (ya da 2/3 yıl) kalınca; sabit başvuru süresi yok.
- Ret kararına **itiraz**: 105/A'da ayrı itiraz hükmü yok; karar infaz hâkimince verildiğinden (105/A/1) **4675 m.6/5** (infaz hâkimi kararlarına tebliğden itibaren iki hafta, CMK hükümlerine göre itiraz; mercii ağır ceza mahkemesi, m.6/6) ve **CMK m.268/1** (öğrenmeden itibaren iki hafta) birlikte gözetilir. Başlangıç farkı içtihatla teyit edilmedi: **öğrenme tarihinden itibaren iki hafta** içinde itiraz et; ihtilafta güncel Yargıtay kararlarını `legal_search_cases` ile ara. 
- Koşullu salıverilme reddine itiraz: 107/11 ("itiraz yoluna gidilebilir") → iki hafta `[doğrula]`.

## Görüşme soruları
1. Hükümlü: ad, T.C., kurum (açık/kapalı), ilam(lar) `[___]`
2. Müddetname: toplam ceza, koşullu salıverilme tarihi, hak ederek tahliye tarihi, denetimli serbestliğe hak kazanma tarihi (müddetnamede yazan)?
3. Suç tarihi(leri) — 31.7.2023 öncesi mi, 4.6.2025 sonrası mı? (geçiş hükümleri)
4. Suç türü (107/2 ve 107/4 kapsamı, örgüt, terör), tekerrür?
5. Disiplin cezası var mı, kaldırıldı mı?
6. Ödenmemiş adli para cezası nedeniyle hapse çevrilen ceza var mı?
7. 0-6 yaş çocuk, ağır hastalık/engellilik/yaşlılık (ATK raporu)?
8. Tahliye sonrası ikamet adresi?

## soorgla adımları
```
legal_search_statute  query: "denetimli serbestlik"  law_no: "5275"  article_no: "105/A"
legal_get_statute_article  law_no: "5275"  article_no: "107" | "108" | "48" | "geçici 10" | "geçici 11"
legal_search_official_gazette  query: "Ceza ve Güvenlik Tedbirlerinin İnfazı"  date_from: "2025-01-01"  search_in: "all"  sort_by: "date_desc"
legal_search_statute_semantic  sorgu: "denetimli serbestlik tedbiri uygulanarak cezanın infazı yönetmelik başvuru"  mevzuat_tur: "cb_yonetmeligi"
legal_search_cases  sorgu: "105/A denetimli serbestlik talebinin reddi açık ceza infaz kurumuna ayrılma şartı"  tarih_baslangic: <son 3 yıl>
legal_get_case_document  belge_id: <seçilen karar>
```

## Dilekçe iskeleti — denetimli serbestlik talebi
```
[İL] İNFAZ HÂKİMLİĞİNE
Gönderilmek üzere [AÇIK CEZA İNFAZ KURUMU] MÜDÜRLÜĞÜNE

HÜKÜMLÜ : [Ad Soyad], T.C. [___], Baba adı [___], [ilam/dosya]
KONU    : 5275 s. Kanun m.105/A uyarınca cezamın koşullu salıverilme tarihine kadar olan kısmının
          denetimli serbestlik tedbiri uygulanarak infazı talebimdir.
İNFAZ SÜRELERİ (müddetnameye göre):
 Toplam ceza: [___] · Koşullu salıverilme tarihi: [___] · Denetimli serbestlik tarihi: [___]
AÇIKLAMALAR
1. Açık kurumdayım / açık kuruma ayrılma şartlarını taşıdığım hâlde iradem dışında ayrılamadım (105/A/1-2).
2. Koşullu salıverilmeme [___] gün kalmıştır ([1 yıl | 2 yıl — 0-6 yaş çocuk | 3 yıl — sağlık]).
3. [4.6.2025 sonrası suç ise] Kurumda geçirmem gereken sürenin onda birini geçirdim.
4. İyi hâlliyim; disiplin cezam yoktur / kaldırılmıştır.
5. Adli para cezasından çevrilen hapis cezam yoktur.
6. Belirlenecek yükümlülüklere uyacağımı beyan ederim.
DENETİM SÜRESİNCE İKAMET ADRESİ: [___]
HUKUKİ NEDENLER: 5275 m.105/A, 107 [MCP'den çekilmiş]
SONUÇ VE İSTEM : Cezamın denetimli serbestlik tedbiri uygulanarak infazına karar verilmesini saygıyla talep ederim.
```

## Sık hatalar
- 🔴 7550 "onda bir" şartını 4.6.2025 öncesi suçlara uygulamak (ya da sonrakilere uygulamamak).
- Kapalı kurumdaki hükümlü için 105/A/2 şartlarını göstermeden başvurmak.
- Müddetnamedeki tarihleri kendi hesabıyla değiştirmek; fark varsa müddetnameye itiraz ayrı yoldur (4675 m.5). Araç sonucu da müddetnamenin yerine geçmez.
- Geçici 10/6'yı bütün kasten öldürme suçlarına kapalı sanmak: istisna kasten öldürmeden yalnız TCK 82/1-d, e, f'yi sayar. 
- Hükümlü yakınına "şu tarihte çıkar" diye kesin tarih vermek.
- Disiplin cezasının etkisini atlamak.
- "Koşullu salıverilme" ile "denetimli serbestlik"i aynı başvuru sanmak.

