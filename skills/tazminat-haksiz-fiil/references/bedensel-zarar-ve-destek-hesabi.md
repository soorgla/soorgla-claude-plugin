# Bedensel zarar ve destekten yoksun kalma: kalemler ve hesap yöntemi

## Ne zaman kullanılır
Yaralanma (geçici/sürekli iş göremezlik, tedavi, bakıcı) ya da ölüm (destekten yoksun kalma, cenaze) hâlinde talep edilebilecek kalemleri, hesap yöntemini, hangi soorgla aracının hangi girdiyi sağladığını ve faiz başlangıcını belirlemek. Sebep ne olursa olsun (trafik, malpraktis, genel haksız fiil, ürün) aynı yöntem uygulanır; iş kazasında SGK yönü için `../../sosyal-guvenlik-sgk/references/is-kazasi-ve-rucu.md`.

**Bu dosya hesap yapmaz, hesabı denetler.** Tutarlar aktüer bilirkişinin işidir; çıktıdaki her sayı `[doğrula — aktüer bilirkişiyle teyit edin]` etiketi alır.

---

## Kalemler (TBK m.53-54)
| Ölüm (m.53) | Bedensel zarar (m.54) |
|---|---|
| 1. Cenaze giderleri | 1. Tedavi giderleri |
| 2. Ölüm hemen gerçekleşmemişse tedavi giderleri ve çalışma gücü kaybı | 2. Kazanç kaybı |
| 3. Ölenin desteğinden yoksun kalanların kayıpları | 3. Çalışma gücünün azalması ya da yitirilmesi |
| | 4. Ekonomik geleceğin sarsılması |

Liste "özellikle" ifadesiyle sayılmıştır; bakıcı gideri gibi kalemler de istenebilir `[incele]`.

## Temel kurallar (TBK m.55)
- Destekten yoksun kalma ve bedensel zararlar **TBK hükümlerine ve sorumluluk hukuku ilkelerine göre** hesaplanır. 
- **Kısmen ya da tamamen rücu edilemeyen sosyal güvenlik ödemeleri** ile ifa amacı taşımayan ödemeler zarardan **indirilemez**. SGK'nın rücuya tabi gelirlerinin peşin sermaye değeri ise mükerrer ödemeyi önlemek için gözetilir `[incele]`. 
- Hesaplanan tazminat, **miktar esas alınarak hakkaniyet düşüncesiyle artırılamaz ya da azaltılamaz** (m.55/1 son cümle); indirim yalnız m.51-52 sebepleriyle olur.
- Bu hükümler **idari eylem ve işlemlerden** doğan ölüm ve vücut bütünlüğü kaybı davalarında da uygulanır (m.55/2) — kamu hastanesi ve idari yargı tam yargı davalarında da aynı hesap ilkeleri. 

### 7589 ile gelen yeni kurallar (yalnız 31.07.2026 ve sonrası olaylar)
- **Faiz başlangıcı:** zarar görenin ya da desteğin **kazancının bilindiği döneme** ilişkin tazminat toplamına **olay tarihinden**, **kazancın bilinemediği döneme** ilişkin toplamına **karar tarihinden** itibaren kanuni faiz.
- **Mahsup:** ifa amacıyla **tahkikat başlayıncaya kadar** ödenen bedel, ödeme tarihine göre belirlenecek tazminattan **oransal** olarak mahsup edilir.
- **Geçiş:** yalnız değişikliğin yürürlüğünden (31.07.2026) **sonra** meydana gelen haksız fiillere uygulanır; önceki olaylarda eski metin.

Önceki olaylarda faiz: haksız fiilde temerrüt olay tarihinde (TBK m.117/2); ZMSS sigortacısında başvuru/ödeme süresine göre (KTK m.97, m.99) `[incele]`. Sigortacıdan avans faizi istenip istenemeyeceği aracın ticari niteliğine göre değişir `[incele]`. 

---

## Hesap yöntemi (güncel Yargıtay uygulaması)

| Unsur | Güncel uygulama | Kaynak |
|---|---|---|
| Yaşam tablosu | **TRH-2010**. PMF-1931 daha kısa ömür verdiğinden yalnız davacı aleyhine olmayacak biçimde (ör. davacı istemiş ya da yalnız davalı istinaf etmişse) sonuca bırakılır. |  |
| İskonto | **Progresif rant** (gelir her yıl %10 artırılıp %10 iskonto edilir); Genel Şartlardaki **%1,8 teknik faiz uygulanmaz**. |  |
| Genel Şartlar yöntemi | AYM E.2019/40 iptali sonrası bağlayıcı değil; Genel Şartlar yalnız KTK ve TBK'ya aykırı olmayan ölçüde. |  |
| Maluliyet raporu | **Kaza tarihinde** yürürlükte olan düzenlemeye göre, beş dönem: 11.10.2008 öncesi Sosyal Sigortalar Sağlık İşlemleri Tüzüğü; 11.10.2008-01.09.2013 Çalışma Gücü ve Meslekte Kazanma Gücü Kaybı Oranı Tespit İşlemleri Yönetmeliği; 01.09.2013-01.06.2015 Maluliyet Tespiti İşlemleri Yönetmeliği; 01.06.2015-20.02.2019 Özürlülük Ölçütü yönetmeliği; 20.02.2019 sonrası Erişkinler İçin Engellilik Değerlendirmesi Hakkında Yönetmelik. 4. HD uyuşmazlık giderme kararında, Özürlülük ve Erişkinler yönetmeliklerinin ZMSS davalarında uygulanmayacağı yönündeki BAM görüşünü reddetti. Dönemi aktüerya aracı (`maluliyet_birlestir`) kaza tarihinden seçer. |  |
| Bakiye ömür | `legal_get_life_expectancy` (cinsiyet, yaş). Araç tablo adını döndürmez; değerleri TRH-2010 ile örtüşüyor. PMF-1931 değeri araçta yok. |  |
| Gelir | Belgeli gerçek gelir; belge yoksa asgari ücret (`legal_get_social_parameters` `asgari_ucret_net` / `asgari_ucret_brut`). Geçmiş dönem asgari ücretleri araçta yok → `[doğrula]`. | |
| Aktif / pasif dönem | Aktif dönem çoğunlukla 60 yaşa kadar, pasif dönem bakiye ömre kadar asgari ücret üzerinden `[model bilgisi — doğrulayın]` |  |
| Destek payları | Destek, eş ve çocuklar arasında pay dağılımı; çocukların destek süresi (kız/erkek, öğrenim durumu) `[model bilgisi — doğrulayın]` |  |
| Ödeme mahsubu | Sigortacının dava öncesi ödemesi: ödeme tarihi verileriyle hesap yapılıp ödemenin zararı karşılayıp karşılamadığı denetlenir; karşılamıyorsa rapor tarihi verileriyle hesaplanıp ödeme güncellenerek mahsup edilir (BAM ve 4. HD uygulaması; 31.07.2026 sonrası olaylarda TBK m.55/4). |  |

### Hesap denetim listesi (aktüer raporu geldiğinde)
Usul denetimi, maluliyet raporunun düzenleyeni, fark tablosu ve itiraz talebi türü → `bilirkisi-raporu-denetimi.md` (§3, §4.1-4.2); liste burada kalır.
Yeniden hesap `legal_calculate_actuarial_present_value` (`islem: tazminat | maluliyet_birlestir`) ile yapılır. Araç yanıt vermezse ya da hata dönerse tutar elle hesaplanmaz; araç varsa raporun kendi girdileriyle çalıştırılır, Yargıtay varsayılanlarından sapan parametre (65 yaş, teknik faiz) verilirse aracın sapma uyarısı aktarılır.
- [ ] Tablo TRH-2010 mı; teknik faiz mi progresif rant mı?
- [ ] Bilinen dönem / işleyecek dönem ayrımı ve tarihleri doğru mu (rapor tarihi)?
- [ ] Gelir: belgeli gelir mi asgari ücret mi; brüt/net tutarlı mı; dönem değerleri doğru mu?
- [ ] Maluliyet oranı hangi yönetmeliğe göre; olay tarihine uygun mu?
- [ ] Kusur indirimi (TBK m.52) ve ZMSS'de m.92/g-j kısıtları uygulandı mı?
- [ ] SGK peşin sermaye değeri: yalnız rücuya tabi kısım mı düşüldü (TBK m.55/1)?
- [ ] Dava öncesi ödemeler doğru yöntemle mahsup edildi mi?
- [ ] Faiz başlangıçları kalem kalem doğru mu (olay tarihi / temerrüt / karar tarihi)?
- [ ] ZMSS limiti kaza tarihine göre mi alındı?
- Rapora itiraz dilekçesi → `hukuk-yargilamasi-dilekce` (`../../hukuk-yargilamasi-dilekce/references/bilirkisi-itirazi-ve-esasa-beyan.md`).

---

## Usul notu: belirsiz alacak kalktı
31.07.2026'dan **sonra açılan** davalarda HMK m.107 (belirsiz alacak davası) uygulanmaz; tazminat davası **kısmi dava** olarak açılır ve talep aynı davada **bir defaya mahsus**, iddianın genişletilmesi yasağına takılmadan tahkikat sonuna kadar artırılabilir; zamanaşımı artırılan kısım için de dava tarihinde kesilmiş sayılır (HMK m.109/4). Daha önce açılmış belirsiz alacak davaları eski hükme göre sürer.  Aktüer raporu gelmeden dava açılacaksa bu ayrım dilekçenin talep kısmını belirler `[incele]`.

---

## Görüşme soruları
1. Olay tarihi (31.07.2026 öncesi mi sonrası mı)?
2. Zarar görenin doğum tarihi, cinsiyeti, mesleği, belgeli geliri (bordro, vergi kaydı)?
3. Maluliyet raporu: hangi kurum, hangi tarih, hangi yönetmelik, oran?
4. Geçici iş göremezlik süresi, tedavi ve bakıcı ihtiyacı?
5. (Ölüm) desteğin yaşı ve geliri; hak sahiplerinin doğum tarihleri, öğrenim durumları, evlilik durumları?
6. SGK gelir bağladı mı; peşin sermaye değeri?
7. Sigorta ya da sorumludan dava öncesi ödeme alındı mı; tarihi ve tutarı?
8. Kusur oranları ve kaynağı?

## soorgla çağrıları
```
legal_list_statute_articles  law_no: "6098"  law_type: "Kanun"  article_no: "5"  include_content: true   # m.50-58 (m.55'in 7589 fıkraları dâhil)
legal_get_life_expectancy  cinsiyet: "erkek" | "kadin"  yas: <tam sayı>
legal_get_social_parameters  tur: "asgari_ucret_net"
legal_get_legal_interest_rates
legal_calculate_cpi_change          # eski tarihli giderlerin güncellenmesi
legal_search_cases  mahkeme: "yargitay"  daire: "4. Hukuk Dairesi"  tarih_baslangic: "<son 3 yıl>"
    sorgu: "destekten yoksun kalma TRH 2010 progresif rant aktif dönem pasif dönem"
legal_search_cases  mahkeme: "yargitay"  daire: "4. Hukuk Dairesi"  sorgu: "uyuşmazlığın giderilmesi maluliyet yönetmeliği olay tarihi"
legal_get_statute_article  law_no: "6100"  article_no: "109"
```

## Çıktı iskeleti
```markdown
## Bedensel zarar / destek hesabı değerlendirmesi — [olay tarihi]
### Uygulanacak kurallar (TBK 55 eski/yeni; HMK 107 / 109/4)
### Girdiler
| Girdi | Değer | Kaynak (araç / belge) | Durum |
### Yöntem
- Tablo: … · İskonto: … · Dönemler: … · Kusur indirimi: … · Mahsup: …
### Kalemler
| Kalem | Formül | Tutar [doğrula] | Faiz başlangıcı |
### Rapora itiraz noktaları (varsa)
### Eksik bilgi
```

## Sık hatalar
- Eski YAML'daki TRH-2010 tablosunu metne kopyalayıp **%1,8 teknik faizle** hesaplamak (4. HD bunu bozma sebebi sayıyor).
- Bakiye ömrü bellekten yazmak; her seferinde `legal_get_life_expectancy`.
- 31.07.2026 öncesi olayda TBK m.55'in yeni faiz kuralını uygulamak (ya da tersini).
- Rücu edilemeyen SGK ödemelerini zarardan düşmek.
- Hesaplanan tazminatı "hakkaniyet" gerekçesiyle tutar üzerinden indirmek (m.55/1).
- 31.07.2026 sonrası davayı belirsiz alacak davası olarak kurmak.

