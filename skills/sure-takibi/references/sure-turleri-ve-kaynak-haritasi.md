# Süre türleri ve kaynak haritası

**Ne zaman kullanılır:** `--ekle` ve `--cikar`'da süreyi sınıflarken; bir sürenin dayanağını hangi alan becerisinin hangi dosyasından alacağını bulurken.

Bu dosya süre **uzunluğu** vermez. Uzunluk her seferinde dayanak maddeden çekilir.

---

## 1. Türler

Tür, sürenin kaçırılmasının sonucunu, tatil ve adli tatil etkisini, durma/kesilme imkânını belirler. Belirsizse **ağır olana** yuvarla ve `[incele]`.

| Tür (`tur`) | Örnek | Kaçırılırsa | Hâkim kendiliğinden gözetir mi | Adli tatil | Durma / kesilme |
|---|---|---|---|---|---|
| `hak-dusurucu` | İşe iade için arabuluculuk ve dava süresi, idari dava açma süresi, önalım dava süresi, mirasın reddi | Hak tamamen düşer | Evet `[model bilgisi — doğrulayın]` | Uygulanmaz; HMK m.104 kapsamı tartışmalı → uzamasız tarih `[incele]` | Kesilmez; zorunlu arabuluculukta işlemez (7036 m.3/17; diğer alanlarda ilgili kanun) |
| `zamanasimi` | Alacak, haksız fiil, işçilik alacakları, ceza dava zamanaşımı | Def'i ile ileri sürülürse dava reddedilir (hukuk); ceza zamanaşımı kendiliğinden | Hukukta hayır (def'i), cezada evet `[model bilgisi — doğrulayın]` | Uygulanmaz | Durur (TBK m.153), kesilir (TBK m.154) → yeni başlangıç alan becerisinden |
| `usul-kesin` | Cevap dilekçesi, delil listesi, ıslah sonrası, bilirkişi raporuna itiraz | O işlemi yapma hakkı kalkar (HMK m.94/3) | Evet | HMK m.104 (m.103 işleri hariç) | Yok; eski hâle getirme ayrı değerlendirme |
| `hakim-suresi` | Ara kararla verilen süre (gider avansı, belge sunma) | Kesin süre ihtarı varsa hak kaybı; yoksa ikinci süre istenebilir (HMK m.94/2) — güvence sayma | Evet | Kararın kendisine ve HMK m.104'e bak | — |
| `kanun-yolu` | İstinaf, temyiz, itiraz (hukuk, ceza, idari) | Karar kesinleşir | Evet | HMK m.104 / CMK m.331 / İYUK m.8/3 | — |
| `idari` | İdareye başvuru (İYUK m.10-11), itiraz, şikâyet, KİK, vergi uzlaşma, SGK itirazı | Yol kapanır, işlem kesinleşir | Evet | Çoğu idari başvuru süresinde uygulanmaz `[incele]`; dava süresinde İYUK m.8/3 | İYUK m.11 başvurusu dava süresini durdurur → bağlı süre |
| `icra` | Ödeme emrine itiraz, şikâyet, itirazın kaldırılması/iptali, istihkak | Takip kesinleşir ya da hak düşer | Çoğu evet | İcra dairesinde yok (bkz. hesap kuralları §5/4) | — |
| `ceza-usul` | Şikâyet süresi, uzlaştırma teklifine cevap, önödeme, KYOK'a itiraz, CMK itirazı | Şikâyet hakkı düşer, yol kapanır | Evet | CMK m.331 | — |
| `sozlesme-bildirim` | Yenilememe bildirimi, fesih ihbarı, opsiyon kullanımı, kira artırım bildirimi, temerrüt ihtarındaki süre | Sözleşme yenilenir ya da fesih geç kalır | Hayır (taraf ileri sürer) | Uygulanmaz | TBK m.93 (aksine anlaşma geçerli); bkz. `sozlesme-yenileme-ve-ihbar.md` |
| `uyum` | KVKK ihlal bildirimi, VERBİS, şirket sicil tescili, teşvik yükümlülüğü, beyanname | İdari para cezası, hak kaybı | — | Uygulanmaz | — |
| `durusma-tarih` | Duruşma, keşif, bilirkişi incelemesi, arabuluculuk toplantısı | — (süre değil, tarih) | — | — | — |

`durusma-tarih` satırları kalan gün bandına girer ama "hesap gerekçesi" yerine kaynağı (tutanak, davetiye) yazılır.

---

## 2. Belgeden süre çıkarma (`--cikar`)

Belgeyi okurken şu olayları ara. Her bulunan olay için `--ekle` önerisi yap; **sürenin hukuki niteliğine** (ör. tebliğ usulsüz mü) karar verme, `[incele]` yaz.

| Belge | Aranacak olay | Olası süre türü | Dikkat |
|---|---|---|---|
| Tebligat mazbatası / e-tebligat kaydı | Tebliğ tarihi, tebliğ şekli (bizzat, m.21, e-tebligat) | Belgenin konusuna göre | Tebliğ şekli başlangıcı değiştirir (`sure-hesap-kurallari.md` §2) |
| Gerekçeli karar / hüküm | Kanun yolu bildirimi ("tebliğden itibaren … içinde"), tefhim tarihi | `kanun-yolu` | Karardaki kanun yolu bildirimi yanlış olabilir; maddeyi çek ve karşılaştır |
| Ara karar / duruşma tutanağı | Verilen süre, kesin süre ihtarı, sonraki duruşma | `hakim-suresi`, `durusma-tarih` | "Kesin süre" ibaresi ve sonucu tutanakta yazılı mı |
| Ödeme emri | Tebliğ tarihi, itiraz ve ödeme süreleri | `icra` | Takip türü (ilamsız, kambiyo, kira) süreyi değiştirir → `icra-iflas` |
| Fesih bildirimi (iş) | Tebliğ tarihi, fesih tarihi | `hak-dusurucu` | → `is-hukuku` |
| İdari işlem / tebliğ yazısı | Tebliğ tarihi, "dava yolu açık" ibaresi | `idari`, `hak-dusurucu` | İbare eksikse etkisi `[incele]` → `idare-davalari-imar` |
| Vergi/ceza ihbarnamesi | Tebliğ tarihi | `idari` | Uzlaşma ve dava süreleri birbirini etkiler → `vergi` |
| İhtarname | Tebliğ tarihi, verilen süre | `sozlesme-bildirim` | Kanuni asgari süre ile ihtardaki süre farklı olabilir |
| Sözleşme | Başlangıç, süre, yenileme, bildirim süresi ve şekli, opsiyon, cezai şart vadesi | `sozlesme-bildirim` | `sozlesme-yenileme-ve-ihbar.md` |
| Arabuluculuk son tutanağı | Tutanak tarihi | Bağlı süre: dava süresi | Arabuluculuk süreyi durdurmuştu; yeniden hesapla |
| Bilirkişi raporu tebliği | Tebliğ tarihi | `usul-kesin` | → `hukuk-yargilamasi-dilekce/references/bilirkisi-itirazi-ve-esasa-beyan.md` |

Belge uzunsa ve süre doğuran olaylar dağınıksa önce `dava-kronolojisi` becerisini öner; onun "Süre aktarım bloğu" bu beceriye toplu devredilir.

---

## 3. Kaynak haritası — süre tablosu hangi beceride?

Sürenin **esası** (hangi olay başlatır, hangi istisna var) alan becerisindedir. Bu beceri oradaki çağrıyı kullanır, maddeyi yeniden çeker, hesabı kendi kurallarıyla yapar.

| Alan | Süre tablosunun yeri |
|---|---|
| İş hukuku (işe iade, arabuluculuk, işçilik alacakları, 6 iş günü) | `../../is-hukuku/SKILL.md` Adım 2; `../../is-hukuku/references/fesih-ve-ise-iade.md`, `iscilik-alacaklari.md`, `fesih-oncesi-kontrol.md` |
| SGK (itiraz, hizmet tespiti, iş kazası, rücu) | `../../sosyal-guvenlik-sgk/references/sgk-uyum-ve-itiraz.md`, `hizmet-tespiti.md`, `is-kazasi-ve-rucu.md` |
| Kira (bildirim, artırım, tahliye, ihtiyaç davası) | `../../kira-hukuku/references/kira-takvimi-ve-ihtarlar.md`, `tahliye-sebepleri.md` |
| Haksız fiil ve tazminat zamanaşımı | `../../tazminat-haksiz-fiil/references/zamanasimi-ve-dava-sartlari.md` |
| İcra ve iflas | `../../icra-iflas/references/odeme-emri-itiraz-ve-sonrasi.md`, `sikayet-tebligat-ve-icra-mahkemesi.md` ve diğer referanslar |
| Aile ve miras (boşanma, tenkis, mirasın reddi, 6284) | `../../aile-miras/references/` altındaki dosyalar |
| İdari dava ve idareye başvuru | `../../idare-davalari-imar/references/iptal-davasi-ve-sureler.md` |
| Kamu personeli | `../../kamu-personeli/references/personel-davasi-usul-ve-sureler.md` |
| Kamu ihale (şikâyet, itirazen şikâyet, ivedi yargılama) | `../../kamu-ihale/SKILL.md`; `../../idari-ve-kurum-basvurulari/references/ihale-sikayet-ve-itirazen-sikayet.md` |
| Hakediş ve sözleşme yürütme | `../../hakedis/references/sure-uzatimi-ve-gecikme-cezasi.md`, `degisiklik-izi-ve-takvim.md`, `uyusmazlik-ve-yargi-yolu.md` |
| Vergi | `../../vergi/references/ihbarname-ve-yol-secimi.md` |
| Gümrük | `../../gumruk-dis-ticaret/SKILL.md` |
| Teşvik | `../../tesvik-yatirim/references/tesvik-belgesi-sureci-ve-yukumlulukler.md`, `iptal-muyyide-ve-geri-alma.md` |
| Sayıştay | `../../kamu-mali-denetim-sayistay/references/sayistay-denetim-sureci-ve-sorgu.md`, `ilam-temyiz-ve-kanun-yollari.md` |
| KVKK (başvuru cevabı, ihlal bildirimi, Kurul süreci) | `../../kvkk/references/veri-ihlali-bildirimi.md`, `kurul-sureci-ve-yaptirimlar.md` |
| Şirketler (genel kurul iptal, uyum takvimi) | `../../sirketler-ticaret/references/sirket-uyum-takvimi.md`, `ortaklik-uyusmazliklari.md` |
| Tüketici (cayma, ayıp, hakem heyeti) | `../../tuketici/references/` altındaki dosyalar |
| Fikri mülkiyet (yayıma itiraz, YİDK, yenileme) | `../../fikri-mulkiyet-bilisim/references/marka-tescil-itiraz-ve-turkpatent.md`, `patent-faydali-model-ve-tasarim.md` |
| Ceza (şikâyet, uzlaştırma, önödeme, zamanaşımı) | `../../ceza-hukuku-suclar/references/sikayet-uzlastirma-onodeme-zamanasimi.md` |
| Yabancılar (sınır dışı, idari gözetim, uluslararası koruma) | `../../yabancilar-vatandaslik/SKILL.md` |
| Deniz ve taşıma (hasar ihbarı, zamanaşımı) | `../../deniz-tasima/references/hasar-ihbari-ve-delil-koruma.md`, `yuk-hasari-ve-tasiyan-sorumlulugu.md` |
| Gayrimenkul (önalım, tapu iptali, KMK) | `../../gayrimenkul-insaat/references/onalim-hakki.md`, `tapu-iptali-ve-tescil.md`, `kat-mulkiyeti-634.md` |
| Kanun yolları (istinaf, temyiz, süre tutum) | `../../kanun-yollari-dilekce/references/hukuk-istinaf.md`, `sure-tutum.md` |
| AYM ve AİHM başvuru | `../../aym-aihm-basvuru/references/aym-bireysel-basvuru.md`, `aihm-basvuru.md` |
| Eski hâle getirme | `../../hukuk-yargilamasi-dilekce/references/eski-hale-getirme.md` |

Alan becerisinin tablosunda bir süre `` notu taşıyorsa bu beceride de `[doğrula]` kalır; maddeyi çekip teyit edersen gözden geçiren notuna yaz ve `ORTAK-KURALLAR.md` §12 doğrulama günlüğüne tek satır öner.

Alan becerisi olmayan bir alanda (ör. sermaye piyasası, enerji, sağlık) süreyi `legal_search_statute_semantic` ile bul, `[incele]` ile işaretle ve "Bu alan için beceri yok; süre ve başlangıç olayı avukat tarafından teyit edilmeli" de.

---

## 4. Karar noktası uyarı kalıpları

Upstream `leave-tracker` uyarı kalıplarının yapısı: kalıp sabit, süre araştırmadan gelir. Raporda 🔴 ve ⛔ satırlar bu kalıplarla açılır.

*Süre geçmiş görünüyor:*
```
[dosya] — [ne] — son gün [tarih] idi ([N] gün önce). Tamamlandı kaydı yok.
Gerekli: (1) İşin yapılıp yapılmadığını teyit edin (UYAP / noter / KEP kaydı). (2) Yapılmadıysa
eski hâle getirme ya da başka yol olup olmadığını avukat değerlendirmeli [incele]. (3) Kayıt
"kacti" olarak işaretlenmeden önce onayınızı alacağım.
```

*Son gün 0–6 gün içinde:*
```
[dosya] — [ne] — son gün [tarih, gün] ([N] gün / [M] iş günü). İç hedef [tarih].
Hesap: [gerekçe]. Dayanak: [madde, etiket].
Gerekli: [dilekçe/başvuru/bildirim] — [ilgili dilekçe becerisi]. Sorumlu: [ad | atanmamış].
```

*Karşı tarafın saati doluyor:*
```
[dosya] — [karşı taraf / idare] için [ne] süresi [tarih]'te doluyor.
Bu tarih geçince bizim için doğan hak/yol: [ör. zımni ret → dava süresi başlar; cevap verilmedi → ...].
Bağlı süreyi şimdi deftere ekleyeyim mi? (başlangıç: [tarih], dayanak: [madde])
```

*Hesaplanmamış süre:*
```
[dosya] — [ne] — son gün hesaplanamadı. Eksik: [tebliğ tarihi | tebliğ şekli | dayanak madde].
Hesaplanmamış süre, olmayan süre değildir. [eksik bilgi sorusu]
```
