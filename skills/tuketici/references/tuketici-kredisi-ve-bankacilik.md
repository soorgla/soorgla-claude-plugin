# Tüketici kredisi, konut finansmanı ve bankacılık işlemleri

## Ne zaman kullanılır
- **Tüketici tarafı:** dosya masrafı/tahsis ücreti iadesi, konut kredisinde erken kapama tazminatı, krediyle birlikte zorla satılan hayat/konut sigortası, kredi kartı yıllık aidatı, kredi sözleşmesinden cayma, değişken faizde artış, muacceliyet ve icra tehdidi, bağlı kredide satıcı teslim etmedi.
- **İşletme tarafı:** banka, finansman şirketi ya da kart çıkaran kuruluş tüketici şikâyetine/THH başvurusuna cevap veriyor; ücret tarifesi ve kredi bağlantılı sigorta akışı denetleniyor.
- Ticari kredi (esnaf, şirket) 6502 kapsamında değildir → `../../sozlesme-incelemesi-tbk/references/odunc-ve-yabanci-para.md`; icra takibine itiraz → `../../icra-iflas/SKILL.md`.

**Sayısal sınırlar beceri metnine yazılmaz.** Erken ödeme tazminatı oranları kanunda (m.37/2), tahsis ücreti sınırı TCMB tebliğinde (TCMB değiştirmeye yetkili), aidat/ücret tarifeleri TCMB düzenlemelerinde; her seferinde çek.

---

## Süreler ve dayanakları

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Tüketici kredisinden cayma: **14 gün**, gerekçesiz ve cezasız | Sözleşme (yönetmelik) `[doğrula]` | 6502 m.24/1 | Süre içinde kredinin tamamı erken ödenirse bildirim aranmaz (m.24/2, 7392/2 ek cümle). |
| Cayan tüketicinin anapara + işlemiş faizi iadesi: **30 gün** | Cayma bildiriminin gönderilmesi | 6502 m.24/3 | Ödemezse cayılmamış sayılır `[doğrula]` |
| Belirsiz süreli kredide faiz artışı bildirimi: yürürlükten **30 gün önce**; tüketici bildirimden itibaren **60 gün** içinde borcu kapatırsa artıştan etkilenmez | Bildirim | 6502 m.26/2 | Artış geriye yürütülemez. |
| Muacceliyet uyarısı: en az **30 gün** süre; ancak ardışık **iki** taksitte temerrüt | Uyarı | 6502 m.28/1 (tüketici kredisi), m.34/1 (konut finansmanı) | Muaccel taksitte faiz/komisyon hesaba katılmaz. |
| Bağlı kredide konut finansmanı kuruluşunun sorumluluğu: kredi tutarıyla sınırlı **1 yıl** | Teslim tarihi ya da teslim edilmediyse sözleşmedeki teslim tarihi | 6502 m.35/2 | Satıcı ile müteselsil. |
| İade davasında zamanaşımı (sebepsiz zenginleşme / sözleşme) | Ödeme | TBK m.146 (m.82 değil) `[incele]` | 3. HD: kredi sözleşmesi varken dosya masrafı iadesi sözleşmeden doğan alacaktır, TBK m.146'daki 10 yıllık süre uygulanır; sebepsiz zenginleşmenin kısa süresi uygulanmaz. Kararda süre, masrafın kesildiği tarihten itibaren değerlendirildi; birden çok kredide her kesinti tarihini ayrı not et `[incele]` |

---

## Kontrol listesi

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| KR-NİTELİK | Tüketici kredisi mi (faiz/menfaat karşılığı erteleme, ödünç)? Kredi kartında 3 aydan uzun erteleme/taksit de tüketici kredisi sayılır | 6502 m.22/1-2 | Ticari kredi → kapsam dışı |
| KR-ŞEKİL | Yazılı ya da mesafeli kuruldu mu? Değilse geçersiz ama kredi veren bunu tüketici aleyhine ileri süremez | 6502 m.22/3, m.32/2 | |
| KR-ÖN-BİLGİ | Sözleşme öncesi bilgi formu makul süre önce verildi mi? | 6502 m.23, m.33 | |
| KR-FAİZ | Belirli süreli kredide faiz sabit ve tüketici aleyhine değiştirilemez; akdi faiz, efektif yıllık faiz ya da toplam maliyet yazılmamışsa kredi **faizsiz** kullanılır | 6502 m.25 | Güçlü bir iade dayanağı; sözleşmeyi oku |
| KR-ERKEN | Erken ödemede tüm faiz ve maliyet unsurlarında indirim; tüketici kredisinde erken ödeme tazminatı öngören bir hüküm yok | 6502 m.27 | Eski YAML "ihtiyaç kredisinde erken ödeme cezası alınamaz" diyordu; dayanağı m.27'nin indirim yükümlülüğü ve m.37'deki tazminatın yalnız konut finansmanına özgü olmasıdır `[incele]` |
| KF-ERKEN | Konut finansmanında: faiz **sabitse** ve sözleşmede yazılıysa erken ödeme tazminatı istenebilir; oran kalan vadeye göre kanunda sınırlı; faiz **değişkense** tazminat istenemez | 6502 m.37/2 | Eski YAML bunu "m.28"e bağlıyordu; doğrusu **m.37** (m.28 temerrüt) |
| KR-SİGORTA | Kredi bağlantılı sigorta tüketicinin yazılı/kalıcı veri saklayıcısıyla **açık talebi** olmadan yapılamaz; sigortasız seçenek de teklif edilmeli; tüketicinin getirdiği poliçe kabul edilmeli; teminat kalan borç ve vadeyle uyumlu olmalı | 6502 m.29, m.38 (7392 ile değişik) | 24.3.2022 öncesi sözleşmede eski metin `[incele]` |
| KR-YAN-ÜRÜN | Kredi, kredi dışı yan ürün satın alma şartına bağlanamaz | 6502 m.29/3, m.38/3 | Kart, mevduat, fon "zorunlu" tutulduysa |
| KR-HESAP | Kredi için açılan ve yalnız kredi işlemi yapılan hesaptan hiçbir ad altında ücret alınamaz | 6502 m.31/1, m.39/1 | |
| KR-KMH | Açık talimat olmadan krediyle bağlantılı kredili mevduat hesabı açılamaz | 6502 m.31/2, m.39/2 | |
| KR-AİDAT | Kart çıkaran kuruluş aidatsız bir kart türü sunmak zorunda | 6502 m.31/3 | Aidat iadesi talebinde önce bu seçeneğin sunulup sunulmadığına bak `[incele]` |
| KR-EK-BEDEL | Yasal yükümlülük ya da kuruluşun kendi menfaatine masraf için ek bedel istenemez | 6502 m.4/3 | |
| KR-TAHSİS | Kredi tahsis ücreti TCMB tebliğindeki sınırı aşıyor mu? Ücret türü tebliğde sayılmış ve tüketiciye bildirilmiş mi? | TCMB Tebliği 2020/7 (`34343`) m.10 | Eski YAML "Yönetmelik Ek-1 (BDDK)" diyordu; güncel dayanak **TCMB tebliği**. Sınırı her seferinde çek; sözleşme tarihindeki düzenlemeyi uygula `[incele]` |
| KR-BAĞLI | Bağlı kredi: satıcı finanse ediyor, kredi veren satıcıdan yararlanıyor ya da mal kredi sözleşmesinde yazılı. Mal sözleşmesinden cayan tüketici kredi verene de bildirirse kredi de tazminatsız sona erer | 6502 m.30 | Konutta m.35 |
| KR-TEMERRÜT-FAİZİ | Temerrüt faizi oranı sözleşmede ve mevzuatta sınırlı mı? | TBK m.120; 3095; kart için 5464 ve TCMB `[incele]` | Eski YAML "akdi faizin %30 fazlasını aşamaz (TBK 88/120)" diyordu; TBK m.120/2 sözleşmesel temerrüt faizini kanuni faiz oranına bağlar, "akdi faizin %30 fazlası" ölçütü bu maddede yok. Kredi kartında tavanı TCMB tebliği belirler (5464 m.26). **Kredi kartı dışındaki tüketici kredisinde** TCMB'nin ayrı bir temerrüt faizi tavanı koyup koymadığı bu beceride doğrulanmadı; çalışma anında `legal_search_statute_semantic` (`sorgu: "tüketici kredisi temerrüt faizi azami oran"`) ve `legal_search_official_gazette` (`query: "Merkez Bankası tüketici kredisi faiz"`, `sort_by: "date_desc"`) ile ara, 6502'nin tüketici kredisi maddelerini `legal_list_statute_articles` (`law_no: "6502"`, `article_query: "kredi"`) ile oku; bulamazsan tavan yazma, `[ARAŞTIRMA GEREKLİ: tüketici kredisinde temerrüt faizi tavanının dayanağı]` yaz |
| KR-SENET-KEFALET | Nama yazılı ve taksit başına ayrı senet; şahsi teminat adi kefalet | 6502 m.4/5-6 | → sozlesme-incelemesi-tbk |
| KR-HAKSIZ-ŞART | Tek taraflı ücret/faiz değiştirme, masraf yükleme şartları | 6502 m.5 | → `../../sozlesme-incelemesi-tbk/references/genel-islem-kosullari-ve-tuketici.md` |

**Tüketici sıfatı ve görev:** bankacılık işlemi tüketici işlemidir (m.3/1-l); tüketicinin bankaya karşı davası tüketici mahkemesinde, değer THH sınırının altındaysa THH zorunlu → `hakem-heyeti-ve-tuketici-davasi.md`. Ticari kredide asliye ticaret.

---

## Görüşme soruları

| Alan | Soru |
|---|---|
| Kredi türü | İhtiyaç, taşıt, konut, kredi kartı, KMH? Kişisel amaçla mı? |
| Tarihler | Sözleşme, kullandırım, erken kapama, ücretin tahsil edildiği tarihler? |
| Belgeler | Sözleşme öncesi bilgi formu, kredi sözleşmesi, ödeme planı, dekontlar, sigorta poliçesi? |
| Faiz | Sabit mi değişken mi? Sözleşmede akdi faiz, efektif yıllık faiz ve toplam maliyet yazıyor mu? |
| Sigorta | Sigorta yazılı talebinizle mi yapıldı? Sigortasız seçenek sunuldu mu? Başka şirketten poliçe getirmeyi teklif ettiniz mi? |
| Tutar | İadesini istediğiniz kalem ve tutar (THH sınırı için toplam değer)? |
| İşletme tarafı | Ücret tarifesi, bilgilendirme kayıtları, sigorta talep formu, ses kaydı var mı? |

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "6502" article_no: "4" | "22" | "23" | "24" | "25" | "26" | "27" | "28" | "29" | "30" | "31" | "32" | "34" | "35" | "36" | "37" | "38" | "39"
legal_list_statute_articles law_no: "34343" include_content: true # TCMB ücret tebliği
legal_search_official_gazette query: "Finansal Tüketicilerden Alınacak Ücretlere İlişkin" search_in: "title" sort_by: "date_desc"
legal_resolve_statute query: "Tüketici Kredisi Sözleşmeleri Yönetmeliği"
legal_resolve_statute query: "Konut Finansmanı Sözleşmeleri Yönetmeliği"
legal_get_statute_article law_no: "5464" article_no: "26" # kart faizi
legal_get_statute_article law_no: "6098" article_no: "120"
legal_search_cases mahkeme: "yargitay" sorgu: "<olay: kredi bağlantılı hayat sigortası açık talep olmadan prim iadesi>" tarih_baslangic: "<son 3 yıl>"
```

---

## Çıktı iskeleti — iade/talep değerlendirmesi

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …

## [Kalem] iadesi: [tüketici] / [banka] — [tarih]

### Sonuç
[Kalem iade edilebilir mi; dayanak; yol (bankaya başvuru → THH / arabuluculuk + tüketici mahkemesi)]

### Kalem tablosu
| Kalem | Tutar | Tahsil tarihi | Dayanak | Değerlendirme |

### Süre tablosu · Dayanaklar · Eksik bilgi · Şimdi ne yapalım?
```

---

## Sık hatalar
- Konut kredisi erken ödeme tazminatı kuralını ihtiyaç kredisine uygulamak.
- Tahsis ücreti sınırını beceriden ya da eski yönetmelikten almak.
- 7392 öncesi ve sonrası sigorta kuralını ayırmamak.
- Faizi sözleşmede yazılmamış krediyi "faizsiz kullanım" (m.25/2) açısından incelememek.
- Ticari krediyi tüketici kredisi sanmak.
