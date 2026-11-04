# İdari yargıda istinaf ve temyiz (İYUK m.45-50, m.20/A)

İdare ve vergi mahkemesi kararlarına karşı bölge idare mahkemesine (BİM) istinaf; BİM'in temyize açık kararlarına ve Danıştay dava dairelerinin nihai kararlarına karşı Danıştay'a temyiz; ivedi yargılama usulüne tabi davalarda doğrudan temyiz.

Bu dosya usulü verir; işlemin esası (imar, personel, ihale, vergi) ilgili alan becerisindedir (`../../idare-davalari-imar/SKILL.md`, `../../kamu-personeli/SKILL.md`, `../../kamu-ihale/SKILL.md`, `../../hakedis/SKILL.md`, `../../vergi/SKILL.md`; tüketici İPC'si → `../../tuketici/SKILL.md`, Rekabet Kurulu → `../../sirketler-ticaret/SKILL.md`). İlk derece idari dava dilekçesi → `../../idare-davalari-imar/references/idari-dava-dilekcesi.md`. KVKK Kurul kararı ve idari para cezası davasında esas → `../../kvkk/SKILL.md`; SGK İPC davasında esas → `../../sosyal-guvenlik-sgk/SKILL.md`.

**Güncellik uyarısı:** İYUK m.45 ve m.46 2024'te (7524) ve **16.7.2026'da (7589)** değişti. Her işte maddeleri yeniden çek. 

## Ne zaman kullanılır

### İstinaf (İYUK m.45)
- İdare ve vergi mahkemesi kararlarına karşı, mahkemenin bulunduğu yargı çevresindeki BİM'e (m.45/1).
- **Kesin kararlar:** konusu madde metnindeki tutarı geçmeyen vergi davaları, tam yargı davaları ve iptal davaları hakkındaki kararlar kesindir (m.45/1 ikinci cümle). Tutarı beceriye yazma; `legal_get_social_parameters` (`tur: "iyuk_istinaf_siniri"`, temyiz için `"iyuk_temyiz_siniri"`) ile o yılın sınırını çek, dava tarihine göre uygula.   Madde metnindeki tutar her yıl İYUK ek m.1 uyarınca VUK mükerrer 298 yeniden değerleme oranıyla artırılır; güncel sınırı o yılın ilanından al. 
- **İvedi yargılama usulüne tabi davalarda istinaf yoktur** (m.45/8) → doğrudan temyiz (m.20/A). 
- Dilekçedeki hitap ve isteğe bakılmaksızın istinafa tabi kararlardaki başvurular BİM'e gönderilir (m.45/2) — yanlış merci yazmak başvuruyu düşürmez, ama doğru yaz.

### Temyiz (İYUK m.46)
- Danıştay dava dairelerinin nihai kararları ile BİM'lerin m.46/1'de **sayılan** davalardaki kararları Danıştay'da temyiz edilebilir: düzenleyici işlemlere karşı iptal davaları; konusu madde metnindeki tutarı aşan vergi, tam yargı ve iptal davaları; meslekten/kamu görevinden/öğrencilikten çıkarma; ticari faaliyeti süresiz ya da metindeki süreden uzun engelleme; müşterek kararname ve daire başkanı ve üstü atamalar; imar planları ve parselasyon; koruma kurulları ve Boğaziçi; maden, orman, jeotermal; ülke çapındaki sınavlar; kıyı tesisleri; YİD/Yİ; serbest bölgeler; 5403; düzenleyici ve denetleyici kurul kararları. 
- **Yeni (m.46/2, 7589):** m.46/1 dışındaki davalarda BİM ilk derece kararını **kaldırıp yeniden** karar verdiyse bu karar da Danıştay'da temyiz edilebilir; istisnalar: tek hâkimle görülen davalar, 4081, 3091, 6458 (yabancılar) davaları, fark tutarı m.45/1 sınırını geçmeyenler, yalnız vekâlet ücreti/yargılama giderine ilişkin kararlar. Yürürlük ve geçiş kuralını kontrol et.   
- BİM'in m.46'ya göre temyize açık olmayan kararları **kesindir** (m.45/6). 

## Süre ve dayanağı

| Süre | Başlangıç | Dayanak | MCP |
|---|---|---|---|
| İstinaf: **otuz gün** | Kararın tebliği | İYUK m.45/1  | `legal_calculate_deadline` `iyuk_appeal` |
| Temyiz: **otuz gün** | Kararın tebliği | İYUK m.46/1, m.46/2  | `legal_calculate_deadline` `iyuk_cassation` |
| İvedi yargılamada temyiz: **on beş gün** | Nihai kararın tebliği | İYUK m.20/A (g)  | araç tanımıyor ("iyuk_ivedi_temyiz" → Kural bulunamadı) → elle |
| Temyize (ve istinafa) cevap: **otuz gün** | Dilekçenin tebliğini izleyen gün | İYUK m.48/3 (istinafta m.45/2 yollamasıyla)  | elle |
| Dilekçe eksikliğini tamamlama: **on beş gün** | Bildirimin tebliği | İYUK m.48/2 | elle |
| Harç/gider tamamlama: **yedi gün** | Bildirim | İYUK m.48/6 | elle |
| BİM'in m.48/7 kararlarına (süre, harç, kesinlik reddi) temyiz: **yedi gün** | Tebliği izleyen gün | İYUK m.45/2 son cümle; m.48/6  | elle |

m.20/A'yı `legal_get_statute_article` (`law_no: "2577"`, `article_no: "20/A"`) ile çek; boş dönerse `legal_search_statute_semantic` (`mevzuat_no: "2577"`). 
İvedi yargılamaya tabi işlerin listesi m.20/A/1'dedir: ihaleden yasaklama hariç ihale işlemleri, acele kamulaştırma, Özelleştirme Yüksek Kurulu kararları, 2634 sayılı Kanun uyarınca satış-tahsis-kiralama, idari yaptırım hariç ÇED kararları, 6306 uyarınca alınan Cumhurbaşkanı kararları; süreler 20/A/2'den. 

## Zorunlu unsurlar ve şekil
- Temyiz dilekçesi **Danıştay Başkanlığına hitaben** yazılır ve İYUK m.3 esaslarına göre düzenlenir; dilekçe kararı veren BİM'e, Danıştay'a ya da m.4'teki mercilere verilir (m.48/1-3). İstinaf temyizin şekil ve usullerine tabidir (m.45/2). 
- m.3/2 unsurları (temyiz/istinafa uyarlanarak): taraflar, vekiller, adresler, gerçek kişilerin T.C. kimlik no'su; konu, sebepler ve deliller; (davada işlemin, kanun yolunda kararın) tebliğ tarihi; vergi ve tam yargı davalarında uyuşmazlık miktarı; vergi davalarında vergi türü, yılı, ihbarname tarih ve sayısı. Ekler karşı taraf sayısından bir fazla örnek (m.3/3). İmzalı dilekçe (m.3/1). 
- **Yürütmenin durdurulması** isteniyorsa temyiz dilekçesinde açıkça iste; dosya tebliğe çıkarılmadan Danıştay'a gönderilir (m.48/5). 
- Karşı taraf cevap dilekçesinde, kendi süresini kaçırmış olsa bile temyiz isteminde bulunabilir (m.48/3).

## İstinaf ve temyiz sebepleri
- **İstinaf (m.45/3-5):** BİM kararı hukuka uygun bulursa ret (gerekçe değiştirme ya da maddi hata düzeltme dahil); uygun bulmazsa **kaldırıp esas hakkında yeniden karar**; yalnız m.45/5'te sayılan hâllerde (usule ilişkin nihai kararlar, görev/yetki, reddedilmiş/yasaklı hâkim, dilekçe reddi gerekirken karar, yanlış hasım, talep hakkında karar verilmemesi, keşif/bilirkişi ya da duruşma yapılmaması) **kaldırıp geri gönderme** (kesin). 
- **Temyiz (m.49/2):** a) görev ve yetki dışında bir işe bakılması, b) hukuka aykırı karar verilmesi, c) usul hükümlerinin uygulanmasında kararı etkileyebilecek hata veya eksiklik. 
- Eski YAML Danıştay'ı yalnız adıyla anıyordu ("Yargıtay/Danıştay başvuru dilekçesi"); idari yargıya özgü süre, sınır ve sebep hiç yoktu. Bu dosya o boşluğu doldurur.

## "Kararın düzeltilmesi" yolu yok
İYUK m.54 (kararın düzeltilmesi) **mülgadır** (6545, 2014). Kullanıcı "karar düzeltme" isterse bunu söyle; olağanüstü yol olarak yargılamanın yenilenmesi (m.53) ve kanun yararına temyiz (m.51) yalnız işaret edilir `[incele]`.  Görev talimatındaki "İYUK 54" atfı bu nedenle bir kanun yoluna karşılık gelmez.

## Görüşme soruları
1. Kararı veren mahkeme (idare/vergi mahkemesi, BİM dairesi, Danıştay dava dairesi), esas/karar no, karar tarihi?
2. Kararın tebliğ tarihi?
3. Dava türü (iptal, tam yargı, vergi) ve konusu; parasal değeri? (kesinlik ve m.46/1-b)
4. Dava m.20/A ivedi yargılamaya tabi mi (ihale, acele kamulaştırma, özelleştirme…)?
5. Tek hâkimle mi heyetle mi görüldü? (m.46/2-a)
6. BİM ne karar verdi: istinafın reddi, kaldırıp yeniden karar, kaldırıp geri gönderme?
7. Davacı/davalı idare, vekiller, adresler?
8. Hukuka aykırılık iddiaları ve karar gerekçesindeki pasajlar?
9. Yürütmenin durdurulması isteniyor mu? Teminat?

## soorgla çağrıları
```
legal_get_statute_article  law_no: "2577"  article_no: "45" | "46" | "48" | "49" | "3" | "53" | "54"
legal_search_statute_semantic  mevzuat_no: "2577"  sorgu: "ivedi yargılama usulü temyiz süresi"   # m.20/A
legal_calculate_deadline  kural_kodu: "iyuk_appeal" | "iyuk_cassation"  baslangic_tarihi: <tebliğ>
legal_get_social_parameters  tur: "harc_istinaf_bam" | "harc_temyiz_danistay"
legal_search_cases  mahkeme: "danistay"  sorgu: "<işlem + hukuka aykırılık>"  tarih_baslangic: <son 3 yıl>
legal_search_cases  mahkeme: "danistay"  daire: "İdari Dava Daireleri Kurulu" | "Vergi Dava Daireleri Kurulu"  sorgu: "<ilke>"
legal_get_case_document  belge_id: <seçilen güncel karar>
```

## Dilekçe iskeleti
```markdown
[___] BÖLGE İDARE MAHKEMESİ BAŞKANLIĞINA                 ← istinaf
  (temyizde: DANIŞTAY BAŞKANLIĞINA)
Gönderilmek üzere
[___] [___]. İDARE / VERGİ MAHKEMESİNE                     ← temyizde: [___] BÖLGE İDARE MAHKEMESİ [___]. İDARİ/VERGİ DAVA DAİRESİNE

DOSYA NO          : [___] E. — [___] K.
[İSTİNAF / TEMYİZ] EDEN ([davacı / davalı idare]) : [___], T.C./VKN [___], [adres]
VEKİLİ            : Av. [___]
KARŞI TARAF       : [___ idaresi], [adres]
KARARIN TEBLİĞ TARİHİ : [___]
KONU              : [___] tarihli kararın [istinaf yoluyla incelenerek KALDIRILMASI /
                    temyizen incelenerek BOZULMASI] [ve yürütmesinin durdurulması] talebidir.

AÇIKLAMALAR
  1. [İYUK m.49/2-(a/b/c) ya da m.45/5 hâli] — [karar gerekçesindeki pasaj] — [ihlal edilen kural]
  2. …
  Danıştay içtihatları: [soorgla'dan, en az bir güncel karar tam metni okunmuş]
HUKUKİ NEDENLER   : İYUK m.45 / m.46, m.49; [esasa ilişkin mevzuat]
SONUÇ VE İSTEM    : … kararın [KALDIRILARAK davanın KABULÜNE / BOZULMASINA], [yürütmenin
                    durdurulmasına], yargılama giderleri ve vekâlet ücretinin karşı tarafa
                    yükletilmesine karar verilmesini saygıyla arz ve talep ederim.
                                         [tarih] — Av. [___] (e-imza)
```

## Sık hatalar
- 🔴 Adli yargıdaki "iki hafta"yı idari yargıya taşımak (idari yargıda otuz gün; ivedi yargılamada on beş gün).
- 🔴 İvedi yargılamaya tabi davada istinafa gitmek (m.45/8).
- 🔴 m.46/1 dışında kalan BİM kararını temyiz etmek (m.45/6) — 2026 tarihli m.46/2 istisnasını ayrıca kontrol et.
- 🟠 "Karar düzeltme" istemek (m.54 mülga).
- 🟡 Yürütmenin durdurulması istemini dilekçeye yazmamak.

