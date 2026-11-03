# Cayma hakkı, mesafeli satış, iş yeri dışı ve taksitli satış

## Ne zaman kullanılır
- **Tüketici tarafı:** internetten/telefonla/pazaryerinden alınan ürünü iade etmek, kapıdan ya da "tanıtım gezisinde" imzalanan sözleşmeden kurtulmak, taksitli satıştan vazgeçmek; sipariş gelmedi; satıcı iade kargo ücreti istiyor; iade parası yatmadı.
- **İşletme tarafı:** satıcı/pazaryeri "cayma istisnası var mı", "iade masrafını kim öder", "kaç günde para iade edilir", "kullanılmış ürünü almak zorunda mıyız" soruyor.
- Ayıp nedeniyle iade (cayma değil) → `ayipli-mal-ve-hizmet.md`. Kredi sözleşmesinden cayma → `tuketici-kredisi-ve-bankacilik.md`. Devre tatil ve ön ödemeli konutta cayma → `on-odemeli-konut-ve-devre-tatil.md`. Finansal hizmetlerin mesafeli satışı → Finansal Hizmetlere İlişkin Mesafeli Sözleşmeler Yönetmeliği (`20495`) `[incele]`.

**Önce ayır:** cayma hakkı **gerekçesizdir** ve ayıp gerektirmez; ayıp varsa m.11 seçimlik hakları ayrıca ve daha uzun süre kullanılabilir. Tüketiciye ikisini karıştırmadan anlat.

---

## Süreler ve dayanakları

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Mesafeli sözleşmede cayma: **14 gün** | Mal: tüketicinin (ya da belirlediği üçüncü kişinin) **teslim aldığı gün**; hizmet: sözleşmenin kurulduğu gün | 6502 m.48/4; Mesafeli Söz. Yön. m.9/1-2 | Teslimden önce de kullanılabilir. Parçalı teslimde son parça/son mal; düzenli teslimde ilk mal (m.9/3). Taşıyıcıya teslim, tüketiciye teslim sayılmaz (m.9/4). |
| Cayma hakkı konusunda gereği gibi bilgilendirilmeyen tüketici: 14 günle bağlı değil; **her hâlde cayma süresinin bitiminden 1 yıl sonra** sona erer | — | 6502 m.48/4; Yön. m.10 | Bilgilendirme 1 yıl içinde sonradan yapılırsa 14 gün o günden işler (Yön. m.10/2). |
| Satıcının teslim süresi: taahhüt edilen süre, mal satışında **her hâlde 30 gün** (kişiye özel mallar hariç); aşılırsa tüketici **feshedebilir** | Siparişin satıcıya ulaşması | 6502 m.48/3 (7392/7) | |
| Tüketicinin malı geri göndermesi: **14 gün** | Cayma bildirimini yönelttiği tarih | Yön. m.13/1 | Satıcı malı kendisi geri alacağını teklif etmişse uygulanmaz. Eski metin "10 gün" diyordu. |
| Satıcının bedel iadesi: **14 gün** | Mal teslimden sonra caymada: iade için ön bilgilendirmede belirtilen **taşıyıcıya teslim** tarihi (başka taşıyıcıyla gönderildiyse satıcıya ulaştığı tarih); teslimden önce ya da hizmette: cayma bildiriminin ulaşması | Yön. m.12/1-3 (RG 23.8.2022) | Teslim masrafı dahil **tüm** ödemeler; ödeme aracına uygun, tek seferde, masrafsız (m.12/4). |
| İş yeri dışında kurulan sözleşmede cayma: **14 gün**; bilgilendirme yoksa en çok cayma süresinin bitiminden 1 yıl sonra | Sözleşme/teslim (yönetmelik) | 6502 m.47/5-6 | Cayma süresinde satıcı ödeme ya da borç senedi **isteyemez** (m.47/5). |
| Taksitle satışta cayma: **7 gün** | Sözleşme (yönetmelik) `[doğrula]` | 6502 m.18/1 | Teslim edilen mal ancak olağan gözden geçirme ölçüsünde kullanılabilir (m.18/3). |
| Taksitle satışta muacceliyet uyarısı: en az **30 gün** süre | — | 6502 m.19/1 | Ancak bedelin en az onda biri olan ardışık iki taksit ya da dörtte biri olan bir taksitte temerrüt. |

`legal_calculate_deadline` bu süreleri tanımaz; elle hesapla, `legal_check_holiday` ile kontrol et, `[doğrula]`.

---

## Kontrol listesi — mesafeli sözleşme

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| MS-NİTELİK | Eş zamanlı fiziksel varlık olmadan, uzaktan pazarlama sistemi içinde, uzaktan iletişim aracıyla mı kuruldu? | 6502 m.48/1 | Mağazada görüp telefonla sipariş sınırda `[incele]` |
| MS-ÖN-BİLGİ | Ön bilgilendirme yapılmış mı; siparişin ödeme yükümlülüğü doğurduğu onaydan hemen önce açıkça söylenmiş mi? Aksi hâlde tüketici siparişle bağlı değil | 6502 m.48/2; Yön. m.8/1 | İspat yükü satıcıda |
| MS-İADE-TAŞIYICI | Ön bilgilendirmede iade için taşıyıcı belirtilmiş mi? Belirtilen taşıyıcıyla iadede masraf tüketiciden istenemez; hiç taşıyıcı belirtilmemişse iade masrafı istenemez; taşıyıcının tüketicinin bulunduğu yerde şubesi yoksa satıcı malı ücretsiz aldırmak zorunda | Yön. m.12/5 (RG 24.5.2025, yürürlük 1.1.2026) | 1.1.2026 öncesi işlemlerde eski m.12/5 ve m.13/3 metnine bak `[incele]` |
| MS-İSTİSNA | Cayma istisnası var mı? (Yön. m.15/1) — fiyatı finansal piyasaya bağlı mal; kişiye özel hazırlanan mal; çabuk bozulan mal; ambalajı açılmış hijyen ürünü; karışan mal; ambalajı açılmış kitap/dijital içerik/sarf malzemesi; süreli yayın; belirli tarihli konaklama, taşıma, araç kiralama, yiyecek, eğlence; anında ifa edilen elektronik hizmet ya da gayrimaddi mal; tüketici onayıyla cayma süresinde ifasına başlanan hizmet | Yön. m.15/1 | "Taraflarca aksi kararlaştırılmadıkça" — satıcı daha geniş hak tanıyabilir |
| MS-İSTİSNA-İPTAL | **Dikkat:** trafiğe tescili zorunlu taşıtlar ve kayıtlı insansız hava araçları (ı), canlı müzayede (j), satıcı/servis kurulumu yapılan mallar (k) istisnaları Danıştay 10. Dairesi kararıyla **iptal edildi**; (i) bendi 24.5.2025 değişikliğiyle mülga | Yön. m.15/1-ı, i, j, k | Mevzuat kaydı bu bentleri iptal edilmiş gösteriyor; ancak kararın tam metni, kesinleşip kesinleşmediği ve iptalden önceki işlemlere etkisi bu beceride doğrulanmadı. İnternetten araç ya da kurulumlu beyaz eşya alımında: (1) olay tarihini 6.5.2026 iptal kararıyla karşılaştır; (2) `legal_search_cases` (`mahkeme: "danistay"`, `sorgu: "Mesafeli Sözleşmeler Yönetmeliği 15 inci madde iptal trafiğe tescili zorunlu taşıt kurulum"`) ve `legal_get_case_document` ile kararı ve varsa İDDK aşamasını ara; (3) bulamazsan satıcının bu bentlere dayanmasının artık mümkün olup olmadığını kesin yazma, `[ARAŞTIRMA GEREKLİ: Danıştay 10. D. E.2022/5534 K.2026/2753 kesinleşme ve zamana etki]` yaz |
| MS-KULLANIM | Tüketici malı işleyişine ve kullanım talimatına uygun kullandıysa değişiklik/bozulmadan sorumlu değil | 6502 m.48/4 son cümle; Yön. m.13/2 | Aşırı kullanım → değer kaybı tartışması `[incele]` |
| MS-PAZARYERİ | Aracı hizmet sağlayıcı (pazaryeri): ön bilgilendirmeden, kayıt tutmadan, bedel tahsil ettiyse iade ve teslim yükümlülüğünden satıcıyla **müteselsilen**; kendi kampanyasının karşılanmamasından ve reklam–ön bilgi uyumundan sorumlu; cayma/iade talep sistemi kurmak zorunda | 6502 m.48/5-6 (7392); Yön. m.12/A | Tüketici davalı olarak pazaryerini de seçebilir `[incele]` |
| MS-KAYIT | Pazaryeri işlem kayıtlarını **3 yıl** tutar ve istenirse tüketiciye verir | Yön. m.12/A-5 | Delil talebi için kullan |
| MS-BİLDİRİM | Cayma bildirimi yazılı ya da kalıcı veri saklayıcısıyla (e-posta, SMS, form) satıcıya, sağlayıcıya **veya pazaryerine** yöneltildi mi? Kullanım ispatı tüketicide | Yön. m.11/1, 11/4 | Ekran görüntüsü ve gönderim kaydı sakla |

## Kontrol listesi — iş yeri dışı ve taksitli satış

| Kod | Kontrol | Dayanak |
|---|---|---|
| İYD-NİTELİK | İş yeri dışında yüz yüze; iş yeri dışı görüşmenin hemen ardından; satıcının düzenlediği tanıtım gezisinde mi kuruldu? | 6502 m.47/1 |
| İYD-YETKİ | Satıcı Bakanlıkça yetkilendirilmiş mi? | 6502 m.47/2 |
| İYD-ŞEKİL | Yazılı mı; tarih tüketicinin **el yazısıyla** mı; nüsha verildi mi? Yazılı değilse geçersiz, ama satıcı geçersizliği tüketici aleyhine ileri süremez | 6502 m.47/4 |
| İYD-ÖDEME | Cayma süresinde para ya da senet alındı mı? (yasak) | 6502 m.47/5 |
| TS-ŞEKİL | Taksitle satış yazılı mı? | 6502 m.17/3 |
| TS-SENET | Kıymetli evrak yalnız nama yazılı ve her taksit için ayrı | 6502 m.4/5 → `../../sozlesme-incelemesi-tbk/references/genel-islem-kosullari-ve-tuketici.md` |
| TS-ERKEN | Erken ödemede faiz/komisyon indirimi yapılıyor mu? | 6502 m.20 |
| SİPARİŞSİZ | İstenmeyen mal gönderildi mi? Tüketiciye karşı hak ileri sürülemez; sessizlik kabul değil | 6502 m.7 |

---

## Görüşme soruları

| Alan | Soru |
|---|---|
| Kanal | Nereden aldınız (site, pazaryeri, telefon, kapıda, gezi)? Satıcı ve pazaryeri adı? |
| Tarihler | Sipariş, ödeme, teslim, cayma bildirimi, iade kargoya veriliş tarihleri? |
| Ürün | Ne aldınız? Kişiye özel mi, ambalajı açıldı mı, hijyen ürünü mü, dijital içerik mi, kurulum yapıldı mı? |
| Bilgilendirme | Ön bilgilendirme formu ve mesafeli sözleşme ekranı/e-postası var mı? Cayma hakkı ve iade kargosu yazıyor muydu? |
| Satıcı tutumu | Satıcı ne dedi (istisna, kullanılmış, kargo ücreti)? Yazılı mı? |
| Tutar | Ödenen bedel ve kargo bedeli? Ödeme aracı (kart/taksit)? |

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "6502" article_no: "7" | "17" | "18" | "19" | "20" | "47" | "48"
legal_list_statute_articles law_no: "20237" article_no: "<5 | 8 | 9 | 10 | 11 | 12 | 12/A | 13 | 15>" include_content: true
legal_search_official_gazette query: "Mesafeli Sözleşmeler Yönetmeliğinde Değişiklik" search_in: "title" sort_by: "date_desc"
legal_resolve_statute query: "İş Yeri Dışında Kurulan Sözleşmeler Yönetmeliği"
legal_search_cases mahkeme: "yargitay" sorgu: "mesafeli satış cayma hakkı ön bilgilendirme bedel iadesi" tarih_baslangic: "<son 3 yıl>"
legal_search_cases mahkeme: "danistay" sorgu: "Mesafeli Sözleşmeler Yönetmeliği cayma istisnası iptal"
```

---

## Çıktı iskeleti — cayma değerlendirmesi

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …

## Cayma hakkı: [ürün/hizmet] — [tüketici/satıcı] — [tarih]

### Sonuç
[Cayma hakkı var / istisna kapsamında / süre geçti ama bilgilendirme eksikliği nedeniyle uzadı]

### Süre tablosu
| Olay | Tarih | Son gün | Dayanak |
| Teslim | … | 14. gün … | 6502 m.48/4, Yön. m.9 |
| Cayma bildirimi | … | — | Yön. m.11 |
| Malın geri gönderilmesi | … | 14. gün … | Yön. m.13 |
| Bedel iadesi (satıcı) | … | 14. gün … | Yön. m.12 |

### Cayma bildirimi metni (dışa gidecek, ayrı blok)
[satıcı/pazaryeri adı, sipariş no, ürün, teslim tarihi, "6502 m.48 uyarınca cayma hakkımı kullanıyorum", iade kargo talebi, IBAN/ödeme aracına iade, tarih]

### Dayanaklar · Eksik bilgi · Şimdi ne yapalım?
```

---

## Sık hatalar
- Cayma süresini sipariş tarihinden saymak (malda teslim alındığı gün).
- "Kutusu açıldı, iade alınmaz" savunmasını her ürüne uygulamak (istisna yalnız hijyen, kitap/dijital/sarf gibi bentlerde).
- İptal edilen (ı), (j), (k) bentlerine hâlâ dayanmak.
- Pazaryerini sorumluluk dışında saymak.
- İade masrafını, satıcının belirlediği taşıyıcıyla gönderilen üründe tüketiciden istemek.
- Cayma ile ayıp hakkını karıştırmak.
