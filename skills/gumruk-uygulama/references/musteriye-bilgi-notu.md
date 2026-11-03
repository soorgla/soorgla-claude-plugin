# Müşteriye bilgi notu (ithalatçı / ihracatçı)

## Ne zaman kullanılır
- Gümrük müşavirinin müşterisine sipariş öncesi maliyet ve ön kontrol sonucu, belge listesi ya da süre uyarısı göndermesi.
- Şirket dış ticaret ekibinin yönetime/satın almaya kısa not yazması.
- Uyuşmazlık bildirimi (ek tahakkuk geldi, itiraz süresi) bu not değildir → `../../gumruk-dis-ticaret/SKILL.md`; sade dil durum mektubu → [muvekkil-iletisimi](../../muvekkil-iletisimi/SKILL.md).

---

## Kurallar

- Müşteri adını, vergi numarasını ve fatura ayrıntısını not şablonuna yazma; kullanıcı ekler.
- Rakamlar maliyet tablosundan (`gumruklenmis-maliyet.md`) gelir; tabloda olmayan rakam yazma.
- Her tutarın yanında varsayımı yaz: tescil tarihi, kur ve tarihi, menşe belgesi var/yok, ödeme şekli.
- "Kesin" deme: GTİP önerisi değerlendirmedir; oranlar tescil günü değişebilir; damping firma oranına bağlıdır.
- Teknik terimi bir kez aç: "ilave gümrük vergisi (İGV)", "kaynak kullanımını destekleme fonu (KKDF)".
- Notun altına müşavirin gözden geçirme satırı (ORTAK-KURALLAR.md §1 meslek mensubu başlığı).

---

## Şablon

```markdown
MESLEKİ ÇALIŞMA TASLAĞI — GÜMRÜK MÜŞAVİRİ İNCELEMESİ GEREKTİRİR

Konu: [eşya] ithalatı — tahmini vergi yükü ve ön kontrol
Tarih: [gg.aa.yyyy]

1. Sonuç
[Eşya] için [menşe] menşeli ithalatta, [tescil tarihi] itibarıyla tahmini vergi yükü kıymetin yaklaşık %[x]'i,
toplam [tutar] TL'dir. [Engel/izin özeti tek cümle.]

2. Varsayımlar
- GTİP: [kod] ([güven düzeyi]; bağlayıcı değildir, BTB önerimiz: [evet/hayır])
- Kıymet: [tutar döviz] × [kur] ([TCMB, tarih]) = [TL]; teslim şekli [..]
- Menşe belgesi: [var/yok] — yoksa tutar [..] TL olur
- Ödeme şekli: [..] (KKDF [var/yok])

3. Vergi tablosu
| Kalem | Tutar (TL) |
| … | … |
| Toplam | … |

4. Yapılması gerekenler
- [ ] [izin / denetim / belge] — [kim] — [son gün]

5. Dikkat
- [önlem, gözetim, süre sonu, eşleme doğrulaması]

[Gümrük müşaviri] — gözden geçirildi: [ ]
```
