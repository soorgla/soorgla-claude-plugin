# İthalat öncesi kontrol

## Ne zaman kullanılır
- "Bu ürünü ithal edebilir miyim, ne lazım?", yeni tedarikçi ya da yeni ürün, sipariş vermeden önce.
- Eşya gümrükte bekliyor ve "neden çekilmedi" sorusu (eksik izin/denetim) — uyuşmazlığa dönmediyse burada.

Sıra: GTİP kesinleşmeden kontrol yapılmaz (`gtip-tespiti.md`).

---

## Kontrol listesi

| # | Kontrol | Nereden | Bulunca |
|---|---|---|---|
| 1 | **İthalat Rejimi listesi ve sütun:** GTİP hangi listede (I–IV), menşe ülkenin sütunu, dipnot | Maliyet aracı (`dayanak` sütunu) ya da İthalat Rejimi Kararı ekleri | Dipnottaki ülke istisnası ve EMY'yi oku |
| 2 | **Askıya alma (V sayılı liste):** eşya tanımı kayıt satırına uyuyor mu; gözden geçirme tarihi | Maliyet aracı `gumruk_vergisi_askiya_alma` satırı (kayıt no, tanım) | Uyarsa indirimli oran; tanım uygunluğu beyan sahibinin ispatı 🟠 |
| 3 | **Nihai kullanım (VII sayılı liste):** eşya belirli bir üretimde mi kullanılacak | Aracın `gumruk_vergisi_nihai_kullanim` satırı; nihai kullanım izni | İzin ve denetim formları form bankasında ("Nihai Kullanım İzin Başvuru Formu") |
| 4 | **İlave gümrük vergisi** | Maliyet aracı | Menşe ülke grubunu doğrula |
| 5 | **Ticaret politikası önlemleri:** damping, telafi edici, etkisizleştirme (ülke ve firma bazlı) | Maliyet aracı (`anti_damping_vergisi`, `etkisizlestirme_onlemi`) — tebliğ künyesi ve süre sonu | Firma oranı tebliğde; tedarikçi firmanın adı ve üretici olup olmadığı sor |
| 6 | **Ek mali yükümlülük kararı** (liste dışı; ör. A.TR ile gelen belirli binek araçlar) | Maliyet aracı `ek_mali_yukumluluk_karari*` | Koşullu satırda belge rotasını sor |
| 7 | **Gözetim:** gözetim tebliği kapsamında mı (birim kıymet eşiği, gözetim belgesi) | `legal_search_official_gazette` "İthalatta Gözetim Uygulanmasına İlişkin Tebliğ" + eşya; başvuru formu form bankasında | Gözetime tabi eşya gözetim belgesiyle ithal edilir; bazı tebliğlerde A.TR eşliğindeki AB menşeli eşyada aranmaz (ör. Tebliğ 2018/11 m.2)  |
| 8 | **Tarife kontenjanı** (ülke bazlı, dönemli) | `legal_search_official_gazette` "Tarife Kontenjanı" + ülke | Dağıtım yöntemi ve başvuru süresi tebliğde |
| 9 | **Ürün güvenliği ve teknik düzenleme denetimi (TAREKS)** | İlgili Bakanlığın ithalat denetimi tebliği (Ticaret, Sanayi, Sağlık, Çevre…) → `legal_search_official_gazette` "Ürün Güvenliği ve Denetimi Tebliği" + yıl | Denetim başvurusu tescilden önce; CE ve uygunluk belgeleri |
| 10 | **İzin ve kayıt:** Tarım ve Orman (bitki/hayvan sağlığı, gıda), Sağlık (ilaç, kozmetik, tıbbi cihaz), enerji, silah/kimyasal | İlgili bakanlık tebliği; "ithalatı izne tabi eşya listesi" form bankasında | Yetkili gümrük idaresi sınırlaması olabilir (Tarım ve Orman kontrolüne tabi ürünlerin girişine yetkili gümrük idareleri listesi) |
| 11 | **Yasak ve kısıtlama** (ülke yaptırımı, yasak eşya) | RG ve Bakanlık duyurusu `[web — doğrulayın]` | 🔴 sipariş öncesi bildirim |
| 12 | **Menşe belgesi** tercihli oran için hazır olacak mı | `mense-belgeleri.md` | Belge yoksa maliyeti DÜ sütunuyla da ver |
| 13 | **ÖTV** listesinde mi; ÖTV için gereken bilgi (motor, perakende fiyat) | Maliyet aracı | Eksik bilgi uyarısını müşteriye ilet |
| 14 | **Ödeme şekli** (KKDF) | Sözleşme/proforma | Vadeli ise KKDF maliyete |

Gümrük genelgesi ve Bakanlık uygulaması için her kalemde: `legal_search_admin_guidance` `kurum: "Ticaret Bakanlığı"` `sorgu: "<konu>"`.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Tedarikçi üretici mi, aracı mı; üreticinin adı? | Damping firma oranı, menşe |
| Sevkiyat rotası (doğrudan mı, üçüncü ülke üzerinden mi)? | Menşe, doğrudan taşıma kuralı, saptırma riski |
| Eşya kendi üretiminizde mi kullanılacak, satılacak mı? | Nihai kullanım, DİR |
| Ödeme vadeli mi? | KKDF |
| Daha önce aynı ürünü getirdiniz mi; hangi denetimden geçti? | Denetim ve izin süreçleri |

---

## Çıktı iskeleti

```markdown
## İthalat ön kontrolü — [eşya, GTİP] — [menşe]
| # | Kontrol | Sonuç | Kaynak | Yapılacak |
### 🔴 Engel / 🟠 Belge ya da izin gerekiyor / 🟡 Dikkat
### Tahmini maliyet → gumruklenmis-maliyet.md tablosu
```

## Sık hatalar
- 🔴 Damping önlemini menşe değil sevk ülkesine göre aramak.
- 🟠 Askıya alma oranını eşya tanımını karşılaştırmadan uygulamak.
- 🟠 Gözetim ve ürün güvenliği denetimini tescil sonrasına bırakmak.
- 🟡 Tebliğin süre sonunu kontrol etmemek (önlem uzatılmış ya da kalkmış olabilir).
