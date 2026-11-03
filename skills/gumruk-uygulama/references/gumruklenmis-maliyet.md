# Gümrüklenmiş maliyet (landed cost)

## Ne zaman kullanılır
- "Bu eşyayı Çin'den getirirsem vergisi ne kadar?", teklif öncesi maliyet, iki menşe ya da iki GTİP arasında karşılaştırma.
- Beyanname öncesi kontrol: idarenin tahakkukuyla karşılaştırılacak kendi hesabın.
- Tahakkuk **farklı çıktıysa ve uyuşmazlık başladıysa** → `../../gumruk-dis-ticaret/references/ek-tahakkuk-ve-yol-secimi.md`.

---

## Girdiler (sor, varsayma)

| Bilgi | Neden |
|---|---|
| 12 haneli GTİP | Oran ve önlem bu koda bağlı (`gtip-tespiti.md`) |
| Menşe ülke (sevk ülkesi değil) | Ülke grubu ve tercihli sütun |
| Menşe ispat belgesi olacak mı (A.TR, EUR.1, menşe beyanı) | Yoksa tercihli oran uygulanmaz, DÜ sütunu |
| Fatura bedeli, para birimi, teslim şekli (Incoterms) | CIF'e tamamlama (navlun, sigorta) |
| Navlun, sigorta, yükleme; royalti/lisans; alıcının sağladığı kalıp vb. | 4458 m.27 ilaveleri |
| Tescil tarihi (planlanan) | Oran sürümü ve kur |
| Ödeme şekli | KKDF |
| Miktar (maktu vergi birimi; adet) | Maktu gümrük vergisi, asgari EMY, ÖTV (I)/(III) |
| ÖTV bilgisi (taşıtta motor tipi/hacmi/gücü; tütünde perakende fiyat) | ÖTV dilimi |

---

## Hesap sırası

| # | Kalem | Matrah | Kaynak | Not |
|---|---|---|---|---|
| 1 | **Gümrük kıymeti** | Fiilen ödenen fiyat + m.27 ilaveleri (Türkiye'deki giriş yerine kadar navlun ve sigorta, komisyon, ambalaj, royalti…) | 4458 m.24, m.27 | TL'ye tescil günü TCMB kuruyla (`legal_get_exchange_rate`). m.27'de sayılanlar dışında ilave yapılamaz (m.27/3) |
| 2 | **Gümrük vergisi** | Kıymet (yüzde) ya da miktar (maktu) | İthalat Rejimi Kararı I–IV sayılı listeler, menşe ülkenin girdiği sütunlardan en düşüğü; yoksa Diğer Ülkeler | Tercihli sütun → menşe ispatı şart |
| 3 | **İlave gümrük vergisi** | Kıymet | İthalat Rejimine Ek Karar (İGV) ekleri | Ülke grubuna göre; AB/STA menşelide çoğu zaman yok |
| 4 | **Ek mali yükümlülük** | Kıymet; liste dipnotunda "yüzde ya da asgari USD/adet, yüksek olanı" | IV sayılı liste, liste dipnotu (ör. binek araçta CBK 10436), ayrı EMY kararları | Asgari tutar için adet ve USD kuru |
| 5 | **Tarım payı** | Bileşime göre | III sayılı liste Tablo 1–2 (bileşim kodu) | Araç uyarır; bileşim kodu kullanıcıdan |
| 6 | **Damping / telafi edici / etkisizleştirme** | Kıymet ya da birim | İlgili tebliğ (firma ve ülke bazlı) | Araç tutar vermez; tebliğden firma oranı |
| 7 | **KKDF** | Kıymet `[doğrula: matrah tanımı]` | BKK 2011/2304 m.4, `legal_calculate_tax` `hesap: "kkdf"` | Yalnız kabul kredili, vadeli akreditif, mal mukabili; peşin ve akreditifte yok; istisna GTİP listesi araçta yok |
| 8 | **ÖTV (II)/(IV)** | Kıymet + 2–7 + diğer giderler (KDV matrahı unsurları, ÖTV hariç) | 4760 m.11/3; listeler ve CBK dilimleri | Taşıtta dilim matrah TL'sine ve motor bilgisine göre |
| 8′ | **ÖTV (I)/(III)** | (I) maktu × miktar; (III-A) nispi × KDV matrahı unsurları, asgari maktudan az olamaz; (III-B) nispi × perakende satış fiyatı + maktu, asgari maktudan az olamaz | 4760 m.11/1, /2, /4, /5 | (III-A) asgari maktu birimi mala göre değişir (bira: litre × alkol derecesi; şarap: litre; diğer: saf alkol litresi) |
| 9 | **KDV** | Kıymet + ithalatta ödenen vergi, resim, harç ve paylar + tescile kadarki diğer giderler (ÖTV dahil) | 3065 m.21 | Genel oran muhasebe tablosundan; indirimli oran listeleri GTİP'e eşlenmedi → mal (I)/(II) sayılı listede ise oran düşer `[incele]` |
| 10 | **Damga vergisi (beyanname)** | Maktu | 488 sayılı Kanun tablosu | `legal_calculate_tax` `hesap: "damga"`; `../../muhasebe/references/damga-ve-harc.md` |

KKDF'nin KDV matrahına girmesi araçta benimsenen yorumdur; 3065 m.21/b "vergi, resim, harç ve paylar" der, "fon" saymaz. Uygulamayı kendi beyannamelerinle karşılaştır `[doğrula]`.

---

## Elle hesap (araç yoksa)

1. Oran sürümü: `legal_search_official_gazette` `query: "İthalat Rejimi Kararı"` `search_in: "title"` `sort_by: "date_desc"`; tescil tarihinden önceki son değişikliği bul. İGV için "İthalat Rejimi Kararına Ek Karar".
2. Satırı bul: ilgili listede GTİP satırı ve menşe ülkenin sütunu; sütun başlıklarının ülke karşılığı listenin başındaki kısaltmalar tablosunda.
3. Önlem: `legal_search_official_gazette` `query: "İthalatta Haksız Rekabetin Önlenmesine İlişkin Tebliğ"` + eşya adı; yürürlükteki son tebliğ.
4. ÖTV: 4760 eki listeler + son CBK (`legal_search_official_gazette` "Özel Tüketim Vergisi (II) Sayılı Listede"…).
5. Her oranın yanına RG künyesini ve "elle hesap — [doğrula]" yaz.

---

## Çıktı iskeleti

```markdown
## Gümrüklenmiş maliyet — [eşya, GTİP] — [menşe] — tescil [tarih]
| Kalem | Matrah (TL) | Oran | Tutar (TL) | Dayanak (liste/sütun, sürüm, RG) |
| Gümrük kıymeti | … | | | kur: [TCMB, tarih] |
| … | | | | |
| **Toplam vergi yükü** | | | | |
| **Gümrüklenmiş maliyet** (kıymet + vergiler + diğer giderler) | | | | |
### Toplama girmeyenler (koşullu / tutarsız)
### Varsayımlar ve uyarılar (menşe belgesi, firma oranı, KKDF ödeme şekli, eşleme doğrulaması)
```

İki menşe ya da iki GTİP karşılaştırmasında aynı tabloyu yan yana sütunlarla ver; fark satırı ekle.

## Sık hatalar
- 🔴 Tercihli oranı menşe belgesi olmadan uygulamak.
- 🔴 Damping önlemini "tutar yok" diye maliyetten tamamen çıkarmak; tutarı bilinmiyorsa ayrı satırda "tebliğe göre — firma oranı gerekir" yaz.
- 🟠 ÖTV dilimini döviz bedele göre seçmek (dilim TL matraha göre).
- 🟠 Navlun ve sigortayı FOB faturaya eklemeyi unutmak.
- 🟡 KKDF'yi peşin ödemede hesaplamak.
