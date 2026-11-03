# Kurul kararına karşı ivedi dava ve Danıştay temyizi

Kurul kararından sonraki halka: dava açılır mı, ne zamana kadar, YD istenir mi, savunma, karar, temyiz, uygulama.
Dava dilekçesi metni → `../../idare-davalari-imar/references/idari-dava-dilekcesi.md`; temyiz dilekçesi →
`../../kanun-yollari-dilekce/SKILL.md`. Süreler → `sure-zinciri.md`.

Kaynak: 4734 m.57; 2577 m.8, 20/A, 45/8, 61, 62 — 2026-11-01'de `legal_get_statute_article` /
`legal_list_statute_articles` ile çekildi `[soorgla]`.

---

## 1. Hangi işlemler ivedi usule tabi

- İvedi usul "ihaleden yasaklama kararları **hariç** ihale işlemleri"ne uygulanır (2577 m.20/A-1-a) `[soorgla]`.
- Kurum'un şikâyetlerle ilgili nihai kararları mahkemelerde dava konusu edilebilir ve **öncelikle görülür**
  (4734 m.57) `[soorgla]`.
- Şikâyet ve itirazen şikâyet **dava açılmadan önce tüketilmesi zorunlu** idari başvuru yollarıdır (4734 m.54/2)
  `[soorgla]`. İdarenin ihale işlemine itirazen şikâyet tüketilmeden doğrudan dava → ön koşul sorunu `[incele]`.
- **Kapsam dışı:** yasaklama (genel dava süresi, istinaf açık) → `kamu-ihale`; sözleşme uygulaması, YFK → `hakedis`.

## 2. İvedi usulün kuralları (2577 m.20/A-2) `[soorgla]`

| Bent | Kural |
|---|---|
| a | Dava açma süresi **30 gün** |
| b | İYUK m.11 (üst makama başvuru) **uygulanmaz** — süreyi durdurmaz |
| c | 7 gün içinde ilk inceleme; dilekçe ve ekleri tebliğe çıkarılır |
| d | Savunma tebliğden **15 gün**; bir defaya mahsus en çok 15 gün uzatma; savunma ya da sürenin geçmesiyle dosya tekemmül eder |
| e | **Yürütmenin durdurulması kararlarına itiraz edilemez** |
| f | Tekemmülden itibaren en geç **1 ay** içinde karar; ara karar, keşif, bilirkişi, duruşma ivedilikle |
| g | Nihai karara tebliğden **15 gün** içinde **temyiz** |
| h | Temyiz dilekçesi 3 gün içinde incelenir, tebliğe çıkarılır; m.48 kıyasen |
| ı | Temyize cevap **15 gün** |
| i | Danıştay esas hakkında karar verebilir; ilk inceleme kararlarına karşı haklı temyizde bozup geri gönderir; **temyiz üzerine verilen kararlar kesindir** |
| j | Temyiz en geç **2 ay** içinde karara bağlanır; karar en geç 1 ay içinde tebliğe çıkarılır |

- **İstinaf yok:** "İvedi yargılama usulüne tabi olan davalarda istinaf yoluna başvurulamaz" (2577 m.45/8) `[soorgla]`.
- Kesin karar sonrası karar düzeltme yolu mülgadır; olağanüstü yol (yargılamanın yenilenmesi) `[model bilgisi — doğrulayın]`.

## 3. Mahkeme ve taraflar

- **Yer:** Kurul kararları "tebliğ edildiği veya tebliğ edilmiş sayıldığı tarihi izleyen otuz gün içerisinde Ankara
  İdare Mahkemelerinde dava yolu açık olmak üzere" ibaresini taşıyor (ör. KİK 2026/MK-240, 16.07.2026) `[soorgla]`.
  Yetki kuralının kanun dayanağı: özel kanunda yetkili mahkeme gösterilmemişse yetkili mahkeme işlemi yapan idari
  merciin bulunduğu yer idare mahkemesidir (İYUK m.32/1) `[soorgla]`; Kurumun merkezi Ankara'dadır (4734 m.53/a)
  `[soorgla]`.
- **Davalı:** Kamu İhale Kurumu. İhaleyi yapan idare ve ihale üzerinde kalan istekli davaya katılabilir: İYUK'ta
  hüküm bulunmayan "üçüncü şahısların davaya katılması" ve davanın ihbarında HMK uygulanır, ihbar re'sen yapılır
  (İYUK m.31/1) `[soorgla]`; katılanın menfaat ilişkisi `[incele]`.
 Kurul'da dava açma ve kanun yolundan vazgeçme yetkisi Kurul'a aittir (4734 m.53/c) `[soorgla]`.
- **Kim dava açar:** itirazen şikâyeti reddedilen istekli; düzeltici işlem/iptal kararından zarar gören diğer istekli
  (ör. ihale üzerinde kalan) `[incele — menfaat ilişkisi]`; idare `[incele]`.
- **Daire:** görülen güncel Kurul kararı temyizleri Danıştay **13. Daire**'de (2023-2024 kararları, `legal_search_cases`
  danistay) `[soorgla]`; iş bölümünü güncel Danıştay Başkanlar Kurulu kararından teyit et `[doğrula]`.

- Harç: `legal_calculate_court_fee` ya da `legal_get_social_parameters` (`harc_basvurma_asliye`,
  `harc_temyiz_danistay`); tutar metne yazılmaz.

## 4. Süre hesabı

- Başlangıç: Kurul kararının **tebliği** (EKAP bildirimi ise bildirim tarihi — 4734 m.65/b) `[soorgla]`.
- `legal_calculate_deadline` `kural_kodu: "kik_lawsuit"` (canlı; 30 gün). Adli tatile rastlarsa araç 7 gün uzatır ama
  **"GÜVENLİ SON GÜN (uzatmasız)"** satırını da verir; ivedi davalarda m.8/3 uzamasının uygulanıp uygulanmadığı
  doğrulanmadı `[doğrula]` → **güvenli günü esas al** (`sure-zinciri.md` §2).

- Temyiz (15 gün), temyize cevap ve savunma (15 gün) kodları (`kik_lawsuit_cassation`, `kik_lawsuit_cassation_response`,
  `kik_lawsuit_defense`) canlı (adli tatil bayrağı açık); güvenli günü esas al, araç yanıt vermezse elle say,
  `legal_check_holiday`, `[incele]`. Genel `iyuk_cassation` (30 gün) kodunu **kullanma** 🔴.

## 5. Yürütmenin durdurulması (YD) stratejisi

- **İstekli için:** Kurul kararı ret ise ve idare sözleşmeyi imzalayabilecek durumdaysa, iptal kararı tek başına
  sözleşmeyi ortadan kaldırmayabilir; YD talebini dava dilekçesinde aç `[incele]`. YD koşulları (açık hukuka
  aykırılık + telafisi güç zarar) ve teminat: İYUK m.27 `[model bilgisi — doğrulayın]`.
- YD kararına **itiraz yoktur** (20/A-2-e) `[soorgla]`: reddi kesindir, iyi gerekçelendir; ret sonrası yeni olgu
  varsa yeniden istem `[incele]`.
- **İdare için:** dava açılmış olması tek başına Kurul kararının uygulanmasını durdurmaz; YD kararı tebliğ edilene
  kadar Kurul kararını uygula (12766 m.23) `[incele]`.
- Sözleşme imzalanmışsa: iptal kararının sözleşmeye etkisi ve tam yargı (tazminat) yolu `[incele]` → kapsam
  sözleşme sonrasıysa `hakedis`.

## 6. Dava sonrası: uygulama ve MK

- Mahkeme Kurul kararını iptal ederse Kurul **mahkeme kararının uygulanması için yeni karar (MK)** alır: ör.
  "Kurulun … sayılı kararının iptaline, … başvuru sahibinin iddialarının esasının incelenmesine" `[soorgla — KİK
  2026/MK-240, MK-260, MK-222]`. Danıştay bozarsa önceki MK kararı da iptal edilip ilk Kurul kararının "hukuken
  geçerliliğini koruduğuna" karar verilebilir `[soorgla — KİK 2026/MK-70]`.
- MK kararları da EKAP'tan 5 iş günü içinde bildirilir (12766 m.24/1) `[soorgla]`; MK kararı yeni bir Kurul kararıdır,
  ona karşı da 30 gün içinde dava yolu açıktır (karar metnindeki ibare) `[soorgla]`.
- Emsal araştırmasında bu zincir **MK etkisi** kontrolüdür → `kik-emsal-arama.md`.

## 7. Görüşme soruları
| Soru | Neden |
|---|---|
| Kurul kararı ne zaman, nasıl tebliğ edildi (EKAP)? | 30 gün |
| Karar türü (ret / düzeltici işlem / iptal) ve hangi iddialarda? | Menfaat, dava konusu |
| Sözleşme imzalandı mı, imza tarihi yakın mı? | YD gereği |
| Bedel iadesi kararı var mı, 30 günlük talep yapıldı mı? | Paralel süre |
| (Temyiz) idare mahkemesi kararının tebliğ tarihi? | 15 gün |

## 8. Sık hatalar
- 🔴 60 gün dava süresi saymak; istinafa başvurmak; temyize 30 gün saymak.
- 🔴 Adli tatil uzamasına güvenmek (güvenli günü kullan).
- 🟠 YD talebini atlamak ve sözleşme imzasıyla davanın pratik sonucunu kaybetmek.
- 🟡 Mahkeme kararı sonrası MK kararını beklemeden işlem yapmak (idare).
