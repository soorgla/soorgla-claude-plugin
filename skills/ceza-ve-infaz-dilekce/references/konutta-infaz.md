# Konutta infaz ve diğer özel infaz usulleri (5275 m.110)

## Önce bunu oku — sınırlar 2025'te değişti

Eski YAML "65 yaş 1 yıl, 70 yaş 2 yıl, 75 yaş 4 yıl, hastalıkta 5 yıl, doğumda 3 yıl" diyordu. **Bunların hepsi eskidi.** 7550 s. Kanun (RG 04.06.2025 mükerrer) m.110'u değiştirdi.  Rakamları her seferinde `legal_get_statute_article(law_no: "5275", article_no: "110")` ile çek.

Güncel metne göre (30.10.2026 itibarıyla çekildi): 

| Fıkra | Kimler | Ceza üst sınırı (toplam) | Not |
|---|---|---|---|
| 110/1 | Herkes (talep üzerine) — **hafta sonu** ya da **gece** infazı | Kasten: 3 yıl; taksirle (taksirle öldürme hariç): 5 yıl | Hafta sonu infazı kurumca hafta içi günlere de kaydırılabilir (7550 ek cümle) |
| 110/2-a | Kadın, çocuk, 65 yaşını bitirmiş | 3 yıl | Zararın giderilmesine ilişkin hukuki sorumluluk saklı |
| 110/2-b | 70 yaşını bitirmiş | 4 yıl | |
| 110/2-c | 75 yaşını bitirmiş | 5 yıl | |
| 110/2-d | 80 yaşını bitirmiş | 6 yıl | 7550 ile eklendi |
| 110/3 | Ağır hastalık/engellilik nedeniyle kurumda hayatını yalnız idame ettiremeyen, toplum güvenliği için ağır ve somut tehlike oluşturmayan | **Sınır yok** (ağırlaştırılmış müebbet hariç; APC'den çevrilen hapis dâhil) | 16/3 usulü rapor (ATK); yıllık inceleme; toplam ceza 10 yılı aşıyorsa elektronik izleme zorunlu |
| 110/4 | Doğurduğu tarihten itibaren **altı ay geçen** kadın | 5 yıl (APC'den çevrilen dâhil) | Talep doğumdan itibaren **bir yıl altı ay** içinde yapılmalı; çocuk ölür ya da verilirse karar kaldırılır |

- **Karar mercii: infaz hâkimi** (110/1-4); kararlara **itiraz** açık (110/8).
- Konutta infaz kararı infaza başladıktan sonra da verilebilir (110/6).
- Özel infaz usulündekilere tabi oldukları rejime göre koşullu salıverilme ve **denetimli serbestlik** hükümleri uygulanır (110/5, 7550 ile değişik). Usule geçerli mazeretsiz uyulmazsa genel hükümlere göre kurumda devam edilir ve 105/A uygulanmaz (110/7).
- **Uygulanmaz (110/9 — 3. ve 4. fıkralar hariç):** terör ve örgüt suçları, cinsel dokunulmazlığa karşı suçlar, APC'den çevrilen hapis, koşullu salıverilmesi geri alınanlar, 105/A/6-7 uyarınca açık kuruma gönderilenler (7550 ile eklendi). Yani **hastalık (110/3) ve doğum (110/4) yolunda bu istisnalar uygulanmaz.**

**"Toplam"** ibaresine dikkat: birden fazla mahkûmiyet varsa toplanmış cezaya bakılır → `cezalarin-toplanmasi.md`.

## Süre
- Sabit süre yok; 110/4'te doğumdan itibaren **1 yıl 6 ay** içinde talep şartı var.
- Ret kararına **itiraz**: 110/8 itiraz yolunu açar. Süre her iki dayanakta da **iki hafta**; başlangıcı farklı: CMK m.268/1 "kararı öğrendiği günden", 4675 m.6/5 (infaz hâkimi kararları) "tebliğden" itibaren; itiraz mercii infaz hâkimliğinin yargı çevresindeki ağır ceza mahkemesi (4675 m.6/6). Hangisinin uygulanacağına dair içtihat okunmadı: **güvenli yol olarak öğrenme tarihinden itibaren iki hafta içinde** itiraz et; tartışma çıkarsa güncel Yargıtay kararlarını `legal_search_cases` ile ara ve en az birinin tam metnini oku. 

## Görüşme soruları
1. Hükümlü: ad, T.C., **doğum tarihi** (yaş hesabı karar tarihine göre), cinsiyet `[___]`
2. Kesinleşmiş ceza(lar): her biri için mahkeme, E./K., süre, suç; toplam ceza? Toplama kararı var mı?
3. Suç terör/örgüt/cinsel suç mu? APC'den çevrilen hapis mi?
4. Hastalık yolunda: tanı, mevcut raporlar, ATK sevki yapıldı mı?
5. Doğum yolunda: doğum tarihi, çocuk yanında mı?
6. Konut adresi ve hanede yaşayanlar?
7. Zarar giderildi mi (110/2)?
8. Daha önce koşullu salıverilme geri alındı mı?

## soorgla adımları
```
legal_get_statute_article  law_no: "5275"  article_no: "110" | "16"
legal_search_official_gazette  query: "Ceza ve Güvenlik Tedbirlerinin İnfazı"  document_type: "kanun"  search_in: "title"  sort_by: "date_desc"
legal_search_statute_semantic  sorgu: "hapis cezasının konutta infazı usul ve esasları elektronik izleme"  mevzuat_tur: "cb_yonetmeligi"
legal_search_cases  sorgu: "5275 sayılı Kanun 110 konutta infaz talebinin reddi yaş sınırı toplam ceza"  tarih_baslangic: "2025-06-04"
legal_get_case_document  belge_id: <seçilen karar>
```

## Dilekçe iskeleti
```
[İL] İNFAZ HÂKİMLİĞİNE
[Gönderilmek üzere: [KURUM] MÜDÜRLÜĞÜNE / [İL] CUMHURİYET BAŞSAVCILIĞI İNFAZ BÜROSUNA]

HÜKÜMLÜ : [Ad Soyad], T.C. [___], Doğum tarihi: [___]
CEZA    : [toplam süre; ilamlar]   ·  SUÇ: [___]
KONU    : 5275 s. Kanun m.110/[2-a | 2-b | 2-c | 2-d | 3 | 4] uyarınca cezanın KONUTTA İNFAZI talebidir.
AÇIKLAMALAR
1. Şartların varlığı: [yaş/hastalık/doğum] — [toplam ceza] — [üst sınır, MCP'den çekilmiş]
2. 110/9 istisnalarının yokluğu (suç türü, APC, geri alma) [3. ve 4. fıkrada gerekmez]
3. [Hastalık] ATK raporu / sevk talebi
4. Zarar durumu
İNFAZIN ÇEKİLECEĞİ KONUT ADRESİ: [___]
HUKUKİ NEDENLER: 5275 m.110 [MCP'den çekilmiş]
SONUÇ VE İSTEM : Cezamın konutta çektirilmesine karar verilmesini saygıyla talep ederim.
```

## Sık hatalar
- 🔴 2025 öncesi sınırlarla (1/2/4 yıl) "şartları taşımıyorsunuz" demek.
- 110/9 istisnalarını hastalık ve doğum yoluna da uygulamak.
- Yaşı başvuru tarihine değil yanlış tarihe göre hesaplamak `[incele]`.
- Birden fazla cezayı ayrı ayrı değerlendirmek; "toplam" ceza esastır.
- Mercii karıştırmak: konutta infaz **infaz hâkimi**, erteleme **başsavcılık**.

