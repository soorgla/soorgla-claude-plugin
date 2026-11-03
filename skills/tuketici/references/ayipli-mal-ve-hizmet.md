# Ayıplı mal ve ayıplı hizmet

## Ne zaman kullanılır
- **Tüketici tarafı:** satın alınan mal (telefon, beyaz eşya, sıfır ya da ikinci el araç, konut) ya da alınan hizmet (tadilat, kurs, kuru temizleme, oto servis) ayıplı; satıcı/sağlayıcı/servis çözmüyor. Hangi seçimlik hak, kime karşı, hangi yoldan.
- **İşletme tarafı:** satıcı, üretici, ithalatçı ya da yetkili servis tüketicinin talebine cevap verecek; "değişim mi onarım mı", "orantısız güçlük savunması tutar mı", "garanti bitti, sorumlu muyuz".
- Ayıplı malın **kişiye ya da başka mala verdiği zarar** (yanan şarj aleti evi yaktı) → ayrıca `../../tazminat-haksiz-fiil/references/urun-sorumlulugu.md`.
- Yol ve usul (THH mi, arabuluculuk mu) → `hakem-heyeti-ve-tuketici-davasi.md`.

---

## Süreler ve dayanakları

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Ayıplı maldan sorumluluk zamanaşımı: **2 yıl**; konut/tatil amaçlı taşınmazda **5 yıl** | Malın **teslimi** (ayıp sonra çıksa bile) | 6502 m.12/1 | Kanun ya da sözleşmede daha uzun süre olabilir. Ayıp ağır kusur ya da hileyle gizlenmişse zamanaşımı işlemez (m.12/3). |
| İkinci el satışta satıcının sorumluluğu en az **1 yıl** (taşınmazda **3 yıl**) — kısaltılamaz | Teslim | 6502 m.12/2 | Ayıba ilişkin etiket/fatura açıklaması (m.10/3) saklı. |
| Ayıplı hizmetten sorumluluk zamanaşımı: **2 yıl** | Hizmetin **ifası** | 6502 m.16 | Hile/ağır kusurda zamanaşımı yok. |
| İspat karinesi: **6 ay** içinde çıkan ayıp teslimde var sayılır | Teslim | 6502 m.10/1 | Malın ya da ayıbın niteliğiyle bağdaşmıyorsa karine uygulanmaz `[incele]`. |
| Ücretsiz onarım / misliyle değişim: **en çok 30 iş günü**; konut/tatil taşınmazında **60 iş günü** | Talebin satıcı/üretici/ithalatçıya yöneltilmesi | 6502 m.11/4 | Aşılırsa tüketici diğer seçimlik haklara geçer. Yönetmelik listesindeki mallarda azami tamir süresi ayrıca (m.58/3) → Satış Sonrası Hizmetler Yönetmeliği `[doğrula]`. |
| Ayıplı hizmette yeniden görme/onarım: **30 iş günü** | Talep | 6502 m.15/4 | |
| Garanti süresi: **asgari 2 yıl** (yenilenmiş üründe asgari 1 yıl) | Teslim | 6502 m.56/2, m.57/A/2 | Bakanlık bazı mallarda başka ölçü birimi (km, saat) belirleyebilir. Garanti süresi ile zamanaşımını karıştırma. |

`legal_calculate_deadline` bu süreleri tanımaz; elle hesapla, `legal_check_holiday` ile son günü kontrol et, `[doğrula]`.

**Ayıp ihbarı:** 6502'nin ayıplı mal bölümünde (m.8-12) tüketiciye ihbar süresi yükleyen bir hüküm yoktur; eski YAML'daki "açık ayıpta teslimde ihtirazi kayıt konulmalıydı" kuralı 4077 dönemine aittir. Sınır m.10/2'dir: tüketici sözleşme kurulurken ayıbı biliyor ya da bilmesi bekleniyorsa sözleşmeye aykırılık yoktur. Ticari satışta (alıcı tacir) TTK m.23 ihbar süreleri geçerli → `../../sozlesme-incelemesi-tbk/SKILL.md`.

---

## Kontrol listesi

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| TÜK-SIFAT | Alıcı tüketici mi, satıcı ticari/mesleki amaçla mı hareket ediyor? İki kişi arasındaki ikinci el satış (ikisi de tüketici) 6502 kapsamında değildir → TBK m.219 vd. | 6502 m.3/1-k, (i), (l) | `[incele]` galerici-araç alım satımı, şirket adına fatura |
| AYIP-TÜRÜ | Ayıp: örnek/modele aykırılık; objektif özellik eksikliği; ambalaj, etiket, kılavuz, **internet portalı ya da reklamdaki** özelliklere aykırılık; maddi, hukuki ya da ekonomik eksiklik | 6502 m.8/1-2 | Hukuki ayıp (hacizli/rehinli araç) da ayıptır |
| GEÇ-TESLİM | Süresinde teslim edilmeme ya da satıcının yaptığı hatalı montaj da ayıp sayılır | 6502 m.8/3 | Mesafeli satışta ayrıca m.48/3 → `cayma-hakki-ve-mesafeli-satis.md` |
| REKLAM-BAĞLILIĞI | Satıcı kendi dışındaki reklamla bağlı mı? Haberdar olmadığını ve olmasının beklenemeyeceğini ya da sözleşmede düzeltildiğini ispatlarsa bağlı değil | 6502 m.9/2, m.14/2 | |
| KARİNE | Ayıp teslimden itibaren 6 ay içinde mi çıktı? Çıktıysa ispat satıcıda | 6502 m.10/1 | 6 aydan sonra ispat tüketicide → bilirkişi şart |
| BİLGİ | Tüketici ayıbı biliyor muydu, ayıplı mal etiketi/faturada açıklama var mı? | 6502 m.10/2-3 | Etiketli ayıp dışındaki ayıplara haklar sürer |
| SEÇİMLİK-HAK | Hangi hak: (a) dönme, (b) indirim, (c) ücretsiz onarım, (ç) ayıpsız misliyle değişim. Satıcı tüketicinin seçtiğini yerine getirmek zorunda | 6502 m.11/1 | İstemde **tek** hak ya da terditli sıra; aynı anda iki hak isteme |
| MÜTESELSİL | Onarım ve değişim üretici/ithalatçıya karşı da kullanılabilir; satıcı, üretici, ithalatçı müteselsilen sorumlu (dönme ve indirim yalnız satıcıya) | 6502 m.11/2 | Davalı seçimi buna göre |
| ORANTISIZLIK | Onarım ya da değişim satıcı için orantısız güçlük doğuruyor mu? Ölçüt: malın ayıpsız değeri, ayıbın önemi, diğer hakların tüketici için sorun yaratıp yaratmadığı | 6502 m.11/3 | Yargıtay: tüketicinin seçimi asıldır; hâkim ancak hak-nesafet dengesi aşırı bozuluyorsa müdahale eder; yargılama süresince artan km tüketici aleyhine yorumlanmaz `[incele]` |
| TAZMİNAT | Seçimlik hakla birlikte TBK'ya göre tazminat (değer kaybı, ikame araç, kira) | 6502 m.11/6 (malda), m.15/1 (hizmette) | Ürünün başka mala/kişiye zararı → tazminat-haksiz-fiil |
| GARANTİ-SONRASI | Garanti içinde onarım hakkı kullanıldıysa: tekrar arızalanma, azami tamir süresinin aşılması ya da tamir imkânsızlığı → diğer seçimlik haklar; satıcı reddedemez | 6502 m.56/3 | Garanti Belgesi Yönetmeliği'ndeki "aynı arızanın tekrarı" ölçütleri `[doğrula]` |
| İHTİYARİ-GARANTİ | "Ek garanti", "uzatılmış garanti" ilave taahhüttür; yasal hakları kısıtlayamaz; reklamdaki ifadelerle bağlar | 6502 m.57 | Ücretli uzatılmış garanti sigorta niteliğinde olabilir `[incele]` |
| HİZMET | Ayıplı hizmette haklar: yeniden görme, eserin ücretsiz onarımı, indirim, dönme; masraflar sağlayıcıda; orantısız güçlükte ilk ikisi kullanılamaz | 6502 m.13, m.15/1-2 | |
| SERVİS | Yetkili servis tamir süresi yönetmelik azamisini aşamaz; "özel servis" ibaresi zorunlu | 6502 m.58/3, m.58/5 | Servis fişleri en güçlü delildir |

---

## Araç ve konutta özel noktalar

- **Sıfır araçta boya/hasar:** 3. HD sıfır km araçtan beklenen faydanın azalmasını ayıp sayıyor ve misliyle değişime hükmeden kararları onaylıyor; değişim imkânsızsa bedel. Karar her olayda bilirkişi raporuna dayanır; boya kalınlığı ölçümü ve üretim kaynaklı olup olmadığı belirleyici.
- **Değişimde iade edilecek araç:** değişime karar verilirken tüketicinin kullanımı sırasında oluşan değer kaybı (kaza vb.) satıcıya ödenebilir `[incele]`.
- **Ticari kullanım (taksi, kiralık araç, şirket aracı):** tüketici sıfatı tartışmalıdır; asliye ticaret ve TTK ihbar süreleri gündeme gelir `[incele]`.
- **Konut ayıbı:** 5 yıllık zamanaşımı ve 60 iş günü onarım süresi; ön ödemeli konutta ayrıca `on-odemeli-konut-ve-devre-tatil.md`. Taşınmazın aynına ilişkin uyuşmazlıkta dava şartı arabuluculuk yok (m.73/A-1-d) → `hakem-heyeti-ve-tuketici-davasi.md`.
- **Hukuki ayıp (haciz, rehin, çalıntı kaydı):** satıcı dışında üretici sorumluluğu yoktur; dönme + tazminat genelde tek gerçekçi yol `[incele]`.

---

## Görüşme soruları

| Alan | Soru |
|---|---|
| Taraflar | Kimden aldınız (bayi, mağaza, internet, şahıs)? Fatura kimin adına? Ne amaçla aldınız (kişisel/işyeri)? |
| Mal/hizmet | Ne, hangi model, kaç TL? **Teslim** (hizmette ifa) tarihi? |
| Ayıp | Kusur ne, ne zaman ortaya çıktı? Satın alırken biliyor muydunuz? Fotoğraf/video var mı? |
| Başvurular | Satıcıya/servise ne zaman başvurdunuz? Servis fişleri, onarım sayısı, serviste kalma süresi? |
| Tercih | Ne istiyorsunuz: para iadesi, yenisi, ücretsiz onarım, indirim? Ek zararınız var mı (ikame araç, kira, iş kaybı)? |
| Kullanım | (Araçta) km, kaza kaydı, değişen parça var mı? |
| Değer | Uyuşmazlık değeri (THH sınırı için)? |
| İşletme tarafı | Talep ne zaman ulaştı? Ürün sizde mi? Servis raporu ne diyor? Üretici/ithalatçı bilgilendirildi mi? |

---

## soorgla çağrıları

```
legal_get_social_parameters tur: "thh_parasal_sinir"
legal_get_statute_article law_no: "6502" article_no: "3" | "8" | "9" | "10" | "11" | "12" | "13" | "15" | "16" | "56" | "57" | "58"
legal_list_statute_articles law_no: "6502" article_no: "57/A" include_content: true
legal_resolve_statute query: "Garanti Belgesi Yönetmeliği"
legal_resolve_statute query: "Satış Sonrası Hizmetler Yönetmeliği" # azami tamir süresi
legal_search_cases mahkeme: "yargitay" sorgu: "<olay: sıfır araç boya ayıbı misli ile değişim>" tarih_baslangic: "<son 3 yıl>"
legal_case_facets mahkeme: "yargitay" sorgu: "ayıplı mal tüketici seçimlik hak" tarih_baslangic: "<son 2 yıl>"
legal_get_case_document belge_id: <seçilen karar>
```

---

## Çıktı iskeleti — ayıp değerlendirmesi

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …

## Ayıplı [mal/hizmet] değerlendirmesi — [tüketici/satıcı] — [tarih]

### Sonuç
[Ayıp var/yok/bilirkişiye bağlı; önerilen seçimlik hak; yol: THH / arabuluculuk + tüketici mahkemesi]

### Süre tablosu
| Süre | Başlangıç | Son gün | Dayanak | Durum |
| Zamanaşımı (2/5 yıl) | Teslim [tarih] | … | 6502 m.12 | |
| 6 ay karinesi | Teslim | … | m.10/1 | içinde / dışında |
| 30 iş günü onarım | Talep [tarih] | … | m.11/4 | aşıldı / işliyor |

### Seçimlik haklar karşılaştırması
| Hak | Kime karşı | Artısı | Riski (orantısızlık, değer kaybı) |

### Delil listesi
[fatura, garanti belgesi, servis formları, yazışma, fotoğraf, ekspertiz/bilirkişi]

### Dayanaklar · Eksik bilgi · Kontrol listemde olmayan soru · Şimdi ne yapalım?
```

---

## Sık hatalar
- Garanti süresi doldu diye hakkın bittiğini sanmak (zamanaşımı ayrı, m.12).
- İki seçimlik hakkı aynı anda istemek; terditli sıra kurmamak.
- Dönme ve indirimi üreticiye yöneltmek (m.11/2 yalnız onarım ve değişim).
- 6 aydan sonra çıkan ayıpta bilirkişi delilini hazırlamamak.
- Tüketici sıfatını sorgulamadan 6502 uygulamak (ticari araç, şirket alımı).
- 4077 dönemi ihbar kuralını 6502 olayına uygulamak.
