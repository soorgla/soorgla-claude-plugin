# Sözleşme değişiklik izi ve kritik tarih takvimi

<!-- Uyarlama: anthropics/claude-for-legal (Apache 2.0) commercial-legal amendment-history (sözleşmenin değişiklikler boyunca izlenmesi) ve renewal-tracker (süre penceresi kapanmadan uyarı, aciliyet bantları) becerilerinden Türk kamu ihale sözleşmelerine uyarlanmıştır. -->

## Ne zaman kullanılır
- Uzun süren bir yapım işinde onlarca olur, tutanak ve yazışma birikti; "sözleşme bugün ne diyor?", "süre şimdi ne zaman bitiyor?", "hangi iş artışları toplamı ne?" soruları.
- Yüklenici ya da idare kaçırılmaması gereken bildirim ve itiraz sürelerinin takvimini istiyor.
- Bir uyuşmazlık ya da Sayıştay sorgusu öncesi olayların kronolojisi gerekiyor.

---

## 1. Değişiklik izi (iki kip)

**Kip 1 — Özet:** temel sözleşme + bütün olurlar/tutanaklar kronolojik okunur; her birinin neyi değiştirdiği tek tabloda.

**Kip 2 — Tek konu izi:** belirli bir konunun (iş bitim tarihi, sözleşme bedeli + artış, bir pozun fiyatı, iş programı) her belgede nasıl değiştiği ve bugün geçerli değeri.

Kamu ihale sözleşmesinde "değişiklik" yalnız 4735'in izin verdiği yollarla olur (m.4: kanundaki hâller dışında sözleşme değiştirilemez, ek sözleşme yapılamaz; m.15: yer ve süreden önce bitirme; m.24: iş artışı/eksilişi; m.10: mücbir sebeple süre uzatımı; Genel Şartname: idare kaynaklı süre uzatımı, proje değişikliği, YBF). Bu yolların dışında kalan bir "zeyilname" görürsen 🔴 işaretle.

| # | Belge (tür, tarih, sayı) | Değiştirdiği konu | Önceki değer | Yeni değer | Kanuni dayanak | Yetkili onay | İşaret |
|---|---|---|---|---|---|---|---|
| 0 | Sözleşme | — | — | Bedel, süre, tür | 4735 m.6-7 | — | |
| 1 | Süre uzatımı kararı | İş bitim tarihi | … | … | 4735 m.10 / Genel Şartname | İhale yetkilisi | |
| 2 | İş artışı oluru | Bedel (+%…) | … | … | 4735 m.24 | İhale yetkilisi | |
| 3 | YBF tutanağı | Poz … fiyatı | yok | … | Genel Şartname m.22 | İdare onayı | |
| 4 | Revize iş programı | Aylık ödenek dağılımı | … | … | Esaslar m.7/4 | İdare | |

Kümülatif sütunlar ekle: toplam iş artışı oranı (ilk sözleşme bedeline göre), toplam süre uzatımı (gün), güncel bitim tarihi.

---

## 2. Kritik tarih takvimi

Aciliyet bantları (yarı açık aralık, her tarih tek banda düşer): 🔴 0–13 gün, 🟠 14–44 gün, 🟡 45–89 gün; geçmiş tarihler ayrı "kaçırılmış" listesinde.

| Olay | Süre | Dayanak | Hesap başlangıcı |
|---|---|---|---|
| Mücbir sebep bildirimi | 20 gün | 4735 m.10 | Mücbir sebebin meydana gelmesi |
| Fesih ihtarındaki süre | ≥ 10 gün | 4735 m.20/a | İhtarın tebliği |
| Fesih kararı / bildirimi | 7 gün / 5 gün | 4735 m.22 | Feshedilmiş sayılma / karar |
| Proje değişikliğine görüş | 15 gün | Genel Şartname m.12/6 (1.9.2025 sonrası) | Tebliğ |
| YBF tespiti | 30 gün, imalattan önce | Genel Şartname m.22/6 | Proje değişikliği onayı |
| YBF anlaşmazlığının YFK'ya intikali (idare) | 10 gün | Genel Şartname m.22/6 | Anlaşmazlık tutanağı |
| Teknik personel bildirimi / idare cevabı | 10 gün / 10 gün | Genel Şartname m.19/6 | Onaylı iş programının tebliği |
| Geçici hakediş düzenlenmesi | Ayın ilk 5 işgünü | Genel Şartname m.39/4-a | — |
| Hakediş onay / tahakkuk / ödeme | 30 / 30 / 15 gün | Tip Sözleşme 11.2 | Hakedişin verilmesi |
| Hakedişe itiraz | Kesin hesap teslimine kadar (yeni metin); eski metinde ödemeden 10 gün | Genel Şartname m.39/4-e | `hakedis-denetimi.md` §3 |
| Kesin hesap değişikliğine itiraz | 15 gün | Genel Şartname m.40/9 | Tebliğ |
| YFK'ya itiraz | Kesin kabul tamamlanıncaya kadar | 4735 ek m.2 | — |
| Geçici kabul komisyonunun işyerine gitmesi | 10 gün | Muayene ve Kabul Yön. m.4 | Komisyonun kurulması |
| Kesin kabul komisyonu | 10 gün | Muayene ve Kabul Yön. m.10/3 | Kesin kabul teklif belgesi |
| Kesin teminatın talep edilmesi | 2 yıl | 4735 m.14 | Kesin hesap ve kesin kabul onayı |
| Yüklenicinin yapı sorumluluğu | 15 yıl | 4735 m.30 | Kesin kabul onayı |
| Alacak zamanaşımı | 5 yıl (`[incele]` başlangıç) | TBK m.147/6 | `uyusmazlik-ve-yargi-yolu.md` §4 |
| Sayıştay sorgusuna savunma | 30 gün | 6085 m.48/1 | Tebliğ |

Dayanakların DOGRULANDI künyeleri ilgili referans dosyalarındadır. Her son günü `legal_check_holiday` ile kontrol et; `legal_calculate_deadline` Genel Şartname sürelerini tanımaz; 4735 m.20/a ihtarı ve m.10 mücbir sebep bildirimi için canlıda `kik_4735_default_notice` ve `kik_4735_force_majeure_notice` var. Madde numaraları Genel Şartname yerel metniyle (örnek ihale 2026/1776751 CD) karşılaştırıldı: m.6, 11, 12, 19, 21, 22, 29, 39, 40, 47 başlıkları tutuyor. Sonuç `[doğrula]`.

**Takvim kaydı (isteğe bağlı):** kullanıcı isterse takvimi `~/.claude/plugins/config/soorgla-hukuk/dosyalar/<dosya-kisa-adi>/hakedis-takvimi.md` dosyasına yaz (dosya çalışma alanları etkinse; ORTAK-KURALLAR.md profil bölümü). Başka dosyanın takvimini okuma.

---

## 3. Görüşme soruları
- Bütün olur, tutanak, revize iş programı ve süre uzatımı kararlarının listesi (tarih, sayı)?
- Hangi konunun izini istiyorsunuz (süre, bedel, poz fiyatı, iş programı)?
- Takvim hangi tarihten itibaren ve kaç günlük pencere için?

## 4. MCP adımları
```
legal_get_statute_article law_no: "4735" law_type: "Kanun" article_no: "4" | "10" | "15" | "24"
legal_check_holiday … # her son gün için
```

## 5. Çıktı iskeleti
```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …
## [İşin adı] — değişiklik izi ve takvim — [tarih]
### Güncel durum
| Güncel bitim tarihi | Toplam süre uzatımı | Toplam iş artışı (%) | Kalan kanuni sınır | YBF sayısı |
### Değişiklik tablosu
[§1 tablosu]
### Takvim
#### 🔴 0–13 gün
#### 🟠 14–44 gün
#### 🟡 45–89 gün
#### Kaçırılmış
### Önerilen aksiyonlar
[kime, ne zamana kadar]
```

## 6. Sık hatalar
- Süre uzatımlarını toplarken mükerrer saymak (aynı dönem için iki gerekçe).
- İş artışı oranını güncel (fiyat farklı) bedel üzerinden toplamak.
- Kanunda olmayan bir "zeyilname" ile yapılan değişikliği geçerli saymak.

## Kaynak
- Upstream: commercial-legal `amendment-history`, `renewal-tracker` (Apache 2.0).
- YAML karşılığı yok; `bureaucrat/procurement_tender/procurement_4735.yaml`'daki "iş artış/eksiliş, süre uzatımı" konuları takvime çevrildi.
