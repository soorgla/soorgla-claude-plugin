# Menfi tespit, istirdat, ihtiyati haciz ve tasarrufun iptali

**Ne zaman kullanılır:**
- Borçlu takipten önce ya da sonra "borçlu değilim" demek istiyor (menfi tespit); borçlu olmadığı parayı ödedi (istirdat).
- Alacaklı takip ya da dava öncesi borçlunun mallarını güvenceye almak istiyor (ihtiyati haciz) ya da borçlu ihtiyati hacze itiraz ediyor.
- Borçlu mallarını devrederek aciz hâline düşmüş; alacaklı tasarrufun iptalini düşünüyor.

Dava dilekçesinin metni → `hukuk-yargilamasi-dilekce` (dava dilekçesi, ihtiyati tedbir/haciz, arabuluculuk başvurusu). Esas sorusu (alacak var mı) alanına göre `is-hukuku`, `sozlesme-incelemesi-tbk`, `kira-hukuku` becerilerinde.

---

## Süre tablosu

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Menfi tespit | Takipten önce ya da takip sırasında (süre yok) | İİK m.72/1 | Takip bitip para ödendiyse istirdata döner. |
| İstirdat **1 yıl** | Ödeme tarihi | İİK m.72/7 | Takibe itiraz etmemiş ya da itirazı kaldırılmış olup borçlu olmadığı parayı **tamamen** ödemek zorunda kalan. Hak düşürücü niteliği `[doğrula]`. |
| Arabuluculuğa başvurmuş tarafa karşı takipte menfi tespit: **iki hafta** | Son tutanak tarihi | HUAK m.18/A/16 (7445/36) | Talep ederse İİK m.72/2 (takip öncesi menfi tespit tedbiri) uygulanır. |
| İhtiyati haczi tamamlama: takip talebi ya da dava **7 gün** | Haczin uygulanması (gıyapta: tutanağın tebliği) | İİK m.264/1 | Kaçırılırsa ihtiyati haciz hükümsüz kalır (m.264/4). 🔴 |
| Takipte borçlu itiraz ederse itirazın kaldırılması ya da dava **7 gün** | İtirazın alacaklıya tebliği | İİK m.264/2 | Ret hâlinde dava için 7 gün. |
| Dava sırasında konulan ihtiyati hacizde takip talebi **1 ay** | Esas hükmün mahkemece tebliği | İİK m.264/3 | |
| İhtiyati haciz kararına borçlu itirazı **7 gün** | Huzurda haciz: tatbik; gıyapta: haciz tutanağının tebliği | İİK m.265/1 | Merci kararı veren mahkeme. |
| Üçüncü kişinin ihtiyati hacze itirazı **7 gün** | Öğrenme | İİK m.265/2 | Sebeplere ve teminata. |
| İtiraz kararına **istinaf** | — | İİK m.265 son fıkra | BAM kararı kesin. |
| Tasarrufun iptali davası **5 yıl** (hak düşürücü) | Batıl tasarrufun yapıldığı tarih | İİK m.284 | |

---

## Menfi tespit ve istirdat kontrol listesi

1. **Zaman:** takipten önce mi, sonra mı? Takipten **önce** açılan menfi tespitte alacağın en az %15'i teminatla takibin durdurulması tedbiri istenebilir; takipten **sonra** açılan davada takip durdurulamaz, yalnız en az %15 teminatla **icra veznesindeki paranın alacaklıya verilmemesi** istenebilir.
2. **Tazminat riski:** dava alacaklı lehine biterse tedbir nedeniyle geciken alacak için en az %20 tazminat (teminattan); borçlu lehine biterse ve takip haksız ve kötü niyetliyse alacaklı aleyhine en az %20. 🟠
3. **Dava şartı arabuluculuk:** ticari (TTK m.5/A) ve işçilik (7036 m.3/1) menfi tespit/istirdat davalarında **1.9.2023 ve sonrasında açılan** davalar için zorunlu; kira ilişkisinden kaynaklanıyorsa HUAK m.18/B. Bu, vatandas-basvurulari'ndaki açık DOGRULA notunu kapatır.
4. **Yetki:** takibin yapıldığı icra dairesinin bulunduğu yer ya da davalının yerleşim yeri.
5. **İspat:** menfi tespitte genel kurallar; istirdatta davacı yalnız paranın verilmesi gerekmediğini ispatlar.
6. **Görevli daire (temyiz):** ticari nitelikteki menfi tespit ve istirdat 11. HD; işçi-işveren arası 9. HD; diğerleri alacağın kaynağı olan ilişkiye bakan daire `[incele]`.
7. **Kambiyo senedi:** senedin teminat senedi olduğu ya da bedelsizlik iddiası yazılı delil ister `[incele]`.

## İhtiyati haciz kontrol listesi

1. **Şartlar:** rehinle temin edilmemiş **ve vadesi gelmiş** para alacağı; vadesi gelmemişse yalnız borçlunun belirli yerleşim yeri yoksa ya da mal kaçırma/kaçma/hileli işlem hâlinde (bu hâlde borç yalnız borçlu bakımından muaccel olur).
2. **Yaklaşık ispat ve teminat:** alacağın ve haciz sebebinin yaklaşık ispatı; teminat kuralı ve istisnaları: alacaklı haksız çıkarsa zarardan sorumludur ve HMK teminatını verir; alacak **ilama** dayanıyorsa teminat aranmaz, ilam niteliğinde belgeye dayanıyorsa mahkeme takdir eder (m.259). Kambiyo senedine dayalı taleplerde uygulama `[incele]`. Ret kararına ve yüzüne karşı verilen karara istinaf; BAM kararı kesin (m.258/3).
3. **Harç:** `legal_get_social_parameters` (`tur: "harc_ihtiyati_tedbir_haciz"`).
4. **Tamamlama süreleri** (tabloda) — 7 gün ve 1 ay kaçırılırsa haciz hükümsüz. 🔴
5. **Kendiliğinden kesin hacze dönüşme:** borçlu süresinde itiraz etmez, itiraz kesin kaldırılır ya da iptal edilirse ihtiyati haciz icrai hacze dönüşür.
6. **Konkordato mühleti** içinde ihtiyati haciz kararları uygulanmaz (m.294).
7. Konutta haciz için icra mahkemesi onayı (m.79/a) ihtiyati hacizde aranmaz.
8. Haksız ihtiyati haciz nedeniyle tazminat (m.259) → `tazminat-haksiz-fiil` ile birlikte `[incele]`.

## Tasarrufun iptali kontrol listesi (çerçeve)

1. **Davacı:** elinde geçici ya da kesin **aciz belgesi** bulunan alacaklı ya da iflas idaresi (istihkak davasına karşı açılan karşı davada aciz belgesi aranmaz). Aciz belgesi niteliğindeki haciz tutanağı da 7571 ile m.278'de açıkça anıldı.
2. **İptale tabi tasarruflar:**
   - **Bağışlama ve ivazsız tasarruflar (m.278):** geçici/kesin aciz belgesinin, aciz belgesi niteliğindeki haciz tutanağının düzenlendiği ya da iflasın açıldığı tarihten önceki **bir yıl** içinde. Aksi ispatlanmadıkça bağışlama sayılanlar 7571 ile genişledi: altsoy-üstsoy, **üçüncü derece dahil** kan ve kayın hısımları, son bir yılda evlilik birliği sona ermiş olsa bile eş, evlat edinen-evlatlık, **ortak konutta yaşayanlar** arasındaki işlemler (gerçek değere uygun ivaz ispatlanmadıkça); pek düşük bedelli sözleşmeler; ömür boyu gelir, intifa ve ölünceye kadar bakma sözleşmeleri. 7571 m.2 yayımı tarihinde, **25.12.2025**'te yürürlüğe girdi; 7571 İİK'ya bu değişiklik için geçiş hükmü eklemedi. Tasarruf ya da aciz belgesi 25.12.2025'ten önceyse yeni metnin (özellikle genişleyen yakınlık listesinin) uygulanıp uygulanmayacağı açık bir sorudur: çalışma anında `legal_search_cases` (`daire: "12. Hukuk Dairesi"`, `tarih_baslangic: "2025-12-25"`, sorgu "tasarrufun iptali 278 7571 değişiklik önceki tasarruf") ile ara, bulursan tam metnini oku; bulamazsan iki metni de göster ve `[ARAŞTIRMA GEREKLİ: 7571 m.2 zaman bakımından uygulama]` yaz.
   - **Aciz hâlinde yapılan tasarruflar (m.279)** ve **zarar verme kastıyla yapılan tasarruflar (m.280)** `[incele]`. m.279: hacizden, aciz belgesinden ya da iflastan önceki **1 yıl** içinde mevcut borç için rehin, olağan dışı araçla ödeme, vadesi gelmemiş borç ödemesi, kişisel hakkı güçlendiren tapu şerhi; karşı taraf borçlunun durumunu bilmediğini ispatlarsa dava dinlenmez. m.280: işlemden itibaren **5 yıl** içinde haciz ya da iflas takibi yapılmış olmalı; eş, üstsoy-altsoy, 3. dereceye kadar hısımlar ve evlatlık için bilgi karinesi var; ticari işletme devrinde özel karine.
3. **Hak düşürücü süre:** tasarruftan itibaren 5 yıl (m.284).
4. **Görevli daire:** İİK ve 6183'ten kaynaklanan tasarrufun iptali davaları ile TBK m.19 muvazaa davaları **12. HD**.

---

## Görüşme soruları

1. Takip var mı, hangi aşamada? Para ödendi mi, ne zaman, nasıl (icra dosyasına, doğrudan)?
2. Borçlu olmadığınızı gösteren belge (ödeme dekontu, ibraname, sözleşme feshi)?
3. Uyuşmazlık ticari mi, işçilik mi, kira mı? Arabuluculuğa başvuruldu mu, son tutanak tarihi?
4. Teminat gösterebilir misiniz (nakit, banka teminat mektubu)?
5. (Alacaklı) Borçlu mal kaçırıyor mu? Delili? Alacağın vadesi geldi mi?
6. (Alacaklı) Aciz belgesi var mı? Borçlunun devrettiği mallar, kime, ne zaman, hangi bedelle?

## soorgla çağrıları

```
legal_get_statute_article law_no: "2004" article_no: "72" | "257" | "258" | "259" | "264" | "265" | "277" | "278" | "279" | "280" | "284"
legal_get_official_gazette_document url: "https://www.resmigazete.gov.tr/eskiler/2025/12/20251225-33.htm" # 7571 (m.278 yeni metin)
legal_get_official_gazette_document url: "https://www.resmigazete.gov.tr/eskiler/2023/04/20230405-3.htm" # 7445 (arabuluculuk)
legal_search_cases mahkeme: "yargitay" daire: "11. Hukuk Dairesi" tarih_baslangic: <son 3 yıl>
    sorgu: "<ör. ticari menfi tespit davasında 1.9.2023 sonrası dava şartı arabuluculuk>"
legal_search_cases mahkeme: "yargitay" daire: "12. Hukuk Dairesi"
    sorgu: "<ör. tasarrufun iptalinde üçüncü derece hısımlar arasındaki satışın bağışlama sayılması>"
legal_search_cases mahkeme: "bam" sorgu: "<ihtiyati haciz itirazı — BAM kararı kesin>"
legal_get_social_parameters tur: "harc_ihtiyati_tedbir_haciz"
```

## Çıktı iskeleti

```markdown
## [Menfi tespit / istirdat / ihtiyati haciz / tasarrufun iptali] değerlendirmesi — [taraf, tarih]
### Sonuç
### Süreler
| İşlem | Başlangıç | Son gün | Dayanak | Durum |
### Şartlar (madde madde ✅/🔴/[incele])
### Teminat ve tazminat riski
### Arabuluculuk ve görevli mahkeme
### Emsal kararlar
### Eksik bilgi
```

## Sık hatalar

- Takipten sonra açılan menfi tespitte "takibin durdurulması" tedbiri istemek (kanun yalnız paranın alacaklıya ödenmemesine izin verir).
- 1.9.2023 sonrası ticari menfi tespit/istirdatı arabuluculuğa gitmeden açmak.
- İhtiyati hacizden sonra 7 günlük takip/dava süresini kaçırmak.
- Tasarrufun iptalinde 7571 öncesi dar hısımlık listesini kullanmak (ya da tersine, eski tarihli tasarrufa yeni listeyi geçiş kontrolü yapmadan uygulamak).
- İstirdat davasında kısmi ödemeyi "tamamen ödeme" saymak `[incele]`.
