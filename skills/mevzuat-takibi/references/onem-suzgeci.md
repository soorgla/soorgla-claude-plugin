# Önem süzgeci: hangi değişiklik hemen bakılmalı

## Ne zaman kullanılır
- Her taramadan sonra, çekilen her kalem için (SKILL.md Adım 3).
- Kullanıcı tek bir düzenleme yapıştırıp "bu önemli mi?" diye sorduğunda.

Upstream `reg-feed-watcher` "Step 2: Classify" ve `materiality-filter.yaml` uyarlamasıdır. ABD'deki "final rule / NPRM / ANPR / enforcement action" ayrımı yerine Türk normlar hiyerarşisi ve yürürlük kuralları kullanılır.

---

## 1. Dört kademe

| Kademe | Anlamı | Özette gösterim |
|---|---|---|
| 🔴 Hemen | Takip edilen bir yükümlülük, süre, oran, yaptırım ya da yetki değişti; ya da izlenen hüküm iptal edildi; yürürlük yakın veya geçmiş | Ayrı blok; madde farkı (`madde-farki.md`) ve önerilen eylemle |
| 🟠 İncelenecek | Takip listesindeki alana dokunuyor ama yükümlülüğü doğrudan değiştirmiyor ya da kapsamı belirsiz | Tabloda tek satır + neden ilgili |
| 🟡 Bilgi | İlgili alanda ama bu kullanıcıyı etkilemesi zayıf | Yalnız sayı ve başlık listesi |
| ⚪ Atla | Takip listesiyle ilgisiz (üniversite iç yönetmeliği, atama, başka sektör) | Yalnız toplam sayı |

Belirsizse yukarı yuvarla ve satıra `[incele]` koy (ORTAK-KURALLAR.md §8: geri alınabilir hatayı tercih et). Takip listesi §6'da kullanıcı eşiği varsa önce onu uygula.

## 2. Varsayılan sınıflandırma tablosu

| Kalem türü | Takip edilen kanun / kurum ile eşleşirse | Eşleşmezse |
|---|---|---|
| Kanun (madde değişikliği, yeni madde, yürürlükten kaldırma) | 🔴 süre, oran, ceza, yaptırım, dava şartı, görevli merci, yükümlülük değişikliği; 🟠 tanım ve usul değişikliği | ⚪ (torba kanunda takip edilen kanun yoksa) |
| AYM norm denetimi — **iptal** | 🔴 (iptalin yürürlük tarihi ayrıca yazılır) | 🟡 |
| AYM norm denetimi — **ret** | 🟠 (hükmün yürürlükte kaldığı teyit edildi; tartışma kapandı) | ⚪ |
| AYM bireysel başvuru ihlal kararı | 🟠 kararda takip edilen kanunun uygulanışı yapısal sorun sayıldıysa | ⚪ / 🟡 |
| Cumhurbaşkanı kararı (oran, tutar, süre belirleyen) | 🔴 | ⚪ |
| CBK (teşkilat) | 🟠 takip edilen kurumun görev ve yetkisi değiştiyse | ⚪ |
| Yönetmelik / yönetmelik değişikliği | 🔴 yükümlülük, süre, form, bildirim usulü; 🟠 diğer | ⚪ |
| Tebliğ (uygulama tebliği, genel tebliğ) | 🔴 parasal sınır, eşik, oran, süre; 🟠 usul | ⚪ |
| Kurul kararı (ilke kararı, düzenleyici karar) | 🔴 ilke kararı ve düzenleyici işlem; 🟠 tekil yaptırım kararı | ⚪ |
| Kurul karar özeti (tekil olay) | 🟠 yeni bir yorum ya da yüksek ceza içeriyorsa; aksi 🟡 | ⚪ |
| Yargıtay BGK iş bölümü / İBK, Danıştay İBK | 🟠 (açık dosyalarda merci ve emsal araması değişir) | 🟡 |
| İkincil kaynak (haber, büro bülteni, sosyal medya) | En fazla 🟠 — RG'deki asıl metin bulunana kadar | — |

**İkincil kaynak kuralı** (upstream "Secondary sources"): kullanıcının yapıştırdığı haber ya da bülten "X yürürlüğe girdi" diyorsa onu RG'de bul. Bulamazsan kalem 🟠 kalır ve satıra "→ Asıl kaynağı RG'de bulun; bulunamadı `[ikincil kaynak — doğrulayın]`" yazılır.

## 3. 🔴'yi tetikleyen içerik sinyalleri (metni okurken ara)

- **Süre:** "… gün içinde", "… iş günü", "süresi … olarak", "hak düşürücü", "zamanaşımı". Süre kısaldıysa açık dosyaların takvimi etkilenir: alan becerisine ve ilgili dilekçe becerisine devret.
- **Parasal sınır ve oran:** "… Türk lirası", "oranı", "katı", "yeniden değerleme". Tutarı özete yazma; "tutar değişti — güncel değer için `legal_get_social_parameters` / ilgili alan becerisi" de. Beceri metnine ve takip listesine tutar yazılmaz.
- **Yaptırım:** "idari para cezası", "hapis", "adli para cezası", "kapatma", "faaliyetten men".
- **Yeni yükümlülük:** "zorundadır", "yükümlüdür", "bildirir", "kaydolur", "… yapmayanlar".
- **Merci ve usul:** "görevli mahkeme", "dava şartı", "arabuluculuk", "itiraz … mercii".
- **Yürürlükten kaldırma:** "yürürlükten kaldırılmıştır", "mülga". soorgla mülga maddeyi `status: "mulga_veya_iptal"` ve uyarıyla döndürür; ama çok yeni bir kaldırma henüz işlenmemiş olabilir: değişikliğin kaydını takip listesinin altına not et ki alan becerileri eski metni alıntılamasın.

## 4. Yürürlük tarihi ve geçiş hükmü (her 🔴/🟠 kalemde zorunlu)

1. Değiştiren düzenlemenin **yürürlük maddesini** oku. Yayım tarihi ≠ yürürlük tarihi. Sık kalıplar: "yayımı tarihinde", "yayımını izleyen ayın başında", "… tarihinde", "… tarihinden itibaren … dönemlerine uygulanmak üzere", maddeden maddeye farklı tarihler.
2. **Geçiş hükmünü** (geçici madde) oku: hangi dosya ve işlemler eski metne tabi kalıyor?
3. Yürürlük tarihi takvimde bir tatile denk geliyor ve bir süre başlatıyorsa `legal_check_holiday` ile kontrol et; süre hesabını kendin yapma, alan becerisine bırak. 
4. Özette üç tarih ayrı sütunda durur: **yayım**, **yürürlük**, **ilk uygulama / geçiş sonu**.
5. Yürürlüğü 30 günden kısa sürede başlayacak ya da başlamış bir 🔴 kalem özetin en üstüne "Bu hafta / bu ay yürürlüğe girenler" bloğuna çıkar.

## 5. AYM iptal kararlarında ayrıca

- **Ertelenmiş yürürlük:** AYM iptal kararının "Resmî Gazete'de yayımlanmasından başlayarak … ay sonra yürürlüğe girmesine" hükmü olabilir. O tarihe kadar hüküm uygulanır; o tarihte yasama boşluğu doğar. Özete her iki tarihi yaz ve boşluk tablosuna `izle` türünde kayıt aç (`etki-ve-bosluk.md` §4). `[model bilgisi — doğrulayın]` (bu kalıp bu turda bir karar metninde okunmadı)
- **Kısmi iptal:** çoğunlukla bir ibare ya da cümle iptal edilir; hangi ibarenin gittiğini alıntıla. Madde metninin araçtaki güncel hâli iptali henüz yansıtmıyor olabilir: AYM iptalleri soorgla sürüm kaydında "Anayasa Mahkemesi" kaynaklı sürüm olarak görünür ama kayıtlar 2014-2015'te kalıyor (`madde-farki.md` §3).
- **Ret kararı:** "iptal talebinin reddi" de bilgidir: hükmün Anayasa'ya uygun bulunduğu ve yürürlükte kaldığı teyit edilmiştir.
- **Karşı oy:** sonuç değildir (`rg-tarama.md` §5).

## 6. Henüz yürürlükte olmayan metin

Kullanıcı TBMM'deki bir kanun teklifini, kurumun görüşe açtığı bir taslak yönetmeliği ya da "yakında çıkacak" bir düzenlemeyi getirirse:
- Kademe en fazla 🟠; satıra "TASLAK — yürürlükte değil; metin değişebilir" yaz.
- Madde farkı yerine **ön konumlanma notu** yaz (upstream `policy-diff` "Pre-rule branch"): yürürlüğe girerse hangi politika ve sözleşmeler değişmek zorunda kalır, tek paragraf. Satır satır "boşluk yok" tablosu üretme.
- Boşluk tablosuna `izle` türünde kayıt aç; `son_tarih` yerine yeniden bakılacak tarih yaz.
- Kurum taslağa görüş topluyorsa görüş son tarihini `izle` kaydına not et; görüş metni yazmak istenirse `idari-ve-kurum-basvurulari` becerisine devret.

## 7. Sınıflandırma gerekçesi

Her 🔴 ve 🟠 kalem için tek satır gerekçe yaz: "K1 (6698) — m.X'te bildirim süresi değişti → 🔴". Gerekçesiz kademe, okuyucunun süzgeci denetlemesini imkânsız kılar. Süzgeci kullanıcı değiştirmek isterse takip listesi §6'ya yaz; bu beceri eşiği kendiliğinden değiştirmez.

---

## Kaynak
- Upstream `reg-feed-watcher` Step 2-3 ("Classify", "ANPR / RFI handling", "Enrich"), `policy-diff` Step 0 ("Verify rule status before you diff") ve "Pre-rule branch", `managed-agent-cookbooks/reg-monitor/subagents/materiality-filter.yaml`. ABD'ye özgü NPRM yorum süresi ve "stay/injunction" kavramları AYM iptali, ertelenmiş yürürlük ve Danıştay yürütmeyi durdurma kararlarıyla değiştirildi.
