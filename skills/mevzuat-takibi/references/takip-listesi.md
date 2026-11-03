# Takip listesi: ne izlenir, nerede tutulur, kim görür

## Ne zaman kullanılır
- İlk kurulum ("şu kanunları takip etmek istiyorum", "mevzuat izleme kur").
- Ekleme / çıkarma ("6698'i de ekle", "ihale tebliğlerini artık izleme").
- Her taramanın başında okuma (SKILL.md Adım 0).

Upstream `regulatory-legal/CLAUDE.md` "Regulators we watch", "Policy library", "Materiality threshold", "Gap response process" ve "Feed configuration" bölümlerinden uyarlandı. Upstream'de bu bilgiler pakete özel yapılandırma dosyasındadır; bizde ortak profilden ayrı, kendi dosyasındadır (profil herkes için; takip listesi yalnız bu beceriyi kullananlar için).

---

## 1. Dosya yeri

```
~/.claude/plugins/config/soorgla-hukuk/mevzuat-takibi/
├── takip-listesi.md # bu dosyanın §3 şablonu
├── bosluk-takibi.yaml # açık boşluklar (etki-ve-bosluk.md §4)
└── ozetler/
    └── mevzuat-ozeti-AAAA-AA-GG.md
```

- Üst klasörleri gerekirse oluştur. Eklenti klasörüne (`skills/…`) kullanıcı verisi yazılmaz.
- Profilde **dosya çalışma alanları etkin** ise ve takip bir müvekkil için yapılıyorsa dosyalar `~/.claude/plugins/config/soorgla-hukuk/dosyalar/<dosya-kisa-adi>/mevzuat-takibi/` altına yazılır; bir müvekkilin takip listesi başka bir müvekkilin taramasında okunmaz (ORTAK-KURALLAR.md "Büro profili" son paragraf).
- Büro geneli takip (ör. "iş hukuku ekibi 4857 ve 7036'yı izler") dosya klasörüne değil, yukarıdaki genel yola yazılır.

## 2. Gizlilik uyarısı (dosya ilk kez yazılırken kullanıcıya bir kez söyle)

> Takip listesi, boşluk tablosu ve özetler bu bilgisayarda düz metin olarak `~/.claude/plugins/config/soorgla-hukuk/mevzuat-takibi/` klasöründe tutulur. Bu dosyalara müvekkil adı, dosya numarası, sözleşme karşı tarafı ya da kişisel veri yazmanızı önermem. Avukatın sır saklama yükümlülüğü (Av.K. m.36) `[model bilgisi — doğrulayın]` ve kişisel verilerin korunması yükümlülükleri (6698 sayılı KVKK, özellikle m.12 veri güvenliği) `[model bilgisi — doğrulayın]` bu dosyalar için de geçerlidir. Müvekkil yerine kısa kod kullanın (ör. "M-014", "Tedarikçi sözleşme şablonu v3"). Klasörü bulut eşitlemesine (OneDrive, Dropbox) açık bir yerde tutuyorsanız bunu bilerek yapın.

- Kullanıcı yine de ad yazmak isterse yaz; kararı kullanıcı verir. Ama özet dosyasına ve ekrana giden "gönderilecek" sürümde adları kod ile değiştirme seçeneğini sun.
- "GİZLİDİR" başlığı koruma yaratmaz (ORTAK-KURALLAR.md §1 sır saklama notu).

## 3. Şablon

```markdown
# Mevzuat takip listesi
*Oluşturma: AAAA-AA-GG · Son güncelleme: AAAA-AA-GG*
*son_tarama: AAAA-AA-GG*

## 1. İzlenen mevzuat
| # | Mevzuat (no ve tür) | Maddeler | Neden izleniyor | Önem varsayılanı | İlgili alan becerisi |
|---|---|---|---|---|---|
| K1 | 6698 Kanun | tümü | veri sorumlusuyuz | 🔴 | kvkk |
| K2 | 4857 Kanun | 17-21, 25, 63 | işveren; fesih ve çalışma süresi | 🟠 | is-hukuku |
| K3 | Kişisel Verilerin Yurt Dışına Aktarılmasına İlişkin Usul ve Esaslar Hakkında Yönetmelik | tümü | standart sözleşme kullanıyoruz | 🔴 | kvkk |

## 2. İzlenen kurumlar (kurul kararı, tebliğ, ilke kararı)
| # | Kurum (soorgla `kurum` filtresine yazılacak tam ad) | Konu sınırı |
|---|---|---|
| R1 | Kişisel Verileri Koruma Kurulu | ilke kararı, karar özeti |
| R2 | Rekabet Kurulu | yalnız [sektör] |

## 3. Anahtar kelimeler (başlıkta aranır)
- "Ticari Reklam", "Mesafeli Sözleşmeler", "Elektronik Ticaret", …

## 4. AYM ve yüksek mahkeme
- AYM norm denetimi: [izlenen kanun numaraları — varsayılan: §1'deki bütün kanunlar]
- Yargıtay / Danıştay iş bölümü kararları: [evet / hayır]

## 5. Politika ve sözleşme dizini (boşluk analizi için; isteğe bağlı)
| # | Belge (kod ya da ad) | Dosya yolu / yer | Son onay tarihi | Sahibi (rol) | İlgili kalemler |
|---|---|---|---|---|---|
| P1 | Kişisel veri saklama ve imha politikası | [yol] | AAAA-AA-GG | Uyum sorumlusu | K1, R1 |
| P2 | Tedarikçi veri işleme sözleşmesi şablonu | [yol] | | Hukuk | K1, K3 |

## 6. Önem eşikleri (boş bırakılırsa onem-suzgeci.md varsayılanı)
- Her zaman 🔴: [ör. "izlenen kanunda süre veya ceza değişikliği", "izlenen kanunda AYM iptali"]
- 🟠 incelenecek: [ör. "izlenen kurumun ilke kararı"]
- 🟡 bilgi: [ör. "başka sektöre özgü yönetmelik"]

## 7. Süreç
- Değişiklikleri kim ilk değerlendirir: [rol]
- Politika güncellemesini kim onaylar: [rol]
- 🔴 kalemlerde yükseltme: [rol]
- Tarama sıklığı: [elle | haftalık | günlük]
- Özet çıktısı: [sohbet | sohbet + dosya]
```

Kurulumda ilk dört soruyu sor; 5-7 isteğe bağlıdır:

1. Hangi kanunları (no) ya da konuları izlemek istiyorsunuz? Belirli maddeler var mı?
2. Kararlarını izlemek istediğiniz kurul veya kurum var mı (KVKK, Rekabet, GİB, BDDK, SPK, EPDK, KİK…)?
3. Hangi değişiklik sizin için "hemen bakılmalı" sayılır?
4. Hangi sıklıkla bakalım: siz istediğinizde mi, haftalık mı?
5. (İsteğe bağlı) Karşılaştırılacak iç politika ya da sözleşme şablonlarınız var mı? Nerede duruyorlar, sahibi kim?
6. (İsteğe bağlı) Değişikliği kim değerlendirir, politikayı kim onaylar?

**Kanun numarasını çözümle:** kullanıcı adla verdiyse `legal_resolve_statute` (`query`, `law_type`) ile numara ve türü bul; numara çakışması olan kanunlarda (657, 4483, 213, 6306, 3201, 6325, 3095…) `statute_id`'yi tabloya not et, `law_type: "Kanun"` ile çağır; yanıttaki `other_candidates` aynı numaralı diğer kayıtlardır, gerekirse `legal_get_statute_article_by_id` kullan.

**Kurum adını tam yaz:** `legal_search_admin_guidance` `kurum` filtresi tam adla çalışır ("Kişisel Verileri Koruma Kurulu", "Rekabet Kurulu", "Gelir İdaresi Başkanlığı", "Reklam Kurulu", "Bankacılık Düzenleme ve Denetleme Kurulu").

## 4. Takip listesini değiştirme

- Ekleme ve çıkarmada tabloyu yeniden yaz, "Son güncelleme" tarihini değiştir. Çıkarılan kalemi silme; tablonun altına `~~K5 …~~ (çıkarıldı AAAA-AA-GG, neden)` diye bırak: geçmiş özetlerin neden o kalemi içerdiği anlaşılsın.
- Kullanıcı "şunu artık sorma" dediyse (ör. kapsam boşluğu uyarısı) bunu §6'ya not et; aynı uyarıyı her taramada tekrarlama.
- **Kapsam boşluğu uyarısı (upstream "coverage check").** Takip listesi bir alanı ima ediyor ama ilgili kurum ya da yönetmelik listede yoksa (ör. 6698 izleniyor ama KVK Kurulu ve KVKK yönetmelikleri yok; 4734 izleniyor ama Kamu İhale Genel Tebliği yok) özetin başına bir kez yaz: "**Kapsam boşluğu:** [kanun] izleniyor ama [ikincil düzenleme / kurum] listede yok. Eklensin mi?"

## 5. Dosya sistemi olmayan istemciler (claude.ai web, ChatGPT, mobil)

Dosya okunamıyor ve yazılamıyorsa:

1. Kullanıcıdan takip listesini sohbete yapıştırmasını iste ("Önceki özetin sonundaki 'takip durumu' bloğunu yapıştırabilir misiniz?"). Yoksa §3'teki sorularla sohbet içinde kur.
2. Her özetin en sonuna, kullanıcının kendi not uygulamasına kopyalayacağı şu bloğu ekle:

```text
--- TAKİP DURUMU (bir sonraki taramada bunu yapıştırın) ---
son_tarama: AAAA-AA-GG
izlenen: 6698 (tümü) | 4857 m.17-21,25,63 | Yurt Dışı Aktarım Yönetmeliği
kurumlar: Kişisel Verileri Koruma Kurulu
anahtar: "Ticari Reklam", "Elektronik Ticaret"
acik_bosluklar: B-003 (P2, son tarih AAAA-AA-GG) | B-004 (izle)
--- SON ---
```

3. Bu bloğa müvekkil adı ve kişisel veri koyma; kod kullan.
4. claude.ai'de proje bilgisi (project knowledge) kullanılıyorsa kullanıcı takip listesini oraya koyabilir; beceri onu okur ama oraya yazamaz.

---

## Kaynak
- Upstream `regulatory-legal/CLAUDE.md` (Regulators we watch, Policy library, Materiality threshold, Gap response process, Feed configuration, Matter workspaces) ve `reg-feed-watcher` "Step 0: Coverage check". ABD'ye özgü besleme ve Slack alanları çıkarıldı.
