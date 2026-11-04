# Dış ticaret ve gümrük mevzuatı değişiklik takibi

## Ne zaman kullanılır
- "Bu hafta RG'de bizi etkileyen bir şey çıktı mı?" (yeni ilave gümrük vergisi, damping tebliği, İthalat Rejimi Kararı değişikliği).
- "Şu değişiklik bizim ürünü etkiler mi?"
- Dosyadaki olay tarihinde hangi metnin yürürlükte olduğu.

Upstream `regulatory-legal/reg-feed-watcher` uyarlamasıdır: **değer süzgeçtedir**; süzülmemiş liste gürültüdür. Kullanıcının izleme listesi (GTİP'ler, menşe ülkeler, rejimler) yoksa önce sor.

---

## İzleme kaynakları (soorgla)

| Kaynak | Çağrı | Not |
|---|---|---|
| İthalat Rejimi Kararı değişiklikleri (vergi oranları, İGV) | `legal_search_official_gazette query: "İthalat Rejimi Kararı" search_in: "title" sort_by: "date_desc"` | 2026'da 11147, 11206, 11485, 11506, 11563, 11644 sayılı kararlar  PDF'ler; içerik için `legal_get_official_gazette_document` |
| Damping ve sübvansiyon önlemleri | `query: "İthalatta Haksız Rekabetin Önlenmesine İlişkin Tebliğ" search_in: "title"` | 2025-06'dan beri 70 tebliğ  |
| Dahilde işleme | `query: "Dahilde İşleme Rejimi" search_in: "title"` | Tebliğ 2006/12 değişiklikleri (2026/2, RG 17.04.2026)  |
| Gümrük Yönetmeliği ve Uzlaşma Yönetmeliği | `query: "Gümrük Yönetmeliğinde Değişiklik" search_in: "title"` | 09.01.2024, 20.04.2024, 15.01.2025, 22.08.2025; Uzlaşma 18.06.2026  |
| 4458'i değiştiren kanunlar | `query: "\"4458 sayılı Gümrük Kanununun\"" document_type: "kanun"` | 2022-06'dan beri: 7420 (2022), 7451 (2023); 4458 Uygulama Kararı değişikliği CB Kararı 8362 (RG 20.04.2024)  |
| Tercihli menşe yönetmelikleri | `query: "Tercihli Menşeinin Tespiti Hakkında Yönetmelik" search_in: "title"` | ör. Maldivler (RG 24.08.2026) |
| AYM iptalleri | `legal_search_cases mahkeme: "anayasa" sorgu: "Gümrük Kanunu"` | E.2023/165 K.2025/165 (m.216/1); E.2025/136 K.2025/200 (m.227/1-d, sonucu `[doğrula]`) |

Gümrük genelgeleri `legal_search_admin_guidance` `kurum: "Ticaret Bakanlığı"` `belge_tur: "genelge"` ile aranır (haftalık güncellenir); Bakanlık duyuruları ve BTB kararları için web araması `[web araması — doğrulayın]`. 

---

## Son 2-3 yılın önemli değişiklikleri (beceriye işlendi)

| Düzenleme | Etki | Dosya |
|---|---|---|
| 7333 (RG 28.07.2021) m.13 → 4458 m.211/1 | Ticaret politikası önlemine tabi eşyada kendi beyanıyla artırılan kıymetin vergisi geri verilmez | `gumruk-kiymeti-ve-geri-verme.md`  |
| 7420 (RG 09.11.2022) → 4458 m.241/6-e, geçici m.11 | Yabancı plakalı taşıtın bilgi verilmeden taşıtsız çıkışı | `gumruk-rejimleri-ve-serbest-bolge.md`  |
| 7451 (RG 10.04.2023) → 4458 m.216 | Geri vermede tecil faizi yerine kanuni faiz; uygulama süresi 3 → 4 ay | `gumruk-kiymeti-ve-geri-verme.md`  |
| CB Kararı 8362 (RG 20.04.2024, 32523) | 4458 Uygulama Kararı m.62/1-a (tarife pozisyonu), m.67 (kurum/savunma sanayii muafiyeti yeniden yazıldı), m.104/2-a (elektrikli otomobil ibaresi), m.122/2 (1/1/2025'te yürürlük), m.126/1-b (posta/hızlı kargo — "bir gerçek kişiye gelen") | `ihracat-kambiyo-ve-e-ihracat.md`  |
| CB Kararı 10813 (RG 07.01.2026, 33130) | 4458 Uygulama Kararı m.62/1 (posta/hızlı kargoyla reçeteye dayalı ilaç ve takviye edici gıdada tek ve maktu vergi) yeniden yazıldı; m.126/1-b'den bir alt sınır ibaresi kaldırıldı; yayımdan 30 gün sonra yürürlük | `ihracat-kambiyo-ve-e-ihracat.md`  |
| 7555 (RG 24.07.2025) → 1567 m.1, 3, 4 | Kambiyo fiilleri kabahat; izinsiz kıymet çıkarma/sokmaya idari para cezası | `ihracat-kambiyo-ve-e-ihracat.md`  |
| AYM E.2023/165 K.2025/165 (RG 31.12.2025, 9 ay sonra yürürlük) | 4458 m.216/1 iptal (geri vermede faiz) | `gumruk-kiymeti-ve-geri-verme.md`  |
| AYM E.2025/136 K.2025/200 (RG 24.12.2025) | 4458 m.227/1-d "...gibi yüz kızartıcı suçlar..." ibaresi **iptal edildi** (oybirliği, yürürlük ertelemesi yok); bentte tek tek sayılan suçlar yürürlükte (gümrük müşavir yardımcılığı şartı) | Meslek izni → idare-davalari-imar  |
| Gümrük Yönetmeliği (RG 22.08.2025) | Antrepo yatırım izni şartları, sayı sınırlaması, fiyat tarifesi | `gumruk-rejimleri-ve-serbest-bolge.md`  |
| Gümrük Uzlaşma Yönetmeliği (RG 18.06.2026) | Komisyon yetki sınırı artırıldı, geçici m.4 | `ek-tahakkuk-ve-yol-secimi.md`  |
| Dahilde İşleme Rejimi Kararı 10211 (RG 16.08.2025), Tebliğ 2026/2 (RG 17.04.2026) | Karar 10211: yurt içi alımın belge süresi içinde yapılması (m.5/6), ek sürelerin tebliğle belirlenmesi (m.10/4), m.22'ye yeni tahsil hâli, Bakanlığa sektörel risk değerlendirmesiyle teminat oranı/türü ve geri ödeme sistemine yönlendirme yetkisi (m.26); lehe hükümler kapatılmamış belgelere de uygulanır (geçici m.1). Tebliğ 2026/2: Tebliğ geçici m.37'ye fıkra 6-7 — kapatılmamış belgelere 6 ay içinde başvuru şartıyla orijinal sürenin yarısı kadar ilave süre (üst sınırlar fıkrada) | `gumruk-rejimleri-ve-serbest-bolge.md`  |
| 7582 (RG 04.06.2026) → 5520 m.10/1-i | Yurt dışından alınıp Türkiye'ye getirilmeden satılan mallara ilişkin kazanç indirimi değişikliği (transit ticaret) | Vergi yönü → `../../vergi/SKILL.md`; 7582 m.7 ayrıca nitelikli hizmet merkezi kazanç indirimini (m.10/1-j) ekledi; indirim oranlarını maddeden oku  |

7589 ve 7590'da gümrüğe doğrudan dokunan hüküm bulunamadı (4458'i değiştiren kanun aramasında yoklar).  7589'un yasal faiz (3095) değişikliği m.216/2'deki "kanuni faiz" hesabını etkiler `[doğrula]` (vergi ve sozlesme-incelemesi-tbk becerilerinin ortak notu; `legal_get_legal_interest_rates` 7589 sonrası yanlış oran veriyor).

---

## İş akışı

1. **İzleme listesini kur/oku:** GTİP'ler (ilk 4-6 hane yeterli), menşe ülkeler, kullanılan rejimler (DİİB, geçici ithalat), ihracat pazarları.
2. **Çek:** yukarıdaki çağrılar, `date_from` = son kontrol tarihi.
3. **Süz (önem):** 🔴 izlenen GTİP/ülkeye yeni önlem ya da oran artışı, yürürlük ≤ 30 gün; 🟠 izlenen rejimde usul değişikliği; 🟡 ilgili ama doğrudan etkisiz; 🟢 bilgi.
4. **Raporla:** yalnız 🔴/🟠'yi ayrıntılı; diğerlerini tek satır.
5. **Geçiş hükmü:** beyanname tescil tarihi esas (m.181/1); yayım ve yürürlük tarihlerini ayrı yaz.

---

## Çıktı iskeleti

```markdown
## Dış ticaret mevzuatı özeti — [son kontrol] → [bugün]
| Önem | Düzenleme (RG künyesi) | Kimi etkiler (GTİP/ülke/rejim) | Yürürlük | Yapılacak |
### Kapsam boşluğu: [izleme listesinde olup kaynakta karşılığı olmayan]
```

---

## Sık hatalar

- 🔴 Yayım tarihini yürürlük tarihi sanmak (önlem tebliğlerinde ayrı olabilir).
- 🟠 İthalat Rejimi Kararı'nın yıllık ana metnini görüp yıl içi değişiklikleri kaçırmak.
- 🟡 Süzmeden her RG kaydını raporlamak.

---

