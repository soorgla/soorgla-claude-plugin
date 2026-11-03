# Çelişen içtihat ve araştırma boşlukları

> Upstream'de bu iş ayrı bir beceri değildir: `memo` ve `research-start` belirsizliği `[UNCERTAIN]` ve `[RESEARCH NEEDED]` ile işaretler. Türk uygulamasında daireler arası farklılık, iş bölümü değişiklikleri ve BAM daireleri arasındaki ayrışma sık görüldüğü için bu adım ayrıca yazıldı.

## 1. Çelişki türleri

| Tür | Nasıl görünür | Nasıl aranır |
|---|---|---|
| **Daireler arası** | Aynı hukuki soruya iki daire farklı cevap veriyor | Aynı önermeyi iki zıt cümleyle `legal_search_cases`'e ver (ör. "onam yazılı olmalıdır" / "onam şekle bağlı değildir"); sonuçların `daire` alanlarını karşılaştır |
| **Daire ile kurul arası** | Daire bir çizgide, HGK, CGK ya da İDDK başka çizgide (çoğu zaman direnme kararıyla) | Aynı sorguyu `daire: "Hukuk Genel Kurulu"` ile tekrarla; kurul kararında "direnme" ve "Özel Daire" ifadelerine bak |
| **Zaman içinde dönüş** | Aynı daire belirli bir tarihten sonra görüş değiştirmiş | `tarih_baslangic` / `tarih_bitis` ile iki dönem ayrı aranır; dönüşü açıklayan karar ("daha önceki kararlarımızdan dönülerek") okunur |
| **İş bölümü değişikliği** | İş başka daireye geçmiş, yeni daire farklı düşünüyor | Eski daireyi `tarih_bitis` ile sınırla; RG'de Yargıtay ya da Danıştay iş bölümü kararını ara. Kapatılan dairelerin kararları yalnızca tarihsel emsaldir |
| **BAM daireleri arası** | Farklı bölge adliye mahkemeleri farklı karar veriyor; kesin işlerde Yargıtay'a gitmiyor | `mahkeme: "bam"`; sonuçlardaki BAM adlarını karşılaştır |
| **AYM ile Yargıtay/Danıştay arası** | AYM bireysel başvuruda ihlal bulmuş; derece mahkemesi çizgisi farklı | `mahkeme: "anayasa"` ile aynı önerme |
| **AİHM ile iç hukuk arası** | Türkiye aleyhine ihlal kararı var, iç hukuk uygulaması değişmemiş | `mahkeme: "aihm"` (Türkçe ve İngilizce sorgu) |
| **Mevzuat ile içtihat arası** | Yönetmelik ya da kanun bir şekil şartı koyuyor, içtihat şartı farklı yorumluyor; ya da kanun içtihattan sonra değişmiş | Madde metni ve notları (`legal_get_statute_article`) ile kararın tarihini karşılaştır |
| **Alt norm ile üst norm arası** | Yönetmelik kanunun öngörmediği bir sınırlama getiriyor | Kanunun yetki maddesi ve Danıştay'da yönetmelik iptal kararları |

## 2. Gerçek çelişki mi, görünüşte mi?

Çelişki yazmadan önce iki kararın da tam metnini oku ve şunları ayıkla:

- **Olgu farkı:** Kararlar farklı olgulara dayanıyor olabilir (ör. biri acil müdahale, öteki planlı ameliyat). Bu durum çelişki değil, ayırt etmedir.
- **Gerekçe mi, aktarılan görüş mü:** Bir kurul kararında "Burada görüldüğü gibi Özel Dairenin … değerlendirecek olursak" gibi ifadeler karşı oy ya da azınlık görüşü olabilir. Çoğunluk gerekçesi sanılmamalıdır.
- **Usul ile esas farkı:** Biri usulden bozma (ör. bilirkişi heyeti eksik), öteki esasa ilişkin olabilir.
- **Mevzuat değişikliği:** Eski kararın dayandığı metin değişmiş olabilir. Örnek: 1219 m.70'e 2025'te 7557 ile elektronik onam cümleleri eklendi; bu tarihten önceki kararlarda bu cümleler yoktur.

Görünüşte çelişkiyi "çelişki" diye sunma. "Ayırt edilebilir" diye yaz ve farkı göster.

## 3. Çelişki tablosu

```markdown
### Çelişen içtihat: [hukuki soru]

| Çizgi | Kararlar (künye) | Gerekçenin özü (birebir kısa alıntı) | Tarih aralığı | Merci ağırlığı |
|---|---|---|---|---|
| A: [önerme] | [kaynak.markdown] [soorgla], … | "…" | yyyy–yyyy | [daire / kurul / BAM] |
| B: [önerme] | … | "…" | … | … |

**Değerlendirme:** [Hangi çizgi daha güncel, daha üst merciden ve daha istikrarlı? Olgu farkı var mı?] `[incele]`
**Uyuşmazlığın çözüm yolu:** [İBK var mı / istenebilir mi, HGK'ya gitmiş mi] `[incele]`
**Okunan:** [tam metni okunan kararlar] · **Yalnızca özeti görülen:** [ … ] `[çekildi ama desteği doğrulayın]`
```

Notta hangi çizginin "doğru" olduğuna sen karar verme. Çizgileri, ağırlıklarını ve müvekkilin olayına hangisinin daha yakın düştüğünü göster. Seçimi avukat yapar.

**Çözüm yolları** (öneri olarak yaz, karar avukatındır):
- Yargıtay'da içtihadı birleştirme: Birinci Başkan, daireler, genel kurullar ya da Cumhuriyet Başsavcısı ister. Diğer merci ve kişiler gerekçeli yazılı başvuru yapabilir; gidilip gidilmeyeceğine Birinci Başkanlık Kurulu karar verir [soorgla: 2797 s. Yargıtay Kanunu m.45].
- BAM daireleri arasındaki (aynı ya da farklı BAM) kesin kararlarda uyuşmazlığın giderilmesi için Yargıtay'a başvuru yolu [soorgla: 5235 s. Kanun m.35].
- Danıştay'da içtihatların birleştirilmesi: dava daireleri ya da kurullar arasında aykırılıkta İçtihatları Birleştirme Kurulu; Danıştay Başkanı, ilgili daireler, kurullar ya da Başsavcı ister [soorgla: 2575 s. Danıştay Kanunu m.39-40].
- Somut davada: kanun yolu dilekçesinde aykırı kararların gösterilmesi. Bu iş `kanun-yollari-dilekce` becerisine aittir.

## 4. Araştırma boşlukları

Bulunamayan, okunamayan ya da doğrulanamayan her şey satır içinde işaretlenir ve notun sonunda tek listede toplanır.

| Etiket | Ne zaman | Örnek |
|---|---|---|
| `[ARAŞTIRMA GEREKLİ: …]` | Kural, karar ya da görüş bulunamadı | `[ARAŞTIRMA GEREKLİ: özel hastanede onam formunun saklanma süresine ilişkin düzenleme — denenen: legal_search_statute_semantic("hasta onam formu saklama süresi") → ilgisiz; Sağlık Bakanlığı genelgeleri soorgla'da yok]` |
| `[OLGU GEREKLİ: …]` | Sonucu değiştirecek olgu eksik | `[OLGU GEREKLİ: müdahale kamu hastanesinde mi özel hastanede mi? Yargı yolu buna bağlı]` |
| `[BELİRSİZ: …]` | Kaynak var ama uygulanabilirliği şüpheli | `[BELİRSİZ: yönetmelik hükmü kanuna aykırı olabilir]` |
| `[ÇERÇEVE — doğrulanmadı]` | Genel çerçeve model bilgisinden | — |
| `[çekildi ama desteği doğrulayın]` | Karar bulundu, tam metni okunmadı | — |
| `[madde çekilemedi — doğrulayın]` | Madde metni araçtan gelmedi | ORTAK-KURALLAR.md §6 |

Her `[ARAŞTIRMA GEREKLİ]` satırında üç şey bulunur:
1. **Ne aranmalı:** dar bir soru.
2. **Ne denendi:** araç, parametreler ve sonuç. "Denenmedi" de yazılabilir.
3. **Nerede aranabilir:** başka bir soorgla aracı, kurum sitesi, kütüphane veri tabanı ya da UYAP.

Bu listede kurum ya da veri tabanı adı geçebilir. Ama bu kaynaklardan atıf **uydurulmaz**; yalnızca "bakılacak yer" olarak gösterilir.

## 5. "Yerleşik içtihat" ifadesi

"Yerleşik", "istikrar kazanmış" ya da "Yargıtay'ın kökleşmiş görüşü" ifadelerini ancak şu koşullar sağlanınca kullan:
- aynı yönde **en az üç karar** okunmuş olmalı (en az biri tam metin ve son 3 yıldan), ve
- karşı yönde güncel bir karar bulunmamalı.

Bu koşullar sağlanmadıysa şunu yaz: "Taranan [N] kararın tamamı/çoğu [yönde]; yerleşik olduğu söylenemez `[incele]`." Araçların döndürdüğü `toplam_karar` sayısı bu yargı için kullanılmaz.
