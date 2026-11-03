# İhracat — günlük işlemler

## Ne zaman kullanılır
- İhracat beyannamesi hazırlığı, e-ihracat (ETGB, mikro ihracat), ihracatçı olarak menşe belgesi düzenletme, ihracatta yerinde gümrükleme.
- İhracat bedelinin yurda getirilmesi ve IBKB'nin işleyişi (bilgi düzeyinde).
- Bedel **gelmedi**, ihbar ya da kambiyo yaptırımı varsa → `../../gumruk-dis-ticaret/references/ihracat-kambiyo-ve-e-ihracat.md`.

---

## Akış

1. **GTİP ve ihracat rejimi:** ihracatı yasak, kayda ya da izne bağlı mı (İhracat Rejimi Kararı ve ilgili tebliğler → `legal_search_official_gazette` `query: "İhracat"` `search_in: "title"`); ürün bazlı ihracat talimatları (Tarım ve Orman, ör. su ürünleri, canlı hayvan) form bankasında.
2. **Beyan yolu:** standart ihracat beyannamesi, e-ihracat (ETGB / mikro ihracat — değer ve ağırlık sınırları, muafiyet kodları 2020/25 sayılı Posta ve Hızlı Kargo Taşımacılığı Genelgesinde, 2020/28 ile değişik; güncel hâlini `legal_search_admin_guidance` `kurum: "Ticaret Bakanlığı"` `sorgu: "posta ve hızlı kargo ETGB"` ile çek), yerinde gümrükleme ya da izinli gönderici (`yys-ve-kolaylastirmalar.md`).
3. **Teslim şekli ve kıymet:** Incoterms → beyanname teslim şekli kodu (`beyanname-kodlari-ve-formlar.md`); FOB kıymet istatistik ve ihracat bedeli için.
4. **Menşe belgesi:** alıcı ülkenin tercihli rejimine göre A.TR, EUR.1/EUR-MED, fatura beyanı ya da menşe şahadetnamesi (`mense-belgeleri.md` tablosunu alıcı ülke tarafından oku); düzenleyen merci (oda, gümrük) ve onaylanmış ihracatçı statüsü `[doğrula]`.
5. **DİR/HİR bağlantısı:** ihracat DİİB taahhüdünü kapatıyorsa beyannamede belge bağlantısı (`rejimler-gunluk.md`).
6. **Bedel ve kambiyo:** bedelin yurda getirilme süresi ve bankaya satış (IBKB) — 32 sayılı Karar tebliği ve TCMB İhracat Genelgesi, sık değişir `[doğrula]`; süre defterine ekle.
7. **KDV yönü** (ihracat istisnası, ihraç kayıtlı teslim) → `../../vergi/SKILL.md` / `../../muhasebe/references/kdv-uygulamalari.md`.

Genelge ve rehber araması:
```
legal_search_admin_guidance sorgu: "<konu> ihracat" kurum: "Ticaret Bakanlığı" belge_tur: "genelge"
legal_search_forms sorgu: "ihracatta yerinde gümrükleme kılavuzu" (araç yoksa FORM-KAYNAKLARI)
```

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Alıcı ülke ve teslim şekli? | Menşe belgesi, teslim kodu |
| Gönderi büyüklüğü ve taşıma (kargo, posta, konteyner)? | E-ihracat mı standart beyan mı |
| Eşya DİİB kapsamında mı? | Taahhüt kapatma |
| Ödeme şekli ve vade? | Bedel getirme süresi |

---

## Çıktı iskeleti

```markdown
## İhracat hazırlığı — [eşya, GTİP] — [alıcı ülke]
| Kalem | Değer / belge | Kaynak |
| Beyan yolu | … | |
| Teslim şekli kodu | … | kod listesi |
| Menşe belgesi | … | anlaşma |
| İzin/kayıt | … | tebliğ |
| Bedel getirme son günü | … [doğrula] | 32 sayılı Karar tebliği |
```

## Sık hatalar
- 🟠 Alıcı ülkenin tercihli rejimine bakmadan menşe şahadetnamesi düzenletmek (alıcı tercihli orandan yararlanamaz).
- 🟠 DİİB bağlantısını beyannameye işlememek.
- 🟡 Bedel getirme süresini eski tebliğe göre hesaplamak.
