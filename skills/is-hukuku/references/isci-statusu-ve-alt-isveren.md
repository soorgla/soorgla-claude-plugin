# İşçi statüsü, alt işveren ve muvazaa

İki soru:
1. **Bu kişi işçi mi?** Serbest çalışan, hizmet sağlayıcı, danışman, şirket ortağı ya da "freelance" olarak kurgulanan ilişki gerçekte iş sözleşmesi mi?
2. **Asıl işveren-alt işveren ilişkisi geçerli mi?** Alt işverenlik (taşeron) kurulabilir mi, mevcut ilişki muvazaalı mı, ödünç (geçici) iş ilişkisi kurallarına uyuluyor mu?

Upstream karşılığı: `employment-legal/skills/worker-classification`. Upstream'deki "yalnız ileriye dönük" kapısı aynen alındı. ABD testleri (ABC testi, IRS ölçütleri) atıldı; yerine 4857 m.2 ve m.7, Alt İşverenlik Yönetmeliği ve Yargıtay içtihadı kondu.

---

## İleriye dönük mü, geriye dönük mü? (kapı)

- **Henüz kurulmamış ilişki** ("bu kişiyi serbest çalışan olarak alabilir miyiz?", "bu işi taşerona verebilir miyiz?") → bu akışı yürüt.
- **Yürüyen ya da sona ermiş ilişki** (kişi zaten çalışıyor, dava ya da müfettiş incelemesi var) → bu artık bir sınıflandırma değil, **muvazaa ve geriye dönük risk** analizidir. Çıktının başına şunu yaz: "Bu, yürüyen bir ilişkinin geriye dönük risk değerlendirmesidir; işçilik alacakları, SGK primi ve idari para cezası riski doğurabilir. Avukat incelemesi şarttır." Sonra aynı kontrol listesini risk diliyle yürüt; alacaklar için `iscilik-alacaklari.md`, SGK tarafı için `../../sosyal-guvenlik-sgk/references/hizmet-tespiti.md` ve `../../sosyal-guvenlik-sgk/references/sgk-uyum-ve-itiraz.md` (`sosyal-guvenlik-sgk` becerisi).

---

## Bölüm A — İşçi mi, bağımsız çalışan mı?

İş sözleşmesinin unsurları: iş görme, ücret ve **bağımlılık**. Ayırıcı olan bağımlılıktır. Tanımı `legal_get_statute_article 4857/2` ve `6098/393` ile çek.

| Gösterge | İşçi yönünde | Bağımsız yönünde |
|---|---|---|
| Talimat ve denetim | İşin nasıl, ne zaman, nerede yapılacağını işveren belirliyor | Kişi yalnız sonuçtan sorumlu |
| İşyeri organizasyonuna katılım | Vardiya, mesai, kartlı giriş, kurumsal e-posta, unvan | Kendi işyeri ve araçları |
| Süreklilik ve tek müşteri | Tek işverene sürekli çalışıyor | Birden çok müşteri |
| Ücret | Sabit aylık ödeme, fatura yalnız biçimsel | İş başına fiyat, girişimci riski |
| Kişisel ifa | Başkasını görevlendiremez | Yardımcı ya da alt yüklenici kullanabilir |

- Sözleşmenin adı belirleyici değildir; fiili durum esastır `[incele]`. Güncel ölçütleri `legal_search_cases` (9. HD, HGK) ile çek, sorgu: "hizmet sözleşmesi ile vekâlet ya da eser sözleşmesinin ayrımı bağımlılık unsuru".
- Şirket ortağı ya da yönetim kurulu üyesinin aynı zamanda işçi sayılıp sayılamayacağı ayrı bir sorundur → içtihadı çek, SGK statüsü için `../../sosyal-guvenlik-sgk/references/emeklilik-ve-borclanma.md` (5510 m.53, `sosyal-guvenlik-sgk` becerisi).
- Sonuç işçi ise: SGK bildirimi, iş güvencesi, kıdem, fazla çalışma. Geriye dönük kurguda bu kalemlerin tamamı risktir.

## Bölüm B — Asıl işveren-alt işveren

`legal_get_statute_article 4857/2` (altıncı ve yedinci fıkralar) ile çek ve sırayla kontrol et:

1. **Verilen iş:** yardımcı iş mi, asıl işin bir bölümü mü? Asıl işin bölümü ise işletmenin ve işin gereği **ve** teknolojik nedenlerle uzmanlık gerektiriyor mu? Bu şartlar yoksa asıl iş bölünerek alt işverene verilemez. 
2. **Yalnız o işyerinde çalıştırma:** alt işverenin bu iş için görevlendirdiği işçiler yalnız o işyerinde mi çalışıyor?
3. **Muvazaa karinesi:** asıl işverenin işçileri alt işverence işe alınarak çalıştırılmaya devam ediliyor ve hakları kısıtlanıyor mu? Daha önce o işyerinde çalışan kişiyle alt işveren ilişkisi kuruluyor mu? Bu hâllerde ilişki muvazaalı kabul edilir ve alt işverenin işçileri başlangıçtan itibaren asıl işverenin işçisi sayılır. 
4. **Birlikte sorumluluk:** geçerli ilişkide asıl işveren, alt işverenin işçilerine karşı o işyeriyle ilgili yükümlülüklerden alt işverenle birlikte sorumludur.
5. **Bildirim ve tescil:** alt işverenliğin bölge müdürlüğüne bildirimi, belgeler ve inceleme → Alt İşverenlik Yönetmeliği (`legal_search_statute_semantic` "Alt İşverenlik Yönetmeliği").
6. **İşaretler:** alt işverenin kendi organizasyonu, ekipmanı, uzmanlığı var mı? Talimatı kim veriyor? Ücreti kim belirliyor? Aynı işi asıl işverenin kadrolu işçileri de yapıyor mu? 🟠

**Kamu kesimi:** 4734 kapsamındaki hizmet alımlarında yüklenici işçilerinin kadro ve mali hak talepleri sınırlanmıştır (`4857/2` sekizinci ve dokuzuncu fıkralar). 2026'da eklenen geçici m.12 (7573/6), 11.09.2014-15.10.2019 arasında 4734 m.62/1-e uyarınca imzalanan ihale sözleşmelerinde kamu idaresinin ödediği kıdem tazminatının alt işverene **rücuya konu kısmının tahsilinden vazgeçilmesini** düzenliyor: derdest rücu davalarında karar verilmesine yer olmadığına hükmedilir, icra takipleri düşer; önceden tahsil edilmiş tutarlar iade edilmez → `legal_get_statute_article 4857 "geçici 12"` ile çek. 

## Bölüm C — Geçici (ödünç) iş ilişkisi

- Holding/şirketler topluluğu içinde ya da özel istihdam bürosu aracılığıyla devir mi? Hangi hâllerde ve ne kadar süreyle kurulabileceğini `4857/7` ile çek.
- İşçinin yazılı rızası alındı mı?
- Geçici işverenin ve özel istihdam bürosunun sorumlulukları; SGK bildiriminde müteselsil sorumluluk (`5510/86` üçüncü fıkra). 

## Görüşme soruları

1. İlişki henüz kurulmadı mı, yürüyor mu, sona erdi mi?
2. Kişi ya da alt işveren hangi işi yapıyor; bu iş asıl iş mi, yardımcı iş mi?
3. Talimatı kim veriyor, mesai ve izin kimin onayına bağlı?
4. Kişi/alt işveren işçileri daha önce sizin işçiniz miydi?
5. Alt işverenin başka müşterileri, kendi ekipmanı, uzmanlık belgesi var mı?
6. Sözleşme, fatura, SGK bildirimi kimin üzerinden?
7. Kamu kurumu mu, 4734 kapsamında ihale mi?

## soorgla çağrıları

```
legal_get_statute_article  law_no: "4857"  article_no: "2" | "7"
legal_get_statute_article  law_no: "4857"  article_no: "geçici 12"
legal_get_statute_article  law_no: "6098"  article_no: "393"
legal_get_statute_article  law_no: "5510"  article_no: "86"
legal_search_statute_semantic  sorgu: "Alt İşverenlik Yönetmeliği bildirim ve muvazaa incelemesi"
legal_search_cases  mahkeme: "yargitay"  daire: "9. Hukuk Dairesi"
    sorgu: "<ör. asıl işin bölünerek alt işverene verilmesi uzmanlık gerektirmeyen iş muvazaa>"
    tarih_baslangic: <son 3 yıl>
legal_search_cases  mahkeme: "yargitay"  daire: "Hukuk Genel Kurulu"  sorgu: "<olay>"
legal_search_admin_guidance  sorgu: "alt işveren muvazaa"      # kapsam dar olabilir; ORTAK-KURALLAR.md §5
```

## Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1]

## İşçi statüsü / alt işveren değerlendirmesi: [ilişki] — [tarih]
**Tür:** ileriye dönük sınıflandırma / geriye dönük risk · **Taraf:** …

### Sonuç
[İşçi / bağımsız; alt işverenlik geçerli / muvazaa riski yüksek — tek cümle neden]

### Göstergeler
| Gösterge | Olgu | Yön | Dayanak [soorgla] |

### Alt işverenlik şartları
| Şart | Durum | Not |

### Riskler (geriye dönükse)
[işçilik alacakları, SGK primi ve İPC, işe iade — ilgili dosyalara yönlendir]

### Emsal kararlar
### Eksik bilgi
```

---

## Kaynak
- Upstream: `claude-for-legal-upstream/employment-legal/skills/worker-classification/SKILL.md` (Apache-2.0), Türk hukukuna uyarlandı.
- Eski YAML: `analysis/employment_hr_docs/subcontractor_agreement.yaml` **boş (0 bayt)**; bu dosya sıfırdan yazıldı.
