# TÜFE değişimi ve on iki aylık ortalama

Araç: `legal_calculate_cpi_change` (`baslangic`, `bitis`, `YYYY-AA-GG`). Tek bir `degisim_yuzdesi` döndürür (iki ondalık); endeks değerini ve hangi ayın kullanıldığını vermez.

## Aracın davranışı (ölçüldü)

| Gözlem | Sınama |
|---|---|
| **Ay düzeyinde çalışır**, gün yok sayılır: 01.09.2025→01.09.2026 ile 30.09.2025→30.09.2026 aynı sonuç (%29,73) |  |
| Başlangıç ve bitiş **ayının endeksi** karşılaştırılır: 2024-10 → 2024-11 = %2,24 (Kasım 2024 aylık değişimi) |  |
| Henüz yayımlanmamış ay için `null` (31.10.2026'da Ekim 2026 → `null`; Eylül 2026 son veri) |  |
| Seri başı: 2003-01 ve 2005-01 başlangıçlı çağrılar `null` döndü; serinin hangi aydan başladığı belli değil |  |

`null` sonucunu "değişim yok" diye okuma; ay yayımlanmamış ya da seride yok demektir.

## Noktadan noktaya değişim (araç doğrudan verir)

Kullanım: alacak güncelleme, nafaka artışı, sözleşmede "TÜFE oranında artış" (on iki aylık ortalama şartı yoksa), ecrimisil güncellemesi.

```
Güncel tutar = Tutar × (1 + degisim_yuzdesi / 100)
```

Hangi ayların kullanılacağı (ör. "yıllık TÜFE" = son yayımlanan ayın bir yıl önceki aya göre değişimi) sözleşme ya da alan kuralına bağlıdır → alan becerisi belirler, tabloda başlangıç ve bitiş ayını yaz.

## On iki aylık ortalamaya göre değişim (TBK m.344) — araçta kip yok, geçici yol

TBK m.344 kira artış sınırını **"tüketici fiyat endeksindeki oniki aylık ortalamalara göre değişim oranı"** olarak koyar. [Türk Borçlar Kanunu m. 344](https://soorgla.com/mevzuat/6098-turk-borclar-kanunu/) [soorgla]  Araç bu kipi vermez. Ama aracın aynı **sabit taban ayına** göre değişimleri endeks oranı yerine geçtiği için ortalama hesaplanabilir:

```
Taban ay B seç (ör. hedef aydan 23 ay önce).
Her ay m için:  E(m) = 100 + legal_calculate_cpi_change(B, m)      [B ayı için E = 100]
Son 12 ay ortalaması   Ā1 = (E(m-11) + … + E(m)) / 12
Önceki 12 ay ortalaması Ā0 = (E(m-23) + … + E(m-12)) / 12
On iki aylık ortalamalara göre değişim (%) = (Ā1 / Ā0 − 1) × 100
```

Bu 23 araç çağrısı ister (taban ayın kendisi 100). Çağrıları paralel yap.

**Sınama (Eylül 2026, taban Ekim 2024):** önceki 12 ay (Eki 2024–Eyl 2025) E değerleri 100; 102,24; 103,30; 108,49; 110,96; 113,69; 117,10; 118,89; 120,52; 123,00; 125,50; 129,56 → Ā0 = 114,4375. Son 12 ay (Eki 2025–Eyl 2026) 132,87; 134,02; 135,21; 141,75; 145,95; 148,78; 155,01; 157,66; 159,22; 162,05; 165,04; 168,08 → Ā1 = 150,47. Sonuç ≈ **%31,49**.  Kontrol: aynı serinin 2025-09→2026-09 noktadan noktaya değeri 168,08/129,56 = %29,73 ve araç doğrudan %29,73 verdi.

Kurallar:
- Sonuç **yaklaşıktır** (her ara değer iki ondalığa yuvarlanmış geliyor; birikmiş hata birkaç yüzde puanın yüzde biri düzeyinde). Çıktıda `[doğrula — TÜİK "12 aylık ortalamalara göre değişim", AAAA/AA bülteni]` etiketiyle ver; kullanıcı TÜİK değerini verirse onu kullan ve ikisini yan yana yaz.
- **Hangi ayın** on iki aylık ortalamasının uygulanacağı (kira yılının başladığı aydan önceki ay mı) hukuki değerlendirmedir → `kira-hukuku/references/kira-bedeli-artis-ve-tespit.md`; orada `[doğrula]` notu açık.
- Konut kirasında geçici sınır, beş yıl kuralı, yabancı para kirası gibi konular `kira-hukuku`'ndadır; bu dosya yalnız oranı hesaplar.
- Kısa yol: 23 çağrı istemiyorsan kullanıcıdan TÜİK bülten değerini iste; aracı yalnız karşılaştırma için kullan.

## Araçta olmayan endeksler

| Endeks | Kim ister | Geçici yol |
|---|---|---|
| Yİ-ÜFE ve alt endeksleri (fiyat farkı, ecrimisil) | `hakedis`, `gayrimenkul-insaat` | Fiyat farkında `legal_calculate_tender` endeksleri kendisi okur; ecrimisilde kullanıcıdan TÜİK değeri, `[doğrula]` |
| TÜFE aylık endeks değeri (ör. 2003=100 tablosu) | Bilirkişi raporu kontrolü | Araç yalnız oran verir; taban-ay yöntemi oranları verir, mutlak endeks yok |
| Memur maaş katsayısı, YDO (yeniden değerleme oranı) | Vergi, harç, kesinlik sınırı güncellemesi | `legal_get_social_parameters` açıklamalarında YDO geçebilir (ör. kesinlik sınırı kaleminde "YDO %25,49"); ayrı kalem yok |

## Teyit eşiği

On iki aylık ortalama geçici yolu, birden fazla yıllık artış zinciri, kira tespit davası değeri ya da TÜFE güncellemesinin dava değeri olarak kullanılması → 🟠 bilirkişi teyidi.

## Örnek çağrılar

```
legal_calculate_cpi_change  baslangic: "2025-09-01"  bitis: "2026-09-01"     # noktadan noktaya yıllık
legal_calculate_cpi_change  baslangic: "2024-10-01"  bitis: "2025-03-01"     # taban-ay yönteminin bir adımı
```
