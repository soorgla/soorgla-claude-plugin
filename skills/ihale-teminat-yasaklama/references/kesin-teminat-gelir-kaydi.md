# Kesin ve ek kesin teminatın gelir kaydı (sözleşme aşaması)

Sözleşme imzalandıktan sonra kesin teminat (%6, 4734 m.43) ve ek kesin teminatın gelir kaydı, güncellenmesi,
yazışması ve yasaklama ile bağı. **Fesih şartlarının esası, tasfiye hesabı, kabul ve teminat iadesi** (4735 m.13-14)
`../../hakedis/references/fesih-tasfiye-ve-kabul.md`'dedir; burada yalnız teminat yönü ve süreç vardır.

---

## 1. Gelir kaydı hâlleri

| Hâl | Kesin + ek kesin teminat | Tasfiye | Yasaklama | Dayanak |
|---|---|---|---|---|
| Taahhüdün dokümana/sözleşmeye uygun yerine getirilmemesi ya da süresinde bitirilmemesi; **en az 10 gün süreli, nedenleri açık ihtara** rağmen devam | Protesto gerekmeksizin gelir | Genel hükümlere göre | ✅ 4735 m.22 son fıkra → m.26 işlemi: **1-2 yıl** (m.26/1); dayanak fiil m.25/f (mücbir sebep dışında taahhüdü yerine getirmemek) | 4735 m.20/a  |
| Sözleşme uygulanırken m.25 yasak fiili (fesat, sahte belge, hileli malzeme, idareye zarar, m.29 aykırılığı, mücbir sebep dışında taahhüdü yerine getirmeme, izinsiz devir) | Gelir | Genel hükümlere göre | ✅ m.26 (1-2 yıl) | 4735 m.20/b, m.25, m.26 |
| İhale aşamasındaki 4734 yasak fiilinin **sözleşmeden sonra** tespiti | Gelir + fesih | Genel hükümlere göre | ✅ m.26 | 4735 m.21/1  |
| Aynı, ama taahhüdün **en az %80**'i tamam + kamu yararı + (a) ivedilik / (b) başkasına yaptırılamama / (c) fiil tamamlamaya engel değil | **Fesih yok**; yükleniciden kesin + ek kesin teminat tutarı kadar **ceza** tahsil edilir (hakedişten kesilebilir) | — | ✅ m.26 yine uygulanır | 4735 m.21/2 |
| Yüklenicinin mali acz bildirimi (m.19) | Gelir | Genel hükümlere göre | m.22 son fıkra → m.26 işlemi, **1-2 yıl**; m.26 yasaklamayı m.25 fiiline bağlar, mali acz bildiriminin hangi bende (m.25/f?) dayandırılacağı metinde yazılı değil `[incele]` | 4735 m.19, m.22 → `hakedis`  |
| Mücbir sebeple fesih (m.23) | **İade** | Genel hükümlere göre | ❌ | `hakedis` |
| İhale tarihinde yasaklı olduğu sözleşmeden sonra anlaşıldı | Gelir + m.21 fesih | Genel hükümlere göre | — | KİGT 28.1.8.1/4  |

**Ortak girişim (yüklenici OG ise):** sözleşme sonrası m.25 fiilinde fiili işleyen ve iştirak eden ortaklar hakkında
yasaklama verilir ve sözleşme m.18'e paralel feshedilir; ihale aşaması m.17 fiilinde aynı ortaklar yasaklanır ve m.21
uyarınca fesih (KİGT 28.1.7/2) `[soorgla]`. 

## 2. Süreç ve süreler

| # | Adım | Kim → kime | Süre | Dayanak |
|---|---|---|---|---|
| 1 | İhtar (m.20/a) | İdare → yüklenici | En az **10 gün** süreli, nedenleri açık; gecikme cezası uygulanmak üzere. Bitişi ihtarda **tam tarih** olarak yaz | 4735 m.20/a; kod `kik_4735_default_notice` yalnız asgari süre kontrolü için (aşağıdaki uyarı) |
| 2 | Fesih **sayılma** anı | — | m.19: talebin idareye intikali; m.20/a: ihtarda **belirlenen** sürenin bitimi (tatile göre kaydırılmış gün değil); m.20/b ve m.21: **tespit tarihi** | 4735 m.22/1 `[soorgla]` |
| 3 | Fesih kararı | İdare (ihale yetkilisi) | 2. satırdaki tarihi izleyen **7 gün** içinde | 4735 m.22/1; `kik_4735_termination_decision` |
| 4 | Fesih kararının bildirimi | İdare → yüklenici | Karar tarihini izleyen **5 gün** içinde | 4735 m.22/1; `kik_4735_termination_notice` |
| 5 | Teminatın güncellenmesi | İdare / muhasebe | Alındığı tarihten gelir kaydı tarihine kadar endeksle; fark yükleniciden tahsil | 4735 m.22/2 (metinde "DİE toptan eşya fiyat endeksi"; bugünkü karşılığı Yİ-ÜFE `[incele]`) |
| 6 | Hakedişten kesintiyle alınan teminat | İdare | Alıkonulan tutar gelir + yapılmayan iş miktarına isabet eden teminat güncellenerek tahsil | 4735 m.22/3 |
| 7 | Muhasebeye gelir kaydı yazısı + mektubun paraya çevrilmesi | İdare → muhasebe → banka | Fesih kararından sonra gecikmeksizin; mektup süresi içinde | MYMY m.458/4  |
| 8 | Yasaklama teklifi | İdare → ilgili/bağlı bakanlık (yetkili makam) | Fesih + m.26 → `yasaklama-sureci-ve-takvim.md` | 4735 m.22 son fıkra, m.26/5 |
| 9 | Zarar ziyanın tazmini | İdare → yüklenici | Genel hükümler; adli yargı | 4735 m.22 son fıkra |

- 🟠 **Araç tuzağı (`kik_4735_default_notice`):** araç 10 günün son gününü tatile göre kaydırır (04.11.2026 tebliğ →
  ham 14.11.2026 Cumartesi → 16.11.2026). 7 günlük fesih kararı süresini araçtaki 16.11'den değil, ihtarda belirlenen
  14.11'den say: son gün **21.11.2026** (Cumartesi; uzamamış say, kararı 20.11 Cuma'ya kadar al) `[incele]`. Yüklenici
  açısından ifa için kalan süre de ihtardaki tarihtir; tatil uzamasına güvenmesin. 
- **Gelir kaydedilen teminat yüklenicinin borcuna mahsup edilemez** (m.22/4) `[soorgla]`: tasfiye hesabında
  teminat "alacak" diye düşülmez; zarar ayrıca istenir.
- **Kesin teminatın gelir kaydı, fesih gerçekleşmeden yapılamaz** — Sayıştay da bu yönde (Sayıştay 6. D. K.654,
  11.04.2019 arama özeti, tam metin okunmadı `[çekildi ama desteği doğrulayın]`); güncellenmeden gelir kaydı Sayıştay
  sorgusu konusu (8. D. K.171, 29.11.2019 özeti) → `../../kamu-mali-denetim-sayistay/SKILL.md`.
  
- Kesin teminat miktarı ve iade şartları sözleşmede yazılı olmak zorundadır (4735 m.7/k) `[soorgla]`; sözleşmedeki
  gelir kaydı maddesi 4735'e aykırı olamaz (m.4: ihale dokümanına aykırı hüküm yok, eşit hak ve yükümlülük) `[soorgla]`.

## 3. Kısmi kabul, geçici kabul ve iade ile ilişkisi
- Taahhüdün müstakil kullanıma elverişli tamamlanan bölümleri için **kısmi kabul** yapılabilir (4735 m.11) `[soorgla]`.
  Kısmi kabulün teminatın bir kısmını serbest bırakıp bırakmadığı sözleşme ve tür yönetmeliğine bağlıdır `[incele]`;
  muhasebe tarafında mektubun bir kısmı serbest bırakılacaksa muhasebe birimi bankaya yazar (MYMY m.458/2) `[soorgla]`.
- Yapımda geçici kabulde kesin teminatın yarısı, kesin kabul + SGK ilişiksizlikte kalanı iade edilir; bu iade
  yapıldıktan sonra fesih/gelir kaydı **yalnız elde kalan** teminat üzerinden yapılabilir `[incele]` → ayrıntı ve
  madde: `../../hakedis/references/fesih-tasfiye-ve-kabul.md` §3.
- Kesin kabulden sonra m.25 fiilinin tespiti: fesih konusu kalmaz, ama m.26 yasaklaması ve 4735 m.27 / 4734 m.59
  suç duyurusu yolu açıktır `[incele]` (4734 m.59 "taahhüt tamamlandıktan ve kabul işlemi yapıldıktan sonra tespit
  edilmiş olsa dahi") `[soorgla]`. 

## 4. Yargı yeri (özet)
Sözleşme imzalandıktan sonra sözleşmenin uygulanmasından doğan **fesih ve kesin teminatın gelir kaydı**
uyuşmazlığı **adli yargıda** görülür; idare mahkemesinde açılan iptal davası görev yönünden reddedilir (Danıştay 13.
D. E.2023/497 K.2023/1152, 14.03.2023) `[soorgla]`. Ayrıntı ve istisnalar: `istekli-itiraz-ve-dava.md` §1.

## 5. Kontrol listesi
- [ ] Fesih sebebi hangi madde (m.19, 20/a, 20/b, 21)? m.20/a'da ihtar süresi ve içeriği yeterli mi?
- [ ] m.21'de %80 + kamu yararı istisnası değerlendirildi mi?
- [ ] Fesih kararı 7 gün, bildirim 5 gün içinde mi?
- [ ] Gelir kaydedilecek teminatın kalan tutarı (geçici kabulde iade edilen yarı düşülerek) ve güncelleme hesabı.
- [ ] Mektubun geçerlilik süresi; muhasebeye yazı tarihi.
- [ ] m.26 yasaklama teklifi ve 45 gün takvimi açıldı mı? Ortaklar (sirayet) tespit edildi mi?
- [ ] Zarar-ziyan ve tasfiye ayrı ayrı mı hesaplanıyor (mahsup yasağı)?

## 6. Sık hatalar
- 🔴 Fesih ve gelir kaydına karşı idare mahkemesinde dava açmak (istekli) / idare mahkemesinde savunma verirken görev
  itirazını atlamak (idare).
- 🔴 Mücbir sebeple feshte teminatı gelir kaydetmek.
- 🟠 Güncelleme farkını tahsil etmemek; gelir kaydedilen teminatı tasfiye alacağına mahsup etmek (m.22/4).
- 🟠 m.21/2 istisnasında feshetmeden devam ettirirken m.26 yasaklamasını ve ceza tahsilini unutmak.
- 🟡 Sözleşme sonrası fiillerde 4734 m.58 (ihale) yerine 4735 m.26 dayanağını ve "sözleşmeyi uygulayan bakanlık"
  yetkisini yazmamak.
