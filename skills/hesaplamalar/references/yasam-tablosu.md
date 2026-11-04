# Bakiye ömür (yaşam beklentisi)

Araç: `legal_get_life_expectancy` (`cinsiyet`: `erkek` | `kadin`, `yas`: tam sayı).

## Çıktı

| Alan | Anlamı |
|---|---|
| `yasam_beklentisi` | Bu yaştaki kişinin beklenen kalan ömrü (yıl, ondalıklı) |
| `yasayan_sayisi` | Tablonun yaşayan sayısı sütunu (l_x) |
| `olum_olasiligi` | O yaşta ölüm olasılığı (q_x) |

## Sınırlar

1. **Tablo adı dönmez.** Değerler TRH-2010 ile örtüşüyor (`tazminat-haksiz-fiil` bulgusu); çıktıda "TRH-2010 olduğu varsayıldı `[doğrula]`" yaz. PMF-1931 araçta yok.
2. **Üst yaş sınırı:** parametre 120'ye izin veriyor ama 100 ve üstü boş döndü. Boş sonuçta değer uydurma.
3. **Tam yaş:** ay/gün kesri yok. Kaza/ölüm tarihindeki yaşı tam yıl olarak gir, kesri nasıl ele aldığını yaz `[incele]`.
4. **Aktüerya hesabı yapmaz.** İskonto, progresif rant, aktif/pasif dönem ayrımı, destek payları, gelir artışı bu araçta yok. Bakiye ömür yalnız **bir girdi**dir.
5. Hangi tablonun, hangi yöntemin (progresif rant / teknik faiz) uygulanacağı Yargıtay uygulamasına bağlıdır ve **alan becerisindedir**: `tazminat-haksiz-fiil/references/bedensel-zarar-ve-destek-hesabi.md` (trafik, haksız fiil), iş kazası için `sosyal-guvenlik-sgk`. Orada eski %1,8 teknik faiz yönteminin bozma sebebi olduğu not edilmiştir.
6. Destekten yoksun kalmada destek ile destek görenin bakiye ömürleri ayrı ayrı çekilir; hangisinin kısa olanı sınırladığı alan becerisinde.

## Tablo

| Kişi | Cinsiyet | Olay tarihindeki yaş | `yasam_beklentisi` | Tablo | Kaynak |
|---|---|---|---|---|---|
| Destek | … | … | … | TRH-2010 varsayımı `[doğrula]` | [soorgla] `legal_get_life_expectancy` |
| Destek gören | … | … | … | | |

## Teyit eşiği

Bakiye ömür bir tazminat hesabına girdiyse her zaman 🟠 **aktüer bilirkişi teyidi gerekir**; bu beceri tazminat tutarı üretmez.

## Örnek çağrı

```
legal_get_life_expectancy  cinsiyet: "erkek"  yas: 35
```
