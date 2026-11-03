# Portföy durumu (`portfoy`)

Kaynak: upstream `litigation-legal/portfolio-status`. Türk usulüne uyarlandı: süre pencereleri, duruşma takvimi, adli tatil uyarısı, çıkar çatışması bayrakları, Av.K. m.39 saklama süresi dolan kapalı dosyalar; ABD'ye özgü "materiality / reserve" ve "outside counsel" bayrakları çıkarıldı (şirket içi kullanıcıda karşılık bayrağı isteğe bağlı).

Amaç: tek okumada "şu an elimde ne var, neye bakmalıyım, ne kayıyor" sorusunu cevaplamak. Üç dakikada okunacak, taranabilir bir özet.

---

## 0. Kaynak ve sınır

- **Yalnız `_liste.yaml` okunur.** Dosya kartları ve günlükler açılmaz; böylece portföy özeti dosyalar arası bağlam kuralını bozmaz.
- Dizindeki bir alan eksik ya da bayatsa özet bunu söyler; eksik bilgiyi tamamlamak için karta bakmaz, `guncelle` önerir.
- Varsayılan: açık dosyalar (`durum != kapali`). Seçenekler: `--hepsi` (kapalılar dahil), `--risk=yuksek`, `--bayat`, `--alan=is-hukuku`, `--sorumlu=<ad>`.

## 1. Süre kontrolü

Bugünün tarihini al. Her açık `sureler` satırı için kalan gün sayısını hesapla. Dizindeki son günler açılışta ya da güncellemede hesaplanmıştır; portföy özeti onları yeniden hesaplamaz, ama:
- 14 gün içindeki her kanun yolu süresini `legal_calculate_deadline` ile bir kez daha kontrol et; fark varsa ikisini de yaz.
- `hesap` alanı "elle [doğrula]" olan satırları ayrı işaretle.
- Adli tatile denk gelen son günleri ayrıca işaretle (`dosya-guncelle.md` §4: `legal_check_holiday` adli tatil günlerini `tatil: true` döndürüyor; son günü kendiliğinden kaydırma, HMK m.104 kontrolü `[incele]`).

## 2. Çıktı iskeleti

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu — Okunan: yalnız _liste.yaml (N satır); dosya kartları açılmadı · Güncellik: en eski son_guncelleme AAAA-AA-GG

# Portföy — [bugün]

**Açık dosya:** [N] · **Bu yıl kapanan:** [N] *(yalnız --hepsi)*

## 🔴 Önce bunlar
[Son günü geçmiş ya da 7 gün içinde olan süreler; çıkar çatışması "yapılmadı"/atlanmış dosyalar. Yoksa bu bölüm yok.]

## Süreler
| Pencere | Dosya — süre — son gün — hesap |
|---|---|
| 0–7 gün | |
| 8–14 gün | |
| 15–30 gün | |
| 31–60 gün | |

## Duruşmalar (60 gün)
| Tarih | Dosya | Merci |
|---|---|---|

## Riske göre
| Risk | Sayı | Dosyalar |
|---|---|---|
| 🔴 engelleyici | | [kısa adlar] |
| 🟠 yüksek | | [kısa adlar] |
| 🟡 orta | | [yalnız sayı; --risk=orta ile aç] |
| 🟢 düşük | | [yalnız sayı] |

## Duruma göre
[ön hazırlık / arabuluculuk / dava / istinaf / temyiz / icra / sulh müzakeresi / beklemede — sayılar]

## ⚠️ Uyarılar
- **Kaçmış olabilir:** son günü geçmiş ama `durum: acik` süre
- **Bayat (30+ gün güncellenmemiş):** [___]
- **Çıkar çatışması bekliyor / yapılmadı:** [___]
- **Çıkar çatışması atlandı (kalıcı kayıt):** [___]
- **Yüksek/engelleyici risk, sorumlu yok:** [___]
- **Süre satırı hiç yok** (açık dosyada): [___]
- **Elle hesaplanmış, doğrulanmamış süre:** [___]
- **Saklama süresi dolan kapalı dosyalar** (`saklama_bitis < bugün`; iade/silme kararı bekliyor): [___]
- **Eksik zorunlu alan:** [kısa ad → alan]

## Kapanış notu
[Yalnız gerçekten öne çıkan bir şey varsa bir iki cümle; yoksa yazma.]
```

Gizlilik sınıfı "yüksek" ya da "çok yüksek" olan dosyalar özette yalnız kısa ad ve kodla görünür (`baslik` zaten kodludur).

## 3. Karar ağacı ve pano önerisi

ORTAK-KURALLAR.md §8 karar ağacı; örnek seçenekler: 1. 🔴 satırdaki dosyanın brifingi · 2. `sure-takibi` ile bütün süreleri yeniden hesapla · 3. Bayat dosyaları sırayla `guncelle` · 4. Bekle ve izle — [tarih] · 5. Başka bir şey.

Dosya sayısı ~10'u geçerse ya da kullanıcı isterse tek satırla **pano** öner (risk sayıları, süre zaman çizelgesi, sıralanabilir dosya tablosu). Pano yalnız `_liste.yaml`'daki alanları gösterir; paylaşılabilir bir sayfaya müvekkil adı konmadan önce sor (gizlilik).

## Bu adım ne yapmaz

- Öncelik kararı vermez; neyin dikkat istediğini gösterir.
- Dosya kartlarını açmaz.
- Büro yönetim programının ya da UYAP'ın yerine geçmez; çalışma belleğidir.
