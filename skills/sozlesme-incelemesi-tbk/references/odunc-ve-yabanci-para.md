# Ödünç sözleşmeleri ve dövizli bedel kısıtları

İki konu: (1) kullanım ödüncü (ariyet) ve tüketim ödüncü (karz) sözleşmeleri, faiz maddeleri; (2) her sözleşme türünde **döviz cinsinden ya da dövize endeksli bedel** kısıtları (32 sayılı Karar ve 2008-32/34 Tebliğ m.8).

## Ne zaman kullanılır
- Şahıslar ya da şirketler arası borç para sözleşmesi, ortaklara borç, araç/ekipman ödünç verme, "faizli borç senedi".
- Tüketici kredisi sözleşmesi incelemesi (bankacılık uyuşmazlığına dönüşmüşse → tüketici/bankacılık; burada yalnız sözleşme denetimi).
- Bedeli USD/EUR ya da kura endeksli **herhangi** bir sözleşme (kira, hizmet, eser, satış, lisans).

---

## 1. Ödünç

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| TÜR | **Kullanım ödüncü**: şeyin kendisi geri verilir, kural olarak karşılıksız. **Tüketim ödüncü**: para ya da tüketilebilen şey devredilir, aynı nitelik ve miktarda geri verilir | TBK m.379, m.386 | Ücret karşılığı kullanım → kira niteliği `[incele]` |
| FAİZ-KARARLAŞTIRMA | Ticari olmayan tüketim ödüncünde faiz ancak **kararlaştırılmışsa**; ticari tüketim ödüncünde kararlaştırılmasa da istenebilir | TBK m.387 | |
| FAİZ-ORANI | Oran belirlenmemişse ödünç zamanında ve yerinde o tür ödünçlerde geçerli oran; aksi yoksa yıllık ödenir | TBK m.388/1-2 | |
| BİLEŞİK-FAİZ | Faizin anaparaya eklenip yeniden faiz yürütülmesi **kararlaştırılamaz** | TBK m.388/3 | Ticari cari hesap ve TTK istisnaları `[incele]`; tüketicide temerrüt dahil yasak (6502 m.4/7) |
| FAİZ-SINIRI | Akdî faiz kanuni faizin yüzde elli fazlasını, temerrüt faizi yüzde yüz fazlasını aşamaz | TBK m.88/2, m.120/2 | Oran → `legal_get_legal_interest_rates`; 3095 m.1 7589 ile değişti (SKILL.md Adım 4). Ticari işlerde TTK m.8 istisnası `[doğrula]` |
| GERİ-VERME | Gün, bildirim süresi ya da "istendiğinde muaccel" kaydı yoksa ödünç alan ilk istemden itibaren **altı hafta** geçmedikçe geri vermekle yükümlü değil | TBK m.392 | Sözleşmeye vade ya da bildirim süresi yaz |
| TESLİM-ZAMANAŞIMI | Ödünç konusunun teslimi ve teslim alınması istemleri, diğer tarafın temerrüdünden itibaren **altı ayda** zamanaşımına uğrar | TBK m.389 | Geri ödeme alacağı değil, **teslim** istemi |
| ÖDEME-GÜÇSÜZLÜĞÜ | Ödünç alan sözleşmeden sonra ödeme güçsüzlüğüne düşerse ödünç veren teslimden kaçınabilir | TBK m.390 | |
| KULLANIM-SINIRI | Kullanım ödüncünde başkasına kullandırma yasağı, sözleşme dışı kullanımda beklenmedik hâl sorumluluğu; olağan bakım giderleri ödünç alana | TBK m.380-381 | |
| ÖLÜM | Kullanım ödüncü ödünç alanın ölümüyle sona erer | TBK m.385 | |
| TÜKETİCİ-KREDİSİ | Tüketici kredisi **yazılı ya da mesafeli** kurulmadıkça geçersiz; kredi veren geçersizliği tüketici aleyhine ileri süremez | 6502 m.22/3 | Cayma 6502 m.24; erken ödeme indirimi m.27 (konut finansmanında m.37) |
| SENET | Tüketici işleminde yalnız nama yazılı, her taksite ayrı senet | 6502 m.4/5 | |

## 2. Dövizli bedel (32 sayılı Karar)

**Kural:** Türkiye'de yerleşik kişiler kendi aralarında aşağıdaki sözleşmelerde bedeli ve diğer ödeme yükümlülüklerini **döviz cinsinden ya da dövize endeksli** kararlaştıramaz; istisnalar Tebliğ m.8'de sayılıdır. Uluslararası fiyatı döviz cinsinden belirlenen kıymetli maden veya emtiaya endeksleme de **dövize endeksli** sayılır (taşımacılıkta akaryakıt endekslemesi hariç). Yurt dışındaki şube ve %50+ iştirakler bu bakımdan Türkiye'de yerleşik sayılır (sözleşme yurt dışında ifa edilmiyorsa).

| Sözleşme | Türkiye'de yerleşikler arasında | Başlıca istisna | Tebliğ m.8 |
|---|---|---|---|
| Taşınmaz satışı (konut ve çatılı işyeri dahil) | **Yasak** | Alıcı TC vatandaşı olmayan yerleşik ya da m.8/19 kişisi | f.1, f.3 |
| Taşınmaz kirası | **Yasak** | Kiracı yabancı / m.8/19 kişisi; belgeli konaklama tesisi işletme kirası; gümrüksüz satış mağazası | f.2, f.3-5 → `../../kira-hukuku/SKILL.md` |
| İş sözleşmesi | **Yasak** | Yurt dışında ifa, gemi adamı; TC vatandaşı olmayan işçi; m.8/19 işverenleri | f.6, f.14, f.19 |
| Hizmet (danışmanlık, aracılık, taşımacılık dahil) | **Yasak** | TC vatandaşı olmayan taraf; ihracat, transit, döviz kazandırıcı hizmet; yurt dışında yürütülen faaliyet; yurt dışıyla bağlantılı taşıma; belgeli konaklama hizmeti | f.7 (a-d) |
| Eser | Serbest **yalnız** döviz cinsinden maliyet içeriyorsa | — | f.8 |
| Taşınır satışı | **Serbest**, taşıt satışı hariç | — | f.9 (Değişik: RG 6/3/2025-32833) |
| Taşınır kirası | **Serbest**, taşıt kirası hariç | — | f.10 |
| Yazılım / donanım | Yurt dışında üretilen yazılımın satışı ile yurt dışında üretilen donanım ve yazılımın lisans ve hizmet sözleşmeleri **serbest** | — | f.11 → `yazilim-lisans-ve-saas.md` |
| Kamu kurumu tarafı, kamu projesi alt sözleşmeleri | Serbest (taşınmaz satışı/kirası ve iş sözleşmesi hariç) | — | f.15-16 |
| Yabancı sermayeli şirketler (%50+ dışarıda yerleşik), serbest bölge şirketleri | İşveren/hizmet alan olarak taraf oldukları iş ve hizmet sözleşmelerinde serbest | — | f.19 |
| Kıymetli evrak | Yasak kapsamındaki sözleşmeye dayalı senet de dövizli düzenlenemez | — | f.22 |

**Güncellik uyarısı:** Tebliğ sık değişiyor. Bu turda Resmî Gazete'de 2025-32/75 (RG 28.03.2025) ve 2025-32/76 (RG 09.07.2025) sayılı değişiklik tebliğleri ile TCMB I-M sayılı Genelge değişiklikleri (2025/25, 2025/29) görüldü; katalogdaki m.8 metninin bunları içerip içermediği teyit edilemedi. Her incelemede `legal_search_official_gazette` (`query: "32 Sayılı Karara İlişkin Tebliğ"`, `search_in: "title"`, `sort_by: "date_desc"`) ile son değişikliği kontrol et; madde metniyle çelişki varsa ikisini de yaz.

**Yaptırım ve sonuç:** yasak kapsamında dövizli kararlaştırılan bedel TL olarak **yeniden belirlenmek zorundadır**; anlaşma olmazsa Tebliğ m.8/29'daki 2.1.2018 kuru + TÜFE yöntemi (geçiş dönemi sözleşmeleri için) uygulanır. Yeni sözleşmede aykırılığın idari yaptırımı 1567 s. Kanun m.3/1'deki idari para cezasıdır (karar vermeye Cumhuriyet savcısı yetkili; tutarı her seferinde `legal_get_statute_article 1567 m.3` ile çek, ezberden yazma). Aykırı dövizli bedel kaydının özel hukuk akıbeti (kaydın hükümsüzlüğü mü, bedelin TL'ye çevrilerek sözleşmenin ayakta kalması mı) bu beceride doğrulanmadı: çalışma anında `legal_search_cases` (`mahkeme: "yargitay"`, `sorgu: "32 sayılı Karar Tebliğ 8. madde yasağına aykırı döviz cinsinden bedel geçersiz mi Türk lirasına çevrilmesi"`, son 3 yıl) ile ara, en az bir kararın tam metnini oku; net değilse `[ARAŞTIRMA GEREKLİ: aykırı dövizli bedel kaydının geçerliliği]` yaz.

**Kur riski:** dövizli bedel geçerli olsa da olağanüstü kur hareketinde TBK m.138 uyarlaması yabancı para borçlarına uygulanır. TL karşılığı → `legal_get_exchange_rate`.

## 3. Kimin adına?
- **Ödünç alan / tüketici:** faiz kararlaştırılmış mı, sınır aşılıyor mu, bileşik faiz, cayma ve erken ödeme hakları, vade ve bildirim süresi.
- **Ödünç veren:** faizin yazılı ve sınır içinde kararlaştırılması, muacceliyet ve temerrüt faizi, teminat (kefalet şekli → `kefalet-ve-saklama.md`), ödeme güçsüzlüğü hâlinde teslimden kaçınma.
- **Dövizli bedel:** her iki taraf için önce "istisna var mı?" — yoksa TL bedel + TÜFE ya da kur farkı değil, açık TL fiyat ayarlama mekanizması öner.

## 4. Görüşme soruları
1. Borç para mı, eşya mı? Taraflardan biri tacir/şirket mi (ticari ödünç)?
2. Faiz kararlaştırıldı mı; oran ne; yazılı mı?
3. Vade ya da geri isteme bildirimi var mı?
4. Bedel ya da borç döviz mi; taraflar Türkiye'de yerleşik mi; yabancı uyruklu ya da yabancı sermayeli taraf var mı?
5. Teminat (senet, kefalet, rehin) var mı?

## 5. MCP adımları
```
legal_get_statute_article law_no: "6098" article_no: "379" | "380" | "381" | "385" | "386" | "387" | "388" | "389" | "390" | "392"
legal_get_statute_article law_no: "6502" article_no: "4" | "22" | "24"
legal_get_statute_article law_no: "11990" article_no: "8" # 2008-32/34 Tebliğ, dövizli bedel istisnaları
legal_search_official_gazette query: "32 Sayılı Karara İlişkin Tebliğ" search_in: "title" sort_by: "date_desc"
legal_get_legal_interest_rates
legal_get_exchange_rate
legal_calculate_cpi_change
```

## 6. Çıktı iskeleti
```markdown
### Ödünç / dövizli bedel kontrolü
- **Tür:** kullanım ödüncü / tüketim ödüncü (ticari: evet/hayır)
- **Faiz:** [oran] — sınır: [kanuni faiz × 1,5 = …, araç tarihi] → [uygun / aşıyor]
- **Bileşik faiz kaydı:** …
- **Vade / geri isteme:** …
- **Dövizli bedel:** [yok / var] → [istisna: Tebliğ m.8/f.__ | yasak → TL'ye çevirme önerisi]
```

## 7. Sık hatalar
- Ticari olmayan ödünçte kararlaştırılmamış faiz istemek.
- Bileşik faiz kaydını "taraflar serbest" diye kabul etmek (TBK 388/3).
- TBK 389'daki altı aylık süreyi geri ödeme alacağına uygulamak.
- Hizmet ve danışmanlık sözleşmelerinde dövizli bedeli serbest sanmak (Tebliğ m.8/7 yasak; istisnalar dar).
- Altın/emtia endekslemesini dövizden ayrı ve serbest sanmak (m.8/23).
- Tebliğ değişikliklerini kontrol etmeden eski istisna listesini uygulamak.

---
