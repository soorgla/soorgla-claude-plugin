# Görevden uzaklaştırma ve memur yargılaması (4483)

## Ne zaman kullanılır
- Memur görevden uzaklaştırıldı ("açığa alındı"); süre, aylık, iade ve dava yolu soruluyor.
- İdare görevden uzaklaştırma tedbiri almak ya da kaldırmak istiyor.
- Memur hakkında suç ihbarı/şikâyeti var; 4483 ön incelemesi, soruşturma izni verilmesi/verilmemesi, işleme koymama kararı ve bunlara itiraz.

**Sınır:** soruşturma izni verildikten sonraki ceza soruşturması ve kovuşturması (ifade, tutuklama, iddianame, savunma) → `../../ceza-ve-infaz-dilekce/SKILL.md`. Paralel disiplin süreci → `disiplin-sorusturmasi-ve-cezalar.md`.

**Araç notu:** 4483 numarasını 1943 tarihli İzmir Tramvay kanunu da taşıyor. `legal_get_statute_article` (`law_no: "4483"`, `law_type: "Kanun"`) doğru kanunu (`statute_id 39868`) döndürür, tramvay kanunu `other_candidates`'ta gelir; `legal_list_statute_articles` için `statute_id: 39868` ver (yalnız `law_no` ile "ambiguous" döner).

---

## A. Görevden uzaklaştırma (657 m.137-145)

| Konu | Kural | Dayanak |
|---|---|---|
| Niteliği | Görevi başında kalmasında sakınca görülen memur hakkında **ihtiyati tedbir**; soruşturmanın her safhasında alınabilir | 657 m.137 |
| Yetkililer | Atamaya yetkili amir; bakanlık ve genel müdürlük müfettişleri; illerde vali; ilçelerde kaymakam (ilçe idare şube başkanları için valinin muvafakati); vali/kaymakam tedbiri kuruma derhal bildirir | 657 m.138 |
| Soruşturmaya başlama | Uzaklaştırmayı izleyen **10 iş günü** içinde soruşturmaya başlanması şart; keyfî ya da garazla tedbir alan amir hukuki, mali, cezai sorumlu | 657 m.139 |
| Ceza kovuşturması | Hakkında mahkemece cezai kovuşturma yapılan memur da uzaklaştırılabilir | 657 m.140 |
| Süre | Disiplin kovuşturması icabıysa **en çok 3 ay**; sonunda karar yoksa memur göreve başlatılır. Ceza kovuşturması icabıysa yetkili amir **her iki ayda bir** durumu inceleyip göreve dönüş hakkında karar verir ve yazıyla tebliğ eder | 657 m.145 |
| Kaldırma | Disiplin ya da cezai işlem gerekmeyenler için derhal kaldırılır; kaldırmayan hakkında m.139 uygulanır | 657 m.142 |
| Göreve iade zorunlu hâller | Çıkarma dışında disiplin cezası; yargılamanın men'i ya da beraat; genel af; memurluğa engel olmayan ve ertelenen ceza — kararların kesinleşmesi üzerine | 657 m.143 |
| Takdirle kaldırma | Fiiller hizmete devama engel değilse her zaman kaldırılabilir | 657 m.144 |
| Uzaklaştırma süresince aylık ve haklar | Aylığın üçte ikisi ödenir, sosyal hak ve yardımlar sürer; m.143 hâllerinde kesilen üçte bir ödenir ve süre kademe ilerlemesinde değerlendirilir (m.141); m.146 ve sonrası | 657 m.141 |
| Yerine vekil | Görevden uzaklaştırma nedeniyle ayrılan memurun yerine vekil atanabilir | 657 m.86 |
| Sendika yöneticisi | Görevden uzaklaştırılan sendika yöneticisinin mahkemeye başvurması hâlinde karar kesinleşinceye kadar sendikadaki görevi devam eder | 4688 m.18 son fıkra |

### Kontrol listesi — memur tarafı
1. Tedbir **yazılı** mı, kim aldı, yetkili mi (m.138)?
2. 10 iş günü içinde soruşturma başladı mı (m.139)? Başlamadıysa 🟠 — tedbirin hukuka aykırılığı ve amir sorumluluğu `[incele]`.
3. Dayanak disiplin mi ceza mı? Disiplinse **3 ay** doldu mu (m.145)? Doluysa göreve başlatılma talebi (yazılı başvuru; cevapsızlıkta İYUK m.10 → `personel-davasi-usul-ve-sureler.md`).
4. Ceza kovuşturmasıysa 2 aylık periyodik değerlendirmeler yapılıp tebliğ edildi mi? Her değerlendirme ayrı bir işlem olarak dava konusu olabilir `[incele]`.
5. Gerekçe somut mu ("görevi başında kalmasında sakınca") yoksa kalıp ifade mi?
6. Aylık ödemeleri doğru mu (m.141) `[doğrula]`.
7. Dava: iptal + yürütmenin durdurulması (telafisi güç zarar argümanı güçlüdür); süre 60 gün (2577 m.7) → dilekçe `../../idare-davalari-imar/references/idari-dava-dilekcesi.md`.

### Kontrol listesi — idare tarafı
1. Tedbiri alan makamın yetkisini yaz (m.138).
2. Somut gerekçe: delillerin karartılması, tanıkları etkileme, hizmetin aksaması, kamu güveni.
3. **10 iş günü içinde soruşturma oluru** — takvime işle 🔴.
4. Disiplin icabı ise 3 ayın son gününü yaz; ceza icabı ise 2 ayda bir değerlendirme takvimi.
5. Tedbir kaldırma şartları gerçekleşince derhal kaldır (m.142-143); gecikme m.139 sorumluluğu doğurur.

---

## B. Memur yargılaması — ön inceleme ve soruşturma izni (4483)

| Konu | Kural | Dayanak |
|---|---|---|
| Kapsam | Memur ve diğer kamu görevlilerinin **görevleri sebebiyle** işledikleri suçlar; ağır cezayı gerektiren suçüstü hâli genel hükümlere tabi; disiplin hükümleri saklı | 4483 m.2 |
| Başvuru | Cumhuriyet başsavcılığı kapsamdaki suçlarda yetkili merciden izin ister; diğer makamlar öğrendikleri suçu yetkili mercie iletir | 4483 m.4 |
| Ön inceleme | Görevlendirilen kişi(ler) müfettiş ve görevlendiren merciin yetkilerine sahip; rapor üzerine merci izin verir ya da vermez | 4483 m.6 |
| Karar süresi | Yetkili merci kararını suçun öğrenilmesinden itibaren **ön inceleme dahil en geç 30 gün** içinde verir; zorunlu hâllerde bir defaya mahsus en çok **15 gün** uzatılabilir | 4483 m.7 |
| İznin kapsamı | İzin olay ve bağlantılı konuları kapsar; tamamen ayrı bir suç ortaya çıkarsa yeni izin gerekir; hukuki nitelendirmenin değişmesi yeni izin gerektirmez | 4483 m.8 |
| İtiraz | İzin verilmesine karşı memur; verilmemesine karşı başsavcılık ya da şikâyetçi; **işleme koymama** kararına karşı şikâyetçi itiraz eder. Süre: **tebliğden 10 gün**. Merci: m.3/(e), (f), (g) (Cumhurbaşkanınca verilen izin hariç) ve (h) bentlerindekiler için **Danıştay İkinci Dairesi**, diğerleri için yetkili merciin yargı çevresindeki **bölge idare mahkemesi**. En geç 3 ayda karar; **kesin** | 4483 m.9 |
| Kesinleşme sonrası | Dosya derhal yetkili başsavcılığa; savcılık CMK'ya göre soruşturur | 4483 m.11 |
| Haksız isnat | İftira amaçlı uydurma ihbarda re'sen soruşturma; memurun tazminat davası hakkı saklı | 4483 m.15 |
| Soruşturmacıya karşı tazminat | Ön inceleme, disiplin soruşturması ya da denetim görevlisinin işlem ve raporlarından dolayı tazminat davası **yalnız idare aleyhine** açılır; kin, garez ya da suç kesinleşmiş kararla saptanırsa idare rücu eder | 4483 ek m.1 (6745, 2016) |
| Anayasal dayanak | Kamu görevlileri hakkında ceza kovuşturması, kanunla belirlenen istisnalar dışında idari merciin iznine bağlıdır | Anayasa m.129/6 |

**Kapsam dışı (izin gerekmez):** görevle ilgisi olmayan kişisel suçlar; özel soruşturma usulüne tabi olanlar ve suçun niteliği yönünden özel usul öngörülenler (4483 m.2/2); ağır cezalık suçüstü hâli (m.2/3); 3628 m.17 kapsamı: irtikâp, rüşvet, basit ve nitelikli zimmet, görev sırasında ya da görevden dolayı kaçakçılık, resmî ihale ve alım-satıma fesat karıştırma, Devlet sırlarını açıklama ile 3628 ve Bankalar Kanunu suçları — müsteşar, vali ve kaymakamlar hariç `[incele]`. **Yükseköğretim:** YÖK ve YÖDK üyeleri, yükseköğretim kurumu yöneticileri, kadrolu ve sözleşmeli öğretim elemanları ve bu kurumların 657'ye tabi memurları için görev suçlarında 2547 m.53/c'deki özel soruşturma usulü uygulanır (ilk soruşturma disiplin amiri ya da görevlendirdiği soruşturmacı; son soruşturmanın açılıp açılmamasına unvana göre YÖK, rektörlük ya da üniversite yönetim kurulu üyelerinden oluşan kurullar, memurlarda il idare kurulu karar verir; itiraz Danıştay 2. Daire); 2547'de hüküm bulunmayan hâllerde 4483 uygulanır (m.53/c-8). İdeolojik suçlar, boykot/işgal ve ağır cezalık suçüstünde savcı doğrudan kovuşturur (m.53/c-7).

**Yetkili merci (m.3):** suç tarihindeki göreve göre — ilçede kaymakam; ilde ve merkez ilçede vali (kaymakamlar için de vali); bölge teşkilatında görev yapılan ilin valisi; bakanlık ve Cumhurbaşkanlığına bağlı kuruluşların merkez teşkilatında **o kuruluşun en üst idari amiri**; Cumhurbaşkanı kararıyla atananlar için Cumhurbaşkanı ya da ilgili bakan; belediye başkanları ve meclis üyeleri için İçişleri Bakanı (belde için kaymakam/vali); TBMM ve Cumhurbaşkanlığı personeli için ayrı merciler. Ast ve üst aynı fiile katılmışsa üstün merciinden izin istenir. m.9'daki Danıştay 2. Daire/BİM ayrımı bu bentlere bağlıdır.

### Kontrol listesi — memur tarafı (izin verildi)
1. İzin kararının tebliğ tarihi → **10 gün** itiraz süresi 🔴.
2. Fiil görev sebebiyle mi işlenmiş (kapsam)? Değilse 4483 uygulanmaz; itiraz konusu da yoktur.
3. Ön inceleme yapıldı mı, ifade alındı mı, rapor gerekçeli mi?
4. Karar süresi (30 gün) aşıldı mı? Aşılmışsa sonuca etkisi `[incele]`.
5. İzin, ön incelemedeki olayı mı kapsıyor (m.8)?
6. Somut delil var mı, yoksa soyut iddia mı? Danıştay 2. Daire / BİM itiraz kararlarından son 3 yıl emsal.
7. Paralel görevden uzaklaştırma ve disiplin süreci (A bölümü ve `disiplin-sorusturmasi-ve-cezalar.md`).

### Kontrol listesi — şikâyetçi tarafı (izin verilmedi / işleme konmadı)
1. Tebliğ tarihi → 10 gün itiraz.
2. İşleme koymama kararı hangi gerekçeyle? İhbar/şikâyet soyut ve genel nitelikte olmamalı, kişi ya da olay belirtmeli, ciddi bulgu ve belgeye dayanmalı, dilekçede doğru ad-soyad, imza ve iş/ikametgâh adresi bulunmalı; iddialar şüpheye yer vermeyen belgelere dayanıyorsa kimlik/adres şartı aranmaz (m.4/3-4).
3. Ön inceleme yeterli mi; deliller toplanmış mı?

### Kontrol listesi — idare tarafı (yetkili merci ve ön incelemeci)
1. Öğrenme tarihi → 30 günlük karar süresinin son günü.
2. Kapsam testi: görev sebebiyle mi? Değilse dosyayı başsavcılığa iade.
3. Ön incelemeci görevlendirmesi; ilgilinin ifadesi; belgeler; rapor (farklı görüşler ayrı ayrı).
4. Karar gerekçeli; m.9 bildirimleri (başsavcılık, ilgili, şikâyetçi) ve itiraz yolu/süresi gösterilerek.

---

## Görüşme soruları

| Alan | Soru |
|---|---|
| Tedbir | Görevden uzaklaştırma yazısının tarihi, sayısı, imzalayan makam? Gerekçe? |
| Dayanak | Disiplin soruşturması mı, savcılık soruşturması/kovuşturması mı? |
| Takvim | Soruşturma oluru ne zaman verildi? Kaç aydır uzaklaştırılmış durumdasınız? |
| 4483 | Ön inceleme yapıldı mı, ifadeniz alındı mı? İzin kararı ne zaman tebliğ edildi? |
| Aylık | Uzaklaştırma süresince aylığınız nasıl ödeniyor? |
| Sendika | Sendika yöneticisi/temsilcisi misiniz? |

---

## soorgla çağrıları

```
legal_list_statute_articles law_no: "657" law_type: "Kanun" article_query: "görevden uzaklaştırma" include_content: true
legal_get_statute_article law_no: "657" law_type: "Kanun" article_no: "141"
legal_get_statute_article law_no: "4483" law_type: "Kanun" article_no: "<2 | 3 | 4 | 6 | 7 | 9>"
legal_search_statute_semantic mevzuat_no: "4483" sorgu: "<kapsam | yetkili merci | ön inceleme | karar süresi | işleme koymama>" # konu araması
legal_search_cases sorgu: "4483 soruşturma izni verilmesine itiraz görev sebebiyle somut delil" mahkeme: "danistay" tarih_baslangic: "<3 yıl önce>"
legal_search_cases sorgu: "<aynı>" mahkeme: "bam"
legal_search_cases sorgu: "görevden uzaklaştırma tedbiri üç ay disiplin kovuşturması iptal" mahkeme: "danistay"
```

---

## Çıktı iskeleti — 4483 itiraz dilekçesi (memur)

```markdown
[TASLAK — gönderilmeden önce avukat incelemesi]

DANIŞTAY İKİNCİ DAİRESİ BAŞKANLIĞINA / [___] BÖLGE İDARE MAHKEMESİ BAŞKANLIĞINA [merci m.3 bendine göre — doğrula]
(Soruşturma izni veren [merci] aracılığıyla)

İTİRAZ EDEN : [ad soyad, T.C. kimlik no, unvan, görev yeri]
İTİRAZ EDİLEN KARAR : [merci], [tarih], [sayı] — soruşturma izni verilmesine ilişkin karar
TEBLİĞ TARİHİ : [___]

AÇIKLAMALAR: [fiilin görevle ilgisi; ön incelemenin yetersizliği; somut delil yokluğu; ifade alınmaması]
HUKUKİ NEDENLER: 4483 m.2, 6, 7, 9; Anayasa m.129
SONUÇ VE İSTEM: Soruşturma izni verilmesine ilişkin kararın kaldırılmasına karar verilmesini arz ederim.
[tarih, imza]
```

---

## Sık hatalar
- 4483 itirazını 60 günlük idari dava sanıp 10 günü kaçırmak.
- 4483 iznine karşı idare mahkemesinde iptal davası açmak (yol özel itirazdır, karar kesindir).
- Görevden uzaklaştırmada 3 aylık disiplin sınırını ceza kovuşturması icabı alınan tedbire uygulamak (orada 2 ayda bir değerlendirme var).
- 10 iş günü içinde soruşturma başlatmamak (idare).
- Muhakkike ya da ön incelemeciye kişisel tazminat davası açmak (yalnız idare aleyhine; 4483 ek m.1).
- 4483 m.1-7'yi `legal_get_statute_article` ile çekip başka kanunun metnini alıntılamak.
