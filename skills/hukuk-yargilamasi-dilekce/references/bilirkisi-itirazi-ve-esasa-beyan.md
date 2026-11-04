# Bilirkişi raporuna itiraz ve esasa ilişkin beyan

## Ne zaman kullanılır
- **Bilirkişi raporuna itiraz:** rapor tebliğ edildi; eksik, belirsiz ya da çelişkili. Ek rapor, sözlü açıklama ya da yeni bilirkişi istenir.
- **Esasa ilişkin beyan:** tahkikat sona ermek üzere ya da rapordan sonra; toplanan delillerin değerlendirmesi ve nihai talep. Tahkikat bitince hâkim taraflara tahkikatın tümü hakkında söz verir. 

Rapora itiraz ile esasa beyan çoğu zaman tek dilekçede birleşir: önce süreli itiraz (m.281), sonra esas değerlendirmesi.

**Esas denetimi bu dosyada yapılmaz.** Maluliyet, aktüerya, kusur, araç hasarı ve işçilik hesabı raporlarında usul bulguları, fark tablosu (itiraz cümlesi sütunuyla) ve önerilen talep türü `../../tazminat-haksiz-fiil/references/bilirkisi-raporu-denetimi.md`'den gelir (ORTAK-KURALLAR.md §14). Bu dosya o tabloyu m.281 ayrımına göre (eksik / belirsiz / çelişkili) gruplar ve süreyi yeniden doğrular.

---

## Süre tablosu

| İşlem | Başlangıç | Süre ve dayanak | Not |
|---|---|---|---|
| Rapora itiraz (tamamlatma, açıklama, yeni bilirkişi talebi) | Raporun **tarafa tebliği** | **İki hafta** — HMK m.281/1 |  |
| İtiraz için **ek süre** | Talep aynı iki hafta **içinde** yapılmalı | Sürenin bitiminden itibaren, **bir defaya mahsus, en çok iki hafta** — HMK m.281/1 (7251/24 ile ek cümle, 2020) | Gerekçe: hazırlanması çok zor/imkânsız ya da özel/teknik çalışma gerekiyor. **Eski YAML bu ek süreyi bilmiyordu.**  |
| Mahkemenin re'sen ek rapor / yeni bilirkişi yetkisi | — | HMK m.281/2-3 | Süre kaçsa bile mahkeme re'sen yaptırabilir; ama taraf itiraz hakkını kaybeder.  |
| Adli tatil | — | HMK m.104 | |

`legal_calculate_deadline` bu süre için kod tanımıyor (`hmk_expert_objection` → "Kural bulunamadı"); elle hesapla. 

**Süresinde itiraz edilmezse:** Yargıtay 10. HD çoğunluğu, SGK maluliyet oranına süresinde itiraz etmeyen davacının sonradan artan oranı isteyemeyeceğini (karşı taraf lehine usuli kazanılmış hak) kabul eden BAM kararını onadı. Karşı oy, AYM Genel Kurulunun 2024 kararına dayanarak m.281'in yalnız itiraz imkânını düşürdüğünü, maddi hakkı ortadan kaldırmadığını savunuyor. Konu tartışmalı: süreyi kaçırma, `[incele]`. Karşı oydaki AYM kararı: **İsmail Tuncel, AYM Genel Kurul, B. No: 2019/8609, 21.12.2023 (RG 20.05.2024, 32551)** — SGK raporundaki maluliyet oranına itiraz edilmediği için karşı taraf lehine usuli kazanılmış hak oluştuğu gerekçesiyle yargılamada alınan daha yüksek oranlı ATK raporunun esas alınmamasını **mahkemeye erişim hakkına müdahale** saydı (§ 29-33); hüküm fıkrası okunmadı, dilekçede kullanmadan önce kararın sonuç kısmını tam metinden oku.  

---

## İtirazın içeriği
- Soyut "rapora itiraz ediyoruz" yetmez; **eksik** (görülmeyen delil, cevaplanmayan soru), **belirsiz** (gerekçesiz sonuç) ya da **çelişkili** (rapor içi ya da önceki raporla çelişki) nokta madde madde yazılır; m.281/1'in ayrımına göre talep seçilir: tamamlatma (ek rapor), açıklama, yeni bilirkişi.
- Hesap hatası (tarih, ücret, faiz, gün sayısı) en başta ve somut tutarla.
- Bilirkişinin hukuki nitelendirme / değerlendirme yapması: bilirkişi uzmanlık gerektiren hususlar dışında açıklama yapamaz, hâkimin yapacağı hukuki nitelendirmede bulunamaz (HMK m.279/4). Raporun asgari içeriği m.279/2'dedir (gerekçe, incelenen vakıalar, görüş ayrılığı). 
- Uzman görüşü (bilimsel mütalaa) sunulabilir, ama **yalnız bu nedenle ayrıca süre istenemez** — mütalaa gerekiyorsa m.281/1'deki ek süreyi "özel veya teknik çalışma" gerekçesiyle iste. Uzman duruşmaya özürsüz gelmezse raporu değerlendirilmez. `[incele]` 

## Esasa ilişkin beyanın içeriği (eski YAML kurgusu korunarak)
1. Bilirkişi raporuna beyanlar (lehe tespitleri vurgula, aleyhe olanları gerekçeyle karşıla).
2. İspatlanan vakıaların özeti (dava dilekçesinden bugüne; her biri delil ve tutanak sayfasıyla).
3. Hukuki değerlendirme (yalnız çekilmiş madde ve tam metni okunmuş karar).
4. Net talep (kabul / ret, faiz, giderler). Islah gerekiyorsa `islah.md` — tahkikat bitmeden.

---

## Görüşme soruları (eski `data_schema`)
1. Mahkeme, esas no, beyanda bulunan taraf, karşı taraf — `court_name`, `file_number`, `party_info`, `opposing_party`
2. Rapor tarihi ve **tebliğ tarihi** — `report_date`
3. Rapordaki her hata: sayfa/paragraf, ne yanlış, doğrusu ne, hangi delil gözden kaçmış — `objection_details`, `expert_report_analysis`
4. Talep: ek rapor mu, açıklama mı, yeni bilirkişi/heyet mi?
5. Tanık, keşif ve diğer delillerin sonuçları — `evidence_evaluation`
6. Rapor sonrası ıslah ya da artırım gerekiyor mu (31.07.2026 sonrası davada HMK m.109/4 bir defalık artırım; eski belirsiz alacak davasında m.107/2)?

## soorgla çağrıları
```
legal_get_statute_article  law_no: "6100"  article_no: "281" | "279" | "282" | "293" | "184"
legal_search_cases  sorgu: "<rapor türü> bilirkişi raporu denetime elverişli değil, itirazlar karşılanmadan hüküm kurulması bozma"  mahkeme: "yargitay"  daire: "<ilgili daire>"  tarih_baslangic: <son 3 yıl>
legal_get_case_document  belge_id: <seçilen karar>
```

## Dilekçe iskeleti (eski `ui_config`: başlık → esas no → taraf → konu → süre uyarısı → itirazlar → hukuki dayanak → sonuç)
```markdown
[YER] [__]. [MAHKEME] MAHKEMESİ'NE
                                                    DOSYA NO: [___] E.
İTİRAZ EDEN [DAVACI/DAVALI] : [___]
VEKİLİ                       : Av. [___]
KONU : [tarih] tarihli bilirkişi raporuna (tebliğ: [___]) itirazlarımız ile [ek rapor alınması / yeni bilirkişi heyeti atanması] talebidir.

RAPORA İLİŞKİN İTİRAZLARIMIZ
1. [Hesap hatası] Raporun [s./§] bölümünde … ([doğru değer: ___])
2. [Eksik inceleme] [delil] incelenmemiştir …
3. [Çelişki] …
4. [Hukuki nitelendirme] …

ESASA İLİŞKİN BEYANLARIMIZ (birlikte sunuluyorsa)
…

HUKUKİ DAYANAK : HMK m.281, [___]
SONUÇ VE İSTEM : Raporun hükme esas alınmamasına, [itirazlarımız doğrultusunda ek rapor alınmasına / yeni bir bilirkişi heyetinden rapor alınmasına] karar verilmesini saygıyla arz ve talep ederim. [TARİH] [İmza]
```

## Sık hatalar
- 🔴 İki hafta kaçmış; ek süre süre bittikten sonra istenmiş.
- 🟠 Soyut itiraz; hangi sayfa, hangi delil yok.
- 🟠 Lehe rapora itiraz edilmeyip sonra "rapora karşı taraf da itiraz etmedi" savunmasının kurulmaması.
- 🟡 Esasa beyanda yeni vakıa ileri sürülmüş (genişletme yasağı — m.141).

