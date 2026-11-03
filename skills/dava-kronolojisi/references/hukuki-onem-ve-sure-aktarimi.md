# Hukuki önem ve süre takibine aktarım

Kronolojide iki ayrı işaret vardır ve karıştırılmaz:

- **Önem** (🔴/🟡/⚪) — bu olay, temsil edilen tarafın davası için ne kadar ağır? Taraf bakışına bağlıdır.
- **Hukuki etki** — bu olay hukuken ne doğurur (süre, zamanaşımı, temerrüt, ispat)? Taraftan bağımsızdır ama **analizdir**; her satır dayanak ve kaynak etiketi taşır.

Bu dosyada süre uzunlukları, parasal sınırlar ve oranlar **yazılmaz**. Her süre, her çalışmada ilgili madde metninden (`legal_get_statute_article`) çekilir (`ORTAK-KURALLAR.md` §5, §13/1).

---

## 1. Önem etiketleri — taraf bakışı

| | Davacı / katılan / başvurucu bakışı | Davalı / sanık / idare bakışı |
|---|---|---|
| 🔴 Kilit | Bir unsuru **kuran** olay (zarar, kusur, illiyet, ihbar, temerrüt); davacı lehine süre başlatan ya da zamanaşımını kesen olay; karşı tarafın ikrarı | Bir unsuru **kıran** olay (illiyet kopması, kusursuzluk, ihbar yokluğu); zamanaşımı ya da hak düşürücü sürenin dolduğunu gösteren olay; ibra, feragat, sulh, müterafik kusur, affetme |
| 🟡 İlgili | Davayı destekleyen ama çürütülebilir olay (tek tanık, sonradan düzenlenmiş tutanak) | Davacının anlatısını zayıflatan olay |
| ⚪ Arka plan | Bağlam | Bağlam |

- "İkisi de" ya da belirsiz ise her kronolojide hangi bakışın uygulanacağını sor. Zaman çizelgesi aynıdır; yalnız önem sütunu değişir.
- Sınırda kalan olay: alttaki seviye + `[incele: sınırda önem]`.
- Alan becerisinin verdiği önem (🔴/🟠) kronolojide gerekçesiz düşürülmez (`ORTAK-KURALLAR.md` §8).

---

## 2. Hukuki etki değerleri

| Değer | Ne zaman | Dayanak örneği (her seferinde yeniden çek) |
|---|---|---|
| `süre başlatır` | Tebliğ, tefhim, öğrenme, son tutanak, fesih bildirimi, ihtarın tebliği | HMK m.345 istinaf [soorgla]; HMK m.281 bilirkişi raporuna itiraz [soorgla]; 4857 m.20 işe iade [soorgla] |
| `hak düşürücü süre` | Süre geçince hakkın kendisi düşer (kendiliğinden gözetilir) | Alan becerisinde (ör. iş hukukunda haklı nedenle fesih süresi, idari dava açma süresi, önalım) `[model bilgisi — doğrulayın; alan becerisinde çek]` |
| `zamanaşımı başlar` | Zararın ve sorumlunun öğrenilmesi, fiilin işlenmesi, alacağın muaccel olması | TBK m.72 haksız fiil (öğrenme + her hâlde fiil tarihi; ceza zamanaşımı daha uzunsa o) [soorgla] |
| `zamanaşımını keser` | Borçlunun ikrarı, faiz/kısmi ödeme, rehin/kefil; dava, def'i, icra takibi, iflas masasına başvuru | TBK m.154 [soorgla]; kesilmeyle yeni süre başlar ve senet/ilamla ikrarda yeni süre farklıdır TBK m.156 [soorgla]; dava süresince her yargılama işlemi ve hâkim kararıyla yeniden başlar TBK m.157 [soorgla] |
| `zamanaşımını durdurur` | Velayet, vesayet, evlilik süresince alacaklar vb.; durma sebebi kalkınca kaldığı yerden işler | TBK m.153 [soorgla] |
| `temerrüt / ihbar` | İhtarname tebliği, ayıp ihbarı, fesih ihbarı | Alan becerisinde (TBK m.117 vb.) `[model bilgisi — doğrulayın]` |
| `ispat` | İkrar, yazılı delil, senede karşı tanık yasağına takılan olay | HMK delil hükümleri; alan becerisinde `[model bilgisi — doğrulayın]` |
| `usul` | Dava şartı (arabuluculuk, idari başvuru), kesinleşme, ön inceleme, kesin süre | Alan ve dilekçe becerilerinde |
| `—` | Hukuki etkisi yok | — |

**Kural:** olgu belgeden gelir, nitelendirme analizdir. "Bu ödeme zamanaşımını keser" cümlesi dekontun değil TBK m.154'ün işidir; dayanak çekilmediyse `[model bilgisi — doğrulayın]`. Kısmi ödemenin gerçekten **borcun ikrarı** sayılıp sayılmadığı `[incele]`.

**Ceza dosyalarında**: dava zamanaşımı, şikâyet süresi, uzlaştırma ve önödeme süreleri `ceza-hukuku-suclar/references/sikayet-uzlastirma-onodeme-zamanasimi.md`'den; `legal_calculate_deadline` ceza alanında yalnız `cmk_appeal`'ı tanıyor.

---

## 3. Süre aktarım bloğu (`sure-takibi`'ne devir)

Kronolojinin sonunda, hukuki etkisi `süre başlatır`, `hak düşürücü süre`, `zamanaşımı başlar` ya da `zamanaşımını keser` olan her olay için bir satır:

```markdown
### Süre aktarım bloğu → sure-takibi
Dosya: [dosya-kisa-adi | belge kipi] Taraf: [davacı/davalı] Hazırlayan: dava-kronolojisi v[N], [YYYY-AA-GG]

| # | Olay (kronoloji satırı) | Başlangıç tarihi | Tarih kesinliği | Süre türü | Dayanak (çekildi mi) | Araç kodu | Ön hesap son gün | Not |
|---|---|---|---|---|---|---|---|---|
| S1 | [K-12] Gerekçeli karar davalı vekiline e-tebligatla ulaştı | [ulaşma + 5. gün sonu = YYYY-AA-GG] | türetilmiş | istinaf | HMK m.345 [soorgla] | hmk_appeal | [araçtan] | adli tatil uzatması araçta uygulandı |
| S2 | [K-03] Haksız fiil, zarar ve sorumlunun öğrenilmesi | [YYYY-AA-GG] | yaklaşık | zamanaşımı | TBK m.72 [soorgla] | — (araçta yok) | [elle, `[doğrula]`] | öğrenme tarihi tartışmalı `[incele]` |
| S3 | [K-07] Kısmi ödeme | [YYYY-AA-GG] | kesin | zamanaşımını keser | TBK m.154/1 [soorgla] | — | yeni süre başlangıcı | ikrar niteliği `[incele]` |
```

- **Başlangıç tarihi**: çelişkili olayda **iki tarihi de** yaz ve hangi tarihle hesaplandığını belirt; temkinli olan (daha erken biten) varsayılan.
- **Araç kodu**: `legal_calculate_deadline` 01.11.2026'da ~70 kod tanıyor (kanun yolu, icra, iş, kira, idari yargı, vergi, KVKK, zamanaşımı); bilinmeyen kodda geçerli kod listesini döndürür (ör. `tbk_zamanasimi` yerine `statute_of_limitations_general`). Tanınmayan sürede kod sütunu `—`, ön hesap elle yapılır ve `[doğrula]` alır.
- **Ön hesap**: `sure-takibi` yüklüyse bu sütunu boş bırak, hesap onundur. Yüklü değilse yalnız ön hesap; HMK m.92 [soorgla] (gün sürelerinde ilk gün sayılmaz; hafta/ay/yıl karşılık gelen gün), HMK m.104 adli tatil [soorgla], `legal_check_holiday` (arifeyi `yarim: true` ile gösterir → "öğleden önce" notu).
- **🔴 kuralı**: ön hesapta süre geçmişse ya da 7 günden az kaldıysa blok başlığına ve kronolojinin en üstüne 🔴.
- `sure-takibi` yüklü değilse blok kopyalanabilir biçimde kalır; kullanıcı takvimine ya da büro programına elle aktarır.

---

## 4. Denenen araç sonuçları (31.10.2026)

| Çağrı | Sonuç |
|---|---|
| `legal_calculate_deadline` (`hmk_appeal`, 2026-07-10) | ✅ ham bitiş 2026-07-24 adli tatile rastladı, araç uzatmayı uyguladı → 2026-09-07; uyarılar alanında açıklama var |
| `legal_calculate_deadline` (`tbk_zamanasimi`) | ⚠️ kod yok; 01.11.2026'dan beri araç geçerli kod listesini döndürüyor (`statute_of_limitations_general` vb.) |
| `legal_check_holiday` 2026-10-29 / 2026-05-27 | ✅ Cumhuriyet Bayramı / Kurban Bayramı |
| `legal_check_holiday` 2026-10-28 / 2026-05-26 (arife) | ✅ `yarim: true`, "13.00'ten sonra tatil" (01.11.2026) |
| `legal_get_statute_article` TBK 49, 72, 154; HMK 92, 104, 281, 345; Tebligat K. 7/a, 11, 21, 32, 35; 4857 m.20; CMK 157; KVKK 28; Av.K. 36 | ✅ hepsi güncel metinle döndü (Tebligat K. m.7/a harfli madde olarak doğrudan geldi) |
| `legal_search_statute_semantic` (TBK zamanaşımının kesilmesi) | ✅ TBK m.157, 156, 153 |
| `legal_search_cases` (e-tebligat beşinci gün) + `legal_get_case_document` | ✅ Yargıtay 5. CD E.2024/4443 K.2024/8038 tam metin; 2. HD sonuçlarındaki pasajlar karşı oydan |
