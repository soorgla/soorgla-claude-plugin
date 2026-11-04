# Sözleşme değişiklik geçmişi ve iş birimine sade özet

İki yardımcı akış: (1) ana sözleşme ve ek protokollerin zaman içindeki değişimini çıkarmak ya da tek bir maddenin bugünkü geçerli metnini bulmak; (2) tamamlanmış bir incelemeyi hukukçu olmayan karar vericiye iki paragrafta anlatmak.

Upstream `amendment-history` ve `stakeholder-summary` becerilerinden uyarlanmıştır.

---

## A. Değişiklik geçmişi

### Ne zaman kullanılır
- "Ek protokollerle sözleşme ne hâle geldi", "bu madde şimdi ne diyor", "hangi ek protokol geçerli", birden çok sürüm ya da ek yüklenmiş.

### Kip seçimi (sormadan belirle; gerçekten belirsizse tek soru sor)
- **Kip 1 — Özet:** "ne değişti", "değişiklik geçmişi", "sözleşmenin bugünkü hâli".
- **Kip 2 — Madde izi:** belirli bir madde adı geçiyor ("sorumluluk", "fesih", "fiyat", "yenileme", "kişisel veri", "fikri mülkiyet"). Terim birden çok maddeye denk geliyorsa adayları say ve hangisi diye sor.

### Adım 1 — Sırala
Belgeleri **içerikten önce** kronolojik sıraya koy: imza tarihi, giriş bölümündeki "…tarihli sözleşmenin 2 No.lu Ek Protokolü" atıfları, dosya adı. Sıra çıkarımla kurulduysa yalnız emin olunmayan belgeyi belirt. Taraflar belgeler arasında aynı mı? Unvan değişmiş ya da yeni taraf eklenmişse işaretle (unvan değişikliği mi, sözleşmenin devri mi — devir TBK m.205 rızası ister `[doğrula]`).

### Adım 2 — Şekil süzgeci (Türk hukukuna özgü ek)
Ek protokol, ana sözleşmenin tabi olduğu **şekle** uymak zorundaysa kontrol et:
- Kefaletin sorumluluğu artıran değişikliği kefalet şekline tabi; değişikliğin türüne göre eşin yeniden rızası (TBK m.583/3, m.584/2). 
- Taşınmaz satış vaadi, arsa payı karşılığı inşaat, ölünceye kadar bakma: değişiklik de resmî şekilde mi? `[incele]`
- Yayım ve FSEK mali hak sözleşmeleri: yazılı mı, haklar ayrı ayrı mı?
- Tüketici sözleşmesi: koşulların süre içinde tüketici aleyhine değiştirilmesi yasak (6502 m.4/2). 
- Genel işlem koşulu içeren sözleşmede düzenleyene **tek yanlı** değişiklik yetkisi veren kayıt yazılmamış sayılır (TBK m.24); karşı tarafın imzası olmayan "güncellenmiş şartlar" ek protokol değildir. 

Şekle uymayan ek protokolü "geçerli son metin" diye gösterme; ikisini de yaz ve `[incele]` işaretle.

### Kip 1 çıktısı
```markdown
# Değişiklik geçmişi: [karşı taraf] — [sözleşme türü]
**Ana sözleşme:** [tarih] · **Ek protokoller:** [N] ([ilk] → [son]) · **Son değişiklik:** [tarih]

## Kronolojik değişiklikler
### Ek Protokol 1 — [tarih]
**Amaç:** [giriş bölümünden; yazmıyorsa boş bırak, tahmin etme]
- [Madde] (m.[X]): [önce → şimdi, sade dille]
- [Yeni madde] (m.[X]): …
- [Kaldırılan madde] (m.[X]): … ve neden önemli

## Bugünkü durum
| Madde | Geçerli pozisyon | Madde no | Son değişiklik |

## Dikkat
[çelişkiler, kaldırılmış maddeyi değiştiren ek, numarası kayan madde, unvan değişikliği, şekle uymayan ek — madde numaralarıyla]
```

### Kip 2 çıktısı
Yalnız maddeyi değiştiren belgeleri göster; dokunmayanları atla.
```markdown
# Madde izi: [madde adı] — [karşı taraf]
### Asıl metin — [ana sözleşme tarihi], m.[X]
> "[aynen alıntı]"   *Sade dille:* …
### Ek Protokol [N] — [tarih], m.[X]
**Önce:** > "…"  **Sonra:** > "…"  *Ne değişti:* …
## Geçerli metin — m.[X], [kaynak belge, tarih]
> "[aynen alıntı]"
## Dikkat
[sorumluluk tavanına dahil mi, numara kaydı, başka maddeyle çelişki]
```
Madde hiç değişmemişse: "Bu madde hiçbir ek protokolle değiştirilmemiş. Asıl metin geçerli: m.[X], ana sözleşme, [tarih]."

### Bu akış ne yapmaz
- Ana sözleşme ile ek arasındaki çelişkide **hangisinin üstün geldiğine karar vermez** (yorum sorusu, `[incele]`).
- Yeni ek protokol yazmaz; playbook karşılaştırması yapmaz (→ `genel-inceleme-ve-playbook.md`).
- Belirsiz dili yorumlamaz; aynen alıntılar ve işaretler.

---

## B. İş birimine sade özet

### Ne zaman kullanılır
- "Yönetime özetle", "satın almaya anlat", "hukukçu olmayan için kısa not", inceleme bitti ve hukuk dışına gidecek.
- Önce **gönderim yeri kontrolü** (ORTAK-KURALLAR.md §1): alıcı avukat-müvekkil ilişkisinin içinde mi? Değilse iç değerlendirme ile dışarı gidecek arındırılmış metni ayır; "GİZLİDİR" başlığını dış metinden kaldırmayı hatırlat.

### Kitle ayarı
| Kitle | Önemser | Önemsemez |
|---|---|---|
| Satın alma | Fiyat, yenileme, onay yolu | Sorumluluk tavanının yapısı |
| Bütçe sahibi birim | Ekip kullanabilir mi, bozulursa ne olur, maliyet | Tazmin kapsamı |
| Finans | Toplam maliyet, yenileme fiyat riski, döviz/kur riski, damga vergisi yükü | Uygulanacak hukuk |
| Bilgi işlem / güvenlik | Veri nerede, alt işleyenler, erişim, çıkış | Geri kalan her şey |
| Üst yönetim | Bizi zor durumda bırakır mı, hukuk engel mi | Ayrıntı |

Kitle belli değilse sor.

### Uzunluk sınırı (zorunlu)
- **1 paragraf:** karar ve sözleşmenin ne olduğu (iş diliyle: "pazarlama ekibinin istediği raporlama aracının sözleşmesi").
- **1 paragraf:** "sonradan şaşıracağınız şey" — yoksa "temiz sözleşme, sürpriz yok".
- **En fazla 3 maddelik** yapılacaklar listesi.
- **Tek satır** onay ve zamanlama.
- **Toplam 200 kelimenin altında.** Daha uzunsa gereksiz ayrıntı vardır; ayrıntı incelemede kalır.

### Alıntı disiplini
Bir maddeyi alıntılıyorsan **koşul cümlesinin tamamını** alıntıla; kesik alıntı istisnayı kurala çevirir. Sığmıyorsa doğru özetle ("kampanyalı fiyatlarda yenilemede liste fiyatına dönülüyor"), kesme.

### Çeviri tablosu
| Hukuki bulgu | İş dili |
|---|---|
| Sorumluluk son 12 ayın bedeliyle sınırlı | "Bir şey bozarlarsa en fazla bir yıllık ödediğimiz kadarını geri alabiliriz." |
| Belirli süreli, erken fesih hakkı yok | "İmzaladıktan sonra süre bitene kadar bağlıyız; kullanmayı bıraksak da ödemeye devam." |
| Otomatik yenileme, 60 gün önceden iptal | "Her yıl kendiliğinden yenilenir; iptal için yenilemeden iki ay önce yazmamız gerek." |
| Fikri mülkiyet tazmini yok | "Biri bu ürün yüzünden bize hak ihlali davası açarsa sağlayıcı bizi savunmak zorunda değil." |
| Alt işleyen listesi açıklanmamış | "Verimize başka hangi şirketlerin erişeceğini bilmiyoruz." |
| Sona ermede 30 gün içinde veri silinir | "İptal edersek verimizi bir ay içinde siler; ihtiyacımız olanı önceden indirmeliyiz." |
| Cezai şart, tacir olduğumuz için indirilemez | "Gecikirsek ödeyeceğimiz ceza sabit; mahkemeden indirmesini isteyemeyiz." |
| Kefalet el yazısı eksik | "Kefil gösterdiğimiz kişi, metindeki eksik nedeniyle büyük ihtimalle sorumlu tutulamaz." |
| Dövizli bedel 32 sayılı Karar'a aykırı | "Bu sözleşmede fiyatı dolarla yazamayız; TL'ye çevirmemiz gerekiyor." |

### Yazılmayacaklar
Madde numaraları, tırnak içinde tanımlı terimler, "tazmin", "işbu", "mezkûr", "müteakiben", renkli risk matrisi (kitle özellikle istemedikçe), "bu hukuki tavsiye değildir" tekrarı (başlık zaten var).

### Sorun bulunduysa
İkinci paragraf "şu [N] konuda karşı tarafa geri dönüyoruz, ana konu: [sade dille]" olur; gerçekçi beklenti ("muhtemelen kabul ederler" / "bu takılabilir"). Yapılacaklar: "Şimdilik bir şey yok, dönüş gelince haber vereceğim" ya da iş kararı ("X'te uzlaşmazlarsa Y'yi kabul eder misiniz, yoksa vazgeçelim mi?").

### Takip iddiası kuralı
"Yenileme tarihini takvime ekledim / takibe aldım" yazmadan önce bunun **gerçekten yapıldığını** doğrula; yapılmadıysa yapılacaklara "Yenileme takvime eklenmeli — henüz eklenmedi" yaz. Hiç kurulmamış bir hatırlatmaya güvenmek, hiç söylememekten kötüdür.

### Yükseltme mutabakatı
İnceleme birden çok onaylayıcı adlandırdıysa (genel müdür yardımcısı, bilgi güvenliği, finans, KVKK irtibat kişisi) özetin altına iç not ekle: "[N] onaylayıcının [M]'ine iletildi; iletilmeyenler: [ad — tek satır neden]". Bu blok 200 kelime sınırına dahil değildir ve dış metne girmez.

### Çıktı iskeleti
```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1; dışarı gidecekse kaldırılacağı notuyla]
**[Karşı taraf] [tür]** — [İMZAYA HAZIR | DEĞİŞİKLİK GEREKİYOR | ENGELLİ]

[Ne olduğu — bir paragraf]

[Sürpriz / geri döndüğümüz konu — bir paragraf]

**Sizin yapmanız gereken:**
- [ ] …

**Onay:** [kim, ne zaman]
```

---

## Görüşme soruları
1. (Geçmiş) Ana sözleşme ve tüm ek protokoller elinizde mi; imza tarihleri?
2. (Geçmiş) Özellikle izlenecek madde?
3. (Özet) Kime gidecek; bu kişi hukuk biriminin içinde mi?
4. (Özet) Hangi kanaldan (e-posta, toplantı, yazışma grubu)?

## MCP adımları
Bu akışlar çoğunlukla belge içi çalışır. Şekil süzgecinde gereken maddeleri çek:
```
legal_get_statute_article  law_no: "6098"  article_no: "24" | "205" | "583" | "584"
legal_get_statute_article  law_no: "6502"  article_no: "4"
legal_check_holiday   # yenileme/iptal son günü
```

## Sık hatalar
- Ek protokolleri dosya adına göre yanlış sıralamak.
- Şekle uymayan ek protokolü geçerli son metin diye sunmak.
- Karşı tarafın tek yanlı "güncellenmiş şartlar"ını ek protokol saymak.
- İş birimi özetinde madde numarası ve hukuk terimi kullanmak; 200 kelimeyi aşmak.
- Kesik alıntıyla istisnayı kural gibi göstermek.
- Yapılmamış takvim kaydını "yapıldı" diye yazmak.

---

