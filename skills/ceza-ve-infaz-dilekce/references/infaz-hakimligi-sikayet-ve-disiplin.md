# İnfaz hâkimliğine şikâyet ve disiplin cezasına itiraz

## Ne zaman kullanılır
- Ceza infaz kurumu disiplin kurulunun ya da kurum en üst amirinin verdiği disiplin cezası (kınama, etkinliklerden alıkoyma, ziyaretçi yasağı, haberleşme kısıtlaması, hücreye koyma vb.).
- Kurumun hükümlü/tutukluya ilişkin diğer işlem ve faaliyetleri (mektup, ziyaret, sağlık, eşya, iletişim kısıtlaması).
- Cumhuriyet savcısının infaza ilişkin kararları (müddetname, erteleme reddi vb.).

Hepsi **4675 m.5 şikâyeti** ile infaz hâkimliğine götürülür.

## Süre ve dayanak

| Adım | Süre | Başlangıç | Dayanak |
|---|---|---|---|
| İnfaz hâkimliğine şikâyet | **15 gün**, her hâlde **30 gün** | Karar/işlemin öğrenilmesi; her hâlde yapıldığı tarih | 4675 m.5/1  |
| İnfaz hâkiminin kararı | Dosya üzerinden **bir hafta** içinde | Şikâyet | 4675 m.6/2  |
| İnfaz hâkimi kararına itiraz | **İki hafta** | Tebliğ | 4675 m.6/5 (7242/6 ile değişik); merci: infaz hâkimliğinin yargı çevresindeki **ağır ceza mahkemesi** (m.6/6)  |

**Eski bilgi düzeltildi:** eski YAML "tebliğden itibaren 15 gün" diyordu; kanun **öğrenmeden** 15 gün ve **yapılmadan** itibaren 30 günlük üst sınır öngörür. Ayrıca itiraz süresi (iki hafta) ve itiraz mercii (ağır ceza mahkemesi) YAML'da yoktu.

`legal_calculate_deadline` bu süreleri tanımaz (`infaz_sikayet` kodu "Kural bulunamadı"); elle hesapla, `legal_check_holiday` ile kontrol et, `[doğrula]`. 

## Kim başvurabilir, nereye verilir
- Hükümlü/tutuklu ya da (kendisiyle ilgili olmak kaydıyla) eşi, anası, babası, ayırt etme gücüne sahip çocuğu, kardeşi, müdafii, kanuni temsilcisi, izleme kurulu (4675 m.5/3). 
- Dilekçe doğrudan infaz hâkimliğine, ya da Cumhuriyet başsavcılığı veya **kurum müdürlüğü aracılığıyla** verilebilir; aracı merci en geç üç gün içinde gönderir. Sözlü şikâyet tutanağa bağlanır (m.5/2). 
- Şikâyet işlemin yerine getirilmesini **durdurmaz**; ancak giderilmesi güç zarar + açık hukuka aykırılık birlikte varsa infaz hâkimi erteleme/durdurma kararı verebilir (m.5/4). Hücre cezası gibi acil durumlarda bu talebi ayrıca yaz. 
- Süre geçmişse, yetki dışıysa ya da başvuru hakkı yoksa dilekçe esasa girilmeden reddedilir (m.6/1). 

## Disiplin cezasına özgü kontrol listesi (5275)
- **Savunma alınmadan disiplin cezası verilemez**; soruşturulan kişiye eylemin niteliği ve sonuçları bildirilip **üç gün** içinde savunma vermesi, aksi hâlde hakkından vazgeçmiş sayılacağı yazılı bildirilir (5275 m.47/4). Savunma istem yazısının tarihini ve tebliğini sor. 🔴  (Eski YAML bu kuralı "m.47 savunma hakkı" diye doğru maddeye bağlıyordu.)
- Soruşturma eylemin öğrenilmesinden itibaren en geç **beş gün** içinde başlamalı ve en geç **on beş gün** içinde tamamlanmalı (infaz hâkiminin onayıyla yedi gün uzatma) (m.47/2-3). Süre aşımı varsa usul itirazı olarak yaz `[incele]`. 
- Disiplin kurulu en geç üç gün içinde karar verir; karar **gerekçeli** olmalı ve **şikâyet mercii ile süresi** kararda gösterilmeli (m.47/5). Gösterilmemişse bunu yaz. 
- Uyarma, kınama ve etkinliklerden alıkoyma cezalarını **kurum en üst amiri** verir; diğerlerini disiplin kurulu (m.47/1). 
- Hücreye koyma ve odaya kapatma cezasının infazı **infaz hâkiminin onayıyla** başlar (m.48/3-a). 
- **Koşullu salıverilmeye etkisi:** disiplin cezalarının tamamı infaz edilip kaldırılmadıkça koşullu salıverilme işlemi yapılmaz (hak ederek salıverme tarihini geçemez) (m.48/3-b). Kaldırma süreleri: kınama 15 gün, etkinlikten alıkoyma 1 ay, ziyaretçi yasağı 3 ay, hücre 6 ay / 1 yıl vb. (m.48/4). Bu yüzden disiplin itirazı çoğu zaman tahliye tarihini doğrudan etkiler — çıktıda belirt. 
- Disiplin cezalarının sırası 5275 m.38'de; her cezayı gerektiren eylem listesi yetişkinlerde m.39-44, çocuklarda m.46'dadır (m.45 çocuklara disiplin tedbirleri); somut eylemi ilgili bende karşılaştır. 
- Şikâyet üzerine infaz hâkimi hükümlünün **savunmasını alır** ve delilleri toplar; avukatla birlikte savunma yapılabilir (4675 m.6/2 ek cümleler). Dilekçede duruşma/savunma ve delil (kamera kaydı, tanık hükümlü) talebini yaz. 

## Görüşme soruları
1. Hükümlü/tutuklu bilgisi, kurum `[___]`
2. Karar: hangi kurul/amir, tarih, sayı; verilen ceza türü ve süresi?
3. Karar ne zaman öğrenildi/tebliğ edildi? Kararda şikâyet mercii ve süresi yazıyor mu?
4. Savunma istendi mi, ne zaman, kaç gün verildi, savunma verildi mi?
5. Eylem nedir (kurumun iddiası) ve hükümlünün anlatımı? Tanık, kamera?
6. Koşullu salıverilme / denetimli serbestlik tarihi yakın mı (müddetname)?
7. Hücre cezası ise infazına başlandı mı (acil durdurma talebi)?

## soorgla adımları
```
legal_get_statute_article  law_no: "4675"  article_no: "5" | "6"
legal_get_statute_article  law_no: "5275"  article_no: "42" | "43" | "44" | "45" | "46" | "47" | "48"
legal_search_statute_semantic  sorgu: "ceza infaz kurumu disiplin soruşturması usulü savunma"  mevzuat_tur: "cb_yonetmeligi"
legal_search_cases  sorgu: "disiplin cezasına karşı şikâyet savunma alınmadan verilen hücre cezası iptali infaz hâkimliği"
legal_search_cases  mahkeme: "anayasa"  sorgu: "hükümlüye verilen disiplin cezası ifade özgürlüğü haberleşme hakkı"  tarih_baslangic: <son 3 yıl>
legal_get_case_document  belge_id: <seçilen karar>
```
Not: infaz hâkimliği ve ağır ceza itiraz kararları çoğunlukla yayımlanmaz; AYM bireysel başvuru kararları (haberleşme, ziyaret, ifade özgürlüğü) daha iyi kaynaktır. Yönetmelik madde numaralarını uydurma; arama sonucundan al. Ceza İnfaz Kurumlarının Yönetimi ile Ceza ve Güvenlik Tedbirlerinin İnfazı Hakkında Yönetmelik'te (RG 29.03.2020, 31083; `statute_id: 40450`) disiplinle ilgili başlıca maddeler: m.24 ve m.30 disiplin kurulu (oluşum; uyarma, kınama, bazı etkinliklerden alıkoyma dışındaki cezaları verir, cezaları kaldırır), m.110 disiplin cezası ve iyi hâl (idare ve gözlem kurulu kararına 4675'e göre şikâyet), m.118 disiplin cezaları ve tedbirleri (5275 m.38-44; çocuklarda m.45-46), m.119 disiplin soruşturması (süreler, **savunma alınmadan ceza verilemez**), m.120 cezaların infazı (hücreye koymada infaz hâkimi onayı), m.121 tekrar ve cezaların kaldırılması, m.124 kayıt. Süre ve tutarları dilekçeye yazmadan önce maddenin güncel metnini `legal_list_statute_articles` (`statute_id: 40450`, `article_no`, `include_content: true`) ile çek. 

## Dilekçe iskeleti
```
[İL] İNFAZ HÂKİMLİĞİNE
Gönderilmek üzere
[KURUM] MÜDÜRLÜĞÜNE (4675 m.5/2)

ŞİKÂYET EDEN        : [Ad Soyad], [hükümlü/tutuklu], [kurum, koğuş]
VEKİLİ              : [___]
ŞİKÂYET EDİLEN KARAR: [Kurum] Disiplin Kurulunun [tarih] tarihli ve [sayı] sayılı kararı — [ceza]
ÖĞRENME TARİHİ      : [___]
KONU                : 4675 s. Kanun m.5 uyarınca disiplin kurulu kararının İPTALİ ve infazının
                      durdurulması talebidir.
AÇIKLAMALAR
1. Usule ilişkin itirazlar
   a) Savunma alınmamıştır / 3 günlük süre verilmemiştir (5275 m.47/4)
   b) Soruşturma süreleri aşılmıştır (m.47/2-3)
   c) Karar gerekçesizdir, şikâyet mercii ve süresi gösterilmemiştir (m.47/5)
2. Esasa ilişkin itirazlar
   a) Eylem gerçekleşmemiştir / disiplin suçunun unsurları oluşmamıştır (5275 m.[___])
   b) Ceza ölçüsüzdür
3. Kararın koşullu salıverilme tarihine etkisi (m.48/3-b) — giderilmesi güç zarar (4675 m.5/4)
DELİLLER: Kurum kamera kayıtları ([tarih/saat]), tanık [___], savunma yazısı, tutanaklar
HUKUKİ NEDENLER: 4675 m.5, 6; 5275 m.47, 48 [MCP'den çekilenler]
SONUÇ VE İSTEM : Kararın İPTALİNE; karar kesinleşinceye kadar infazının DURDURULMASINA; savunmamın
                 alınmasına ve delillerin toplanmasına karar verilmesini saygıyla talep ederim.
```

## Sık hatalar
- 🔴 Süreyi "tebliğden" saymak; öğrenmeden 15 gün, her hâlde işlemden 30 gün.
- Şikâyeti Bakanlığa ya da idare mahkemesine göndermek; mercii infaz hâkimliğidir.
- Ret kararından sonra iki haftalık itiraz süresini ve ağır ceza merciini atlamak.
- Disiplin cezasının koşullu salıverilmeye etkisini müvekkile anlatmamak.
- Acil durdurma (m.5/4) talebini yazmamak.

