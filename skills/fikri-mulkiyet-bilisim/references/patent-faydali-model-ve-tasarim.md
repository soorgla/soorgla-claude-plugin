# Patent, faydalı model ve tasarım

## Ne zaman kullanılır
- "Buluşumuzu patentleyebilir miyiz?", "yazılım patentlenir mi?", "rakip bizim patentimizi kullanıyor", "bu ürünü piyasaya sürersek patent ihlali olur mu" (serbest kullanım triyajı), "verilen patente itiraz", "yıllık ücreti kaçırdık", "çalışanın buluşu kimin", "tasarımımız kopyalandı", "tescilsiz tasarım koruması".

**Bu bir triyajdır.** Patent kapsamı istemlerle belirlenir; istem yorumu ve eşdeğerlik teknik bilirkişi ve avukat işidir. Upstream `fto-triage` ve `infringement-triage` (patent kipi) uyarlandı: önce istem tablosu, sonra her unsurun ürünle karşılaştırması; "ihlal etmez" sonucu yazılmaz.

**Sınır:** Patent/tasarım lisans sözleşmesinin incelemesi → `../../sozlesme-incelemesi-tbk/SKILL.md`. Ar-Ge teşvikleri → `tesvik-yatirim`. Çalışanla iş sözleşmesindeki buluş maddesi → `../../is-hukuku/references/ise-alim-ve-rekabet-yasagi.md` (bu dosya SMK yönünü verir).

---

## Süre tablosu

| İşlem | Başlangıç | Süre | Dayanak |
|---|---|---|---|
| Patent koruma süresi | Başvuru tarihi | 20 yıl, uzatılamaz | SMK m.101/1  |
| Faydalı model koruma süresi | Başvuru tarihi | 10 yıl, uzatılamaz | SMK m.101/1 |
| Yıllık ücret | Başvurudan itibaren 2. yılın sonu, sonra her yıl vade (başvuru ay-günü) | Vadede ödenmezse ek ücretle 6 ay; o da kaçarsa hak vade tarihinde sona erer; sona erme bildiriminden 2 ay içinde telafi ücretiyle yeniden geçerlilik (üçüncü kişilerin kazanılmış hakları saklı) | SMK m.101/2-5 |
| Verilen patente itiraz (üçüncü kişi) | Verme kararının Bülten'de yayımı | 6 ay, ücretle | SMK m.99/1-2  |
| Patent sahibinin itiraza cevabı/değişiklik | İtirazın bildirimi | 3 ay | SMK m.99/4 |
| Kısmi uygunlukta değişiklik | Bildirim | 2 ay | SMK m.99/6 |
| Yenilik kaybettirmeyen açıklama (patent/FM) | Başvuru ya da rüçhan tarihinden geriye | 12 ay | SMK m.84  |
| Tescilli tasarım koruması | Başvuru tarihi | 5 yıl; 5'er yıllık yenilemeyle toplam 25 yıl | SMK m.69/1  |
| Tescilsiz tasarım koruması | Kamuya ilk sunma | 3 yıl | SMK m.69/2 |
| Tasarım yenilemesi | Bitimden önceki 6 ay; ek ücretle sonraki 6 ay | — | SMK m.69/4 |
| Tasarımda yenilik kaybettirmeyen kamuya sunma | Başvuru/rüçhan tarihinden geriye | 12 ay | SMK m.57/2  |
| İşverenin hizmet buluşu üzerinde hak talebi | Çalışanın bildiriminin işverene ulaşması | 4 ay, yazılı; süresinde bildirim yoksa buluş serbest | SMK m.115/1  |
| Kurum kararlarına itiraz (patent; m.99 itirazı saklı) | Bildirim | 2 ay; itirazı Kurul inceler | SMK m.100  |
| Tasarım kararına itiraz | Bildirim | 2 ay | SMK m.67/1 (alıntı)  |

---

## Kontrol listesi — patentlenebilirlik

1. **Üç şart:** yenilik, buluş basamağı, sanayiye uygulanabilirlik; teknolojinin her alanında (m.82/1).  Tanımlar m.83 `[doğrula]`.
2. **Buluş sayılmayanlar (m.82/2):** keşif, bilimsel teori, matematiksel yöntem; zihni faaliyet, iş yöntemi, oyun kuralları; **bilgisayar programları**; estetik mahsul ve eserler; bilginin sunumu. **Yalnız bunların "kendisi"** dışarıda kalır: teknik bir soruna teknik çözüm getiren bilgisayarla uygulanan buluşlar ayrı değerlendirilir `[incele]`. Yazılımın kendisi FSEK ile korunur → `telif-fsek-eser-ve-ihlal.md`.
3. **Patent verilmeyenler (m.82/3):** kamu düzeni/genel ahlaka aykırı; bitki çeşitleri ve hayvan ırkları (mikrobiyolojik işlemler hariç); teşhis, cerrahi ve tedavi yöntemleri (bu yöntemlerde kullanılan ürünler hariç, m.82/6); insan bedeninin öğelerinin salt keşfi; klonlama vb.
4. **Önceki açıklama:** başvurudan önceki 12 ayda buluşu yapanın kendisinin ya da ondan bilgi alan üçüncü kişinin açıklaması yeniliği bozmaz; ispat yükü bunu ileri sürende (m.84). Fuar, makale, yatırımcı sunumu, açık kaynak yayını kontrol et.
5. **Faydalı model mi patent mi?** Faydalı modelde buluş basamağı aranmaz ve inceleme daha hızlıdır; kapsam m.142/1 (yenilik + sanayiye uygulanabilirlik); kimyasal/biyolojik madde ve usuller, eczacılık, biyoteknolojik buluşlar ve **usul buluşları** faydalı modelle korunmaz (m.142/3). Faydalı model verildikten sonra m.99 itirazı yok, yalnız mahkemede hükümsüzlük (m.143/11); hükümsüzlük davası koruma süresince ya da sona ermeden sonraki 5 yıl içinde (m.144/3). 
6. **Gizlilik:** başvuru öncesi açıklamalar NDA ile mi yapıldı → `../../sozlesme-incelemesi-tbk/references/nda-ve-niyet-mektubu.md`.

## Kontrol listesi — serbest kullanım triyajı (FTO, upstream `fto-triage`)

- [ ] İlgili patentler: kullanıcıdan patent numarası ve **istemler** (soorgla'da patent veri tabanı yok; `[kullanıcı verdi]` ya da `[web araması — doğrulayın]`).
- [ ] Patent Türkiye'de geçerli mi (TR tescili ya da Türkiye'de geçerlilik kazanmış Avrupa patenti), yıllık ücretler ödenmiş mi, süre dolmuş mu (m.101)?
- [ ] **İstem tablosu:** bağımsız istemin her unsuru ↔ ürünün karşılık gelen özelliği ↔ mevcut mu (evet/hayır/belirsiz). Bir unsur yoksa literal ihlal zayıflar; eşdeğerlik ihtimali `[incele]`.
- [ ] Dolaylı kullanım (buluşun esaslı unsurlarını, buluşu uygulamaya yeterli ve bu amaçla kullanılacağını bilerek yetkisiz kişiye sağlama; piyasada her zaman bulunan ürünlerde teşvik şartı) m.86.
- [ ] Önceki kullanım hakkı (m.87: başvuru tarihinde ya da önce iyiniyetle ülke içinde kullanım ya da ciddi hazırlık; işletmenin makul ihtiyacıyla sınırlı; lisansla genişletilemez, yalnız işletmeyle devredilir), hakkın kapsamı ve sınırları (m.85/3: ticari amaçsız özel fiiller, deneme amaçlı fiiller, ilaç ruhsatı için test ve deneyler, eczanede reçeteye göre hazırlama, geçici olarak ülkede bulunan taşıtlar). 
- [ ] Hükümsüzlük ihtimali (m.138) ve itiraz süresi açık mı (m.99, 6 ay).
- Çıktı: istem tablosu + risk düzeyi + "bu bir serbest kullanım görüşü değildir".

## Kontrol listesi — patent/faydalı model tecavüzü (hak sahibi)

- [ ] Tecavüz fiilleri m.141 (üretme, satma, kullanma, ithal, usul patentinde doğrudan elde edilen ürün; gasp; lisans haklarını izinsiz genişletme/devretme). Usul patentinde yeni ürün için ispat yükü davalıya geçebilir (m.141/2); başvuru yayımından itibaren dava hakkı (m.141/3). 
- [ ] Talepler ve tazminat SMK m.149-151 (bkz. `marka-tecavuz-ve-hukumsuzluk.md`); **patentini kullanma yükümlülüğünü yerine getirmeyen** hak sahibinde yoksun kalınan kazanç yalnız makul lisans bedeliyle hesaplanır (m.151/5). 
- [ ] Kullanmama → zorunlu lisans riski (m.129-130) `[doğrula]`.
- [ ] İhtiyati tedbirde usul patenti vasıtalarına el koyma (m.159/2-b).

## Kontrol listesi — hizmet buluşu (çalışan buluşları, m.113-122)

- [ ] Buluş hizmet buluşu mu (iş ilişkisi sırasında, yükümlü olunan faaliyet gereği ya da büyük ölçüde işletmenin deneyim ve çalışmalarına dayanarak) yoksa serbest buluş mu (m.113); öğrenci ve ücretsiz stajyerler de çalışan sayılır (m.113/3).
- [ ] Çalışan buluşu yazılı ve gecikmeksizin bildirdi mi (m.114/1); işveren 2 ay içinde düzeltme istemezse bildirim geçerli sayılır (m.114/4).
- [ ] İşveren 4 ay içinde yazılı tam/kısmi hak talebinde bulundu mu; bulunmadıysa buluş serbest (m.115/1). Tam talepte haklar bildirimin çalışana ulaşmasıyla işverene geçer (m.115/2).
- [ ] Çalışana **makul bedel** (m.115/6-7); hükümler çalışan aleyhine değiştirilemez, sözleşme serbestliği hizmet buluşunda patent başvurusundan sonra başlar; hakkaniyete aykırı sözleşme/bedel itirazı iş sözleşmesinin bitiminden itibaren 6 ay içinde yazılı (m.117).
- [ ] Yükseköğretim (m.121: kurum hak talep ederse başvuru yapmakla yükümlü; m.115, 116, 118 uygulanmaz) ve kamu destekli projeler (m.122: destek veren kuruma bildirim, bildirimden 1 yıl içinde hak sahipliği tercihi) ayrı rejim. 7592 m.9 (RG 09.08.2026) ile 2547 ek m.32'ye fıkralar eklendi: yükseköğretim kurumu yönetim kurulu, masrafları teknoloji transfer ofisi sermayesinden karşılanmak şartıyla hizmet buluşlarının hak sahipliğini ofise devredebilir; gelir paylaşımı, ortak ofis ve ofisin yatırım yapması da aynı maddede (oranları maddeden çek). 
- Tasarımda çalışan hak sahipliği ayrıca m.73-74.

## Kontrol listesi — tasarım

- [ ] Yenilik ve ayırt edici nitelik (m.56): bilgilenmiş kullanıcı nezdinde genel izlenim; tasarımcının seçenek özgürlüğü dikkate alınır; küçük ayrıntılarda farklı tasarımlar aynı sayılır (m.56/4-6). 
- [ ] Kamuya sunma tanımı: sergileme, satış, kullanma, yayım; gizlilik şartıyla açıklama sayılmaz; 12 aylık hoşgörü (m.57). 
- [ ] Tescilli mi, tescilsiz mi? Tescilsiz tasarım 3 yıl ve yalnız kopyalamaya karşı korunur (m.69/2; kapsam m.59) `[doğrula]`. 6769 öncesi olaylarda (554 sayılı KHK) tescilsiz tasarım koruması yoktu; bu dönemde ürün görünümü taklidi haksız rekabetle korunuyordu (11. HD E.2022/5205 K.2024/1610'daki BAM gerekçesi). 
- [ ] Tecavüz fiilleri m.81; hükümsüzlük m.77-78 `[doğrula]`.
- [ ] Görünüm aynı zamanda marka (üç boyutlu) ya da eser olabilir: korumaları ayrı ayrı yürüt.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Patent/tasarım numarası, istemler, başvuru ve rüçhan tarihi; yıllık ücret dökümü? | Geçerlilik ve kapsam |
| Buluş/tasarım ilk ne zaman, nerede açıklandı (fuar, makale, satış, GitHub)? | m.84, m.57 |
| Buluşu kim yaptı; çalışan mı, danışman mı, üniversite ile ortak mı? | m.113-122, hak sahipliği |
| Ürünün teknik dokümanı ya da örneği var mı? | İstem tablosu |
| Türkiye dışında başvuru planı var mı? | Rüçhan (m.93-94) |

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "6769"  law_type: "Kanun"  article_no: "82" | "83" | "84" | "85" | "86" | "87" | "99" | "100" | "101" | "113" | "114" | "115" | "117" | "121" | "138" | "141" | "142" | "151"
legal_get_statute_article  law_no: "6769"  law_type: "Kanun"  article_no: "55" | "56" | "57" | "58" | "59" | "69" | "73" | "77" | "81"
legal_search_cases  mahkeme: "yargitay"  sorgu: "<patent istem kapsamı eşdeğerlik / tescilsiz tasarım / hizmet buluşu bedeli>"  tarih_baslangic: "<son 3 yıl>"
legal_search_cases  mahkeme: "bam"  sorgu: "<konu> patent hükümsüzlüğü"
legal_search_official_gazette  query: "Türk Patent ve Marka Kurumunca Uygulanacak Ücret Tarifesi"  search_in: "title"  sort_by: "date_desc"
```

---

## Çıktı iskeleti

```markdown
## [Patentlenebilirlik / FTO / tecavüz / hizmet buluşu / tasarım] — [konu]
> Bu bir triyajdır; ihlal ya da serbest kullanım görüşü değildir.
### Hak durumu (no, tarih, geçerlilik, yıllık ücret)
### İstem tablosu
| İstem unsuru | Ürün özelliği | Var mı | Not |
### Riskler ve savunmalar
### Süreler
### Öneri — [incele]
```

---

## Sık hatalar

- 🔴 Yıllık ücret vadesini ve 6 aylık ek süreyi kaçırmak (m.101/3-4).
- 🔴 Başvurudan önce 12 aydan eski açıklamayı gözden kaçırmak (m.84).
- 🟠 "Yazılım patentlenemez" diye kesip atmak; yalnız programın kendisi dışarıda (m.82/2).
- 🟠 İşverenin 4 aylık hak talebi süresini kaçırması (buluş serbest kalır).
- 🟠 Tescilsiz tasarım korumasını 6769 öncesi olaylara uygulamak.
- 🟡 İstem tablosu yapmadan "benzer ürün = ihlal" demek.

---

