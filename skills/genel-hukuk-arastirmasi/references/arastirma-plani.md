# Araştırma planı (yol haritası)

> Uyarlama: anthropics/claude-for-legal `legal-clinic/skills/research-start` (Apache 2.0), değiştirilmiştir. Westlaw ve CourtListener sorguları yerine soorgla MCP çağrıları, ABD "state law" çerçevesi yerine Türk norm hiyerarşisi ve yargı kolları kullanılır.

Amaç, araştırmanın "nereden başlamalıyım" aşamasını kısaltmaktır. Bu dosya iki biçimde kullanılır:

- **Yalnızca plan istendiyse** (SKILL.md durum D): aşağıdaki çıktı şablonunu doldur ve dur. Planda soorgla'da **gerçekten denenmiş** sorgular ve dönen sonuç sayıları yer alır, böylece kullanıcı işi kaldığı yerden sürdürür.
- **Araştırma notunun ilk aşamasıysa** (durum A ve B): planı uygula, bulguları `arastirma-notu.md` şablonuna taşı.

---

## 1. Önce eldeki belgeler

Kullanıcı bir belge verdiyse önce onu oku: sözleşme, idari işlem, karar, bilirkişi raporu ya da önceki bir not. İçinde atıf yapılan madde ve kararlar en hızlı ipucudur. Bu atıflar `[kullanıcı verdi]` etiketiyle başlar; soorgla'dan çekilip teyit edilince `[soorgla]` olur.

Dosya çalışma alanı etkinse, aynı dosyanın `arastirma/` klasöründe daha önce yazılmış not var mı diye bak. Yalnızca **o dosyanın** klasörüne bak.

Eşleşen bir şey yoksa bunu açıkça yaz: "Elde ön belge yok, doğrudan birincil kaynaklardan başlanıyor."

## 2. Soruyu daralt

"Sağlık hukuku" bir araştırma sorusu değildir. Şu dört soruyu cevapla:

- Kim kime karşı? Tarafların sıfatı önemlidir: kamu idaresi mi, özel kişi mi, tacir mi, tüketici mi? Bu sıfat **yargı yolunu** belirler (adli, idari, anayasa yargısı).
- Hangi işlem ya da olay? Tarihi ne?
- Hangi sonuç isteniyor? İptal, tazminat, tespit, ceza ya da uyum?
- Hangi yer? İl, yerel yönetim ya da özel bölge (OSB, serbest bölge) önemli mi?

Soru üçten fazla alt soruya bölünüyorsa kullanıcıyla sıraya koy.

## 3. Kaynak sırası ve araç çağrıları

Türk hukukunda norm hiyerarşisi şöyledir: Anayasa → usulüne göre yürürlüğe konmuş milletlerarası antlaşma (Any. m.90; temel hak ve özgürlüklere ilişkin olanlar kanunla çatışırsa antlaşma esas alınır `[model bilgisi — doğrulayın]`) → kanun → Cumhurbaşkanlığı kararnamesi → yönetmelik → tebliğ, genelge ve kurum kararları.

İçtihadın ağırlığı mahkemeye göre değişir:
- Bağlayıcı olanlar: AYM norm denetimi kararları ve içtihadı birleştirme kararları.
- Yol gösterici olanlar: kurul kararları (HGK, CGK, İDDK, VDDK) ve daire kararları.
- Kesin olanlar: BAM'ın kesin karar verdiği işlerde BAM kararları.

Ayrıntı için `karar-ozeti.md` §5'e bak.

| Sıra | Ne aranır | Araç ve parametre | Not |
|---|---|---|---|
| 1 | Hangi mevzuat? | `legal_search_statute_semantic` (`sorgu`: olay cümlesi; gerekirse `mevzuat_tur`) | Sonuçlardaki `ilgili_mevzuatlar` listesi hangi kanun ve yönetmeliğin ağırlıklı olduğunu gösterir. `ustveri_eksik: true` olan sonuç atıf olarak kullanılmaz. |
| 2 | Kaydı çöz | `legal_resolve_statute` (`query`: mevzuat adı; varsa `law_no`, `law_type`) | Numara tek başına tekil değildir. `statute_id` ve başlığı not et. |
| 3 | Madde metni | `legal_get_statute_article` (`law_no`, `article_no`, **`law_type`**) | Dönen `title` beklenen mevzuat mı? Değilse çakışmadır (`soorgla-arama-rehberi.md` §1). Harfli maddede boş dönerse `legal_list_statute_articles`. |
| 4 | Yapı ve komşu maddeler | `legal_get_statute_outline` / `legal_list_statute_articles` | Tanımlar maddesi, istisnalar, geçici maddeler ve yürürlük maddesi atlanmamalıdır. |
| 5 | Güncellik ve olay tarihindeki metin | `legal_get_statute_article_history` (`statute_id`), `legal_list_statute_versions`, `legal_compare_statute_versions`; `legal_get_statute_article` için `effective_date` | Sonuç boşsa bu "değişmemiş" demek değildir. Madde notlarına ("Değişik", "Ek", "Mülga") ve RG başlık aramasına bak. AYM iptali de aranır (sıra 8). |
| 6 | Yüksek mahkeme kurulları | `legal_search_cases` (`mahkeme: "yargitay"`, `daire: "Hukuk Genel Kurulu"` ya da `"Ceza Genel Kurulu"`; Danıştay için `mahkeme: "danistay"`, `daire: "İdare Dava Daireleri Kurulu"` ya da Vergi Dava Daireleri Kurulu) | Kurul kararları dairelerin çeliştiği konuları çoğu zaman özetler. Kurul adı etiketlerini sonuçlardaki `daire` alanından doğrula. |
| 7 | İlgili daire ve güncel çizgi | `legal_search_cases` (`mahkeme`, gerekirse `daire`, `tarih_baslangic`: son 3 yıl) | Hangi dairenin baktığını sonuçlardaki `daire` alanlarından çıkar. Daire iş bölümü değişir; şüphede RG'de Yargıtay ya da Danıştay iş bölümü kararını ara. |
| 8 | Anayasa Mahkemesi | `legal_search_cases` (`mahkeme: "anayasa"`) | Hem norm denetimi (iptal) hem bireysel başvuru (ihlal) kararları çıkar. İptal kararının yürürlük tarihini ve RG künyesini kontrol et. |
| 9 | AİHM | `legal_search_cases` (`mahkeme: "aihm"`; hem Türkçe hem İngilizce sorgu dene) | Türkiye aleyhine kararlar ve ilke kararları. Metin çoğunlukla İngilizcedir; Türkçe çeviri gayriresmîdir. |
| 10 | BAM ve ilk derece | `legal_search_cases` (`mahkeme: "bam"` ya da `"mahkeme"`) | BAM'ın kesin karar verdiği işlerde son söz BAM'dadır. İlk derece kararı emsal değil, örnektir. |
| 11 | İçtihadı birleştirme | `legal_search_official_gazette` (`query: "İçtihadı Birleştirme"`, `search_in: "title"`, gerekirse `date_from`) | `daire` filtresiyle bulunmuyor (rehber §3). |
| 12 | İdari görüş ve kurul kararları | `legal_search_admin_guidance` (`kurum`: tam ad; `belge_tur`; `tarih_baslangic`) | Kapsam kurumdan kuruma değişir (rehber §5). Bu belgeler mahkeme kararı değildir. |
| 13 | Yeni düzenleme ve değişiklik | `legal_search_official_gazette` (`search_in: "title"`, `sort_by: "date_desc"`, `date_from`); tam metin için `legal_get_official_gazette_document` (`url` ya da `id`) | Torba kanunlar başlık aramasında kaçabilir; `search_in: "all"` ile de dene. |
| 14 | Doktrin | soorgla'da yok | Uydurma. Yalnızca gerçekten bildiğin eserleri `[model bilgisi — doğrulayın]` etiketiyle öner; bilmiyorsan `[ARAŞTIRMA GEREKLİ: doktrin]` yaz. |

**Sayısal değer gerekiyorsa** (faiz, harç, parasal sınır, TÜFE, kur, yaşam tablosu) değeri beceri metnine ya da ezbere yazma. İlgili aracı çağır (`legal_get_legal_interest_rates`, `legal_calculate_court_fee`, `legal_get_social_parameters`, `legal_calculate_cpi_change`, `legal_get_exchange_rate`, `legal_get_life_expectancy`) ya da hesabı `hesaplamalar` becerisine bırak.

## 4. Sorgu yazma

- `legal_search_cases` ve `legal_search_statute_semantic` anlam araması yapar. Anahtar kelime listesi değil, **hukuki önerme cümlesi** yaz: "aydınlatılmış onamın ispat yükü hekime aittir" sorgusu, "onam ispat hekim" sorgusundan iyi sonuç verir.
- Aynı soruyu iki zıt önermeyle ara. Ör. "onam yazılı olmalıdır" ve "onam şekle bağlı değildir". Çelişkiyi bulmanın en hızlı yolu budur (`celisen-ictihat-ve-bosluklar.md`).
- Önce dar ara (kurul + son 3 yıl), sonuç azsa genişlet (tarih filtresini kaldır, daireyi kaldır).
- Her denenen sorguyu plana yaz: araç, parametreler, dönen ilk sonuçların künyesi. "Hiç sonuç yok" da bir bulgudur.

## 5. Belirsizliği yaz

Emin olmadığın her yerde şunu yaz: `[BELİRSİZ: [konu] özel kanunla mı düzenlenmiş, yoksa yalnızca genel hükümlere mi tabi? Tarama gösterecek]`. Belirsizliği gizleme.

---

## Çıktı şablonu (yalnızca plan istendiyse)

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1]

> ⚠️ Gözden geçiren notu … (ORTAK-KURALLAR.md §8)

═══════════════════════════════════════════════════════════════
  ARAŞTIRMA YOL HARİTASI: İPUÇLARIDIR, KAYNAK DEĞİLDİR
  [soorgla] etiketli satırlar bu oturumda araçtan döndü, ama
  kararın neyi desteklediği okunarak doğrulanmalıdır. Diğer her
  satır bakılacak yeri gösterir; atıf olarak kullanılamaz.
═══════════════════════════════════════════════════════════════

# Araştırma planı: [soru]

**Yargı yolu (tahmini):** [adli / idari / anayasa] `[incele]` · **Olay tarihi:** [ ] · **Alan becerisi:** [yok / kısmen: …]

## Daraltılmış soru(lar)
1. …

## Eldeki belgeler
[okunanlar ya da "ön belge yok"]

## Mevzuat başlangıç noktaları
| Mevzuat / madde | Neden ilgili | Kaynak | Güncellik |
|---|---|---|---|
| [markdown_citation] | … | [soorgla] | [tarihçe kontrol edildi / boş, RG'de N değişiklik] |

## İçtihat alanları ve denenen sorgular
| Alan | Araç ve parametre | Dönen ilk künyeler | Sonraki adım |
|---|---|---|---|

## İdari görüş / kurul kararları
…

## Resmî Gazete
…

## Doktrin (atıf için değil, çerçeve için)
…

## Belirsizlikler
…

## Ne yapmalı
1. [ ] Tam metni okunacak kararlar: …
2. [ ] `[ARAŞTIRMA GEREKLİ]` boşlukları: …
3. Kural belli olunca: "araştırma notu yaz" deyin, OSKUS notu kurulsun.
```
