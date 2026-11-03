# Etki ve boşluk: değişiklik iç politikayı ve sözleşmeleri nasıl etkiler

## Ne zaman kullanılır
- 🔴/🟠 bir değişiklikten sonra "politikamızı / sözleşme şablonumuzu / prosedürümüzü etkiler mi?" (SKILL.md Adım 5).
- "Açık boşluklar ne?", "B-003'ü kapat", "bunu risk kabul edelim".
- "Politikayı buna göre güncelle" (değişiklik önerisi).

Upstream `policy-diff`, `gap-surfacer`, `gaps` ve `policy-redraft` uyarlamasıdır. Slack bildirimi ve otomatik hatırlatma çıkarıldı; boşluk tablosu düz YAML dosyasıdır.

---

## 1. Yükümlülükleri tek tek yaz

Madde farkından (`madde-farki.md`) yeni ya da değişen her yükümlülüğü ayrı satır yap:

| # | Yükümlülük | Dayanak | Yürürlük | Kimi bağlar |
|---|---|---|---|---|
| Y1 | [kim, neyi, ne zaman, hangi biçimde yapar] | [kanun m./fıkra] [soorgla] | [tarih] | [veri sorumlusu / işveren / ihaleye katılan…] |

Somut yaz. "Bildirim yükümlülükleri artırıldı" yükümlülük değildir; "veri sorumlusu, standart sözleşmeyi imzalamasından itibaren beş iş günü içinde Kuruma bildirir" yükümlülüktür.

Metin kısmi ya da belirsizse dur ve sor (upstream "No silent supplement"): "Elimde [şu] var; yükümlülüğü doğru çıkarmak için [şu] gerekir. Seçenekler: (1) tam metni yapıştırın, (2) RG'den okuyayım, (3) web araması `[web araması — doğrulayın]`, (4) burada durayım."

Kurala bağlı olmayan kişiyi kapsam dışı bırakmadan önce kapsam maddesini (tanımlar, istisnalar) oku; "bizi bağlamaz" sonucu bir takdir kararıdır → `[incele]`.

## 2. Politikalarla eşleştir

Takip listesi §5'teki dizinden her yükümlülük için en yakın belgeyi bul:
- **Doğrudan:** belge bu konuyu açıkça düzenliyor.
- **Dolaylı:** belge yakın bir konuyu düzenliyor; bu yeni bir alt başlık.
- **Karşılığı yok:** hiçbir belge düzenlemiyor → "yeni belge gerekli" boşluğu.

Dizin boşsa her yükümlülüğü "karşılığı yok" say ve sona ekle: "Takip listesinde politika dizini yok; bu yüzden her yükümlülük yeni belge boşluğu olarak işaretlendi. Bu konuları düzenleyen belgeleriniz varsa dizine ekleyin ve analizi yeniden çalıştırın."

Belgeyi oku (dosya yolu verildiyse `Read`; yapıştırıldıysa metin). Okuyamıyorsan ORTAK-KURALLAR.md §11. Okumadan "politika bunu kapsıyor" deme.

**Sözleşmeler:** şablon ya da imzalı sözleşme dizindeyse aynı karşılaştırmayı yap; ama mevcut bir sözleşmenin değişiklik zorunluluğu (uyarlama, TBK m.138, emredici hükme aykırılık, kısmi hükümsüzlük) bir hukuki değerlendirmedir → `sozlesme-incelemesi-tbk` becerisine devret; bu beceri yalnız "hangi madde etkileniyor" der.

## 3. Fark tablosu

Her doğrudan ya da dolaylı eşleşme için:

```markdown
### Y[N]: [kısa ad]
**Yeni kural:** [yükümlülük] — [dayanak] [soorgla]
**Belgemiz ([kod/ad], son onay [tarih]) diyor ki:**
> "[ilgili alıntı]" [kullanıcı verdi]
**Boşluk:** Yok | Kısmi — [X'i karşılıyor, Y'yi karşılamıyor] | Tam — [çelişiyor ya da hiç değinmiyor]
**Gerekli değişiklik:** [somut: "4.2'ye beş iş günlük Kurum bildirimi adımı ekle" — "politikayı güncelle" değil]
**Sahibi:** [takip listesinden rol]
**Önem:** 🔴/🟠/🟡 — [gerekçe]
```

**Kısa yol (yanlış hedef):** bütün yükümlülükler aynı belgeye karşı "boşluk yok" çıkıyorsa satır satır tekrar etme; tek paragraf yaz: "[Düzenleme] [belge]de değişiklik gerektirmiyor gibi görünüyor; [belge] §X zaten [Y]'yi karşılıyor. Bu düzenlemenin dokunduğu belgeler [A] ve [B] olabilir; analizi onlara karşı çalıştırayım mı?" (upstream "Negative-finding branch").

**Taslak / teklif metni için** (`onem-suzgeci.md` §6) fark tablosu kurma; ön konumlanma paragrafı yaz.

**Önem tabanı:** önem süzgecindeki kademe burada gerekçesiz düşürülemez (ORTAK-KURALLAR.md §8). Düşürüyorsan yaz: "Süzgeç 🔴 dedi; politikamız zaten karşıladığı için 🟡'ye indiriyorum, çünkü …".

## 4. Boşluk tablosu

Yer: `~/.claude/plugins/config/soorgla-hukuk/mevzuat-takibi/bosluk-takibi.yaml` (gizlilik: `takip-listesi.md` §2; dosya sistemi yoksa §5'teki takip durumu bloğu).

```yaml
bosluklar:
  - id: B-001
    yukumluluk: "Standart sözleşme imzadan itibaren beş iş günü içinde Kuruma bildirilir"
    dayanak: "6698 m.9/5 (7499 ile değişik) [soorgla]"
    belge: "P2 Tedarikçi veri işleme sözleşmesi şablonu" # ya da "yeni belge gerekli"
    tur: kismi # yok | kismi | tam | yeni-belge | izle
    onem: "🔴"
    sahibi: "Uyum sorumlusu"
    acilis: 2026-10-31
    son_tarih: 2026-11-30 # yürürlük tarihi, iç tarih ya da (izle türünde) yeniden bakış tarihi
    yururluk_dogrulandi: true # false: kuralın yürürlükte olduğu teyit edilemedi
    durum: acik # acik | suruyor | kapandi | risk-kabul
    kapsam_siniri: "" # kapsam daraltıldıysa bildirim metni aynen
    kapanis: "" # kapanışta: ne yapıldı, kim onayladı, tarih
```

Kurallar:
- **Tekrar yok:** aynı yükümlülük + aynı belge = aynı boşluk; ikinci kez açma, mevcut kaydı güncelle.
- **`izle` türü** taslak metinler, ertelenmiş AYM iptalleri ve henüz yürürlüğe girmemiş düzenlemeler içindir; uyum boşluğu değildir, raporda ayrı blokta durur.
- **Gecikti sayma kuralı:** `yururluk_dogrulandi: false` olan kayıt hiçbir zaman "🔴 Gecikti" bloğuna girmez; "🟡 Kontrol gerekli — kural yayımlandığı gibi yürürlükteyse [N] gün gecikmiş olur; önce yürürlüğü doğrulayın" diye görünür.
- **Hatırlatma:** bildirim gönderilmez. Durum raporunda `son_tarih`'e 30 gün (`izle` hariç) kalan kayıtlar "Yaklaşanlar" bloğuna çıkar.

### Durum raporu

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1]
## Açık boşluklar — [tarih]
**Sonuç:** [N] boşluk [tarih]e kadar işlem bekliyor — en önemli üçü: …
### 🔴 Gecikti        | ID | Yükümlülük | Belge | Sahibi | Son tarih | Gecikme |
### 🟠 30 gün içinde   | … |
### 🟡 Açık            | … |
### 👀 İzlenenler (taslak, ertelenmiş yürürlük)  | ID | Konu | Yeniden bakış | Sahibi |
### Sürenler           | … |
### Son kapananlar (5) | … kapanış notuyla |
En eski açık boşluk: [ID], [N] gün · Sahibe göre dağılım: …
```

10'dan fazla satır varsa bir satırla teklif et: "Bunu sıralanabilir bir tablo görünümüne çevirmemi ister misiniz?" Kendiliğinden kurma. Tabloya giren dış kaynaklı metinlerde (`haftalik-ozet.md` §4) kaçış kurallarını uygula.

### Kapatma ve risk kabulü

- **Kapat:** kullanıcı ne yapıldığını ve kimin onayladığını söyler ("P2 v4 onaylandı, 15.11.2026, Hukuk Müdürü"). `durum: kapandi`, `kapanis` doldurulur. Taslak üretilmiş olması kapatma sebebi değildir.
- **Risk kabulü:** gerekçe ve kabul eden yetkili zorunlu ("Kural yalnız X'e uygulanır, biz X değiliz; Y olursa yeniden bakılacak — kabul eden: [rol]"). Kayıt silinmez, açık listeden düşer.
- **Kapı (ORTAK-KURALLAR.md §1):** avukat olmayan kullanıcıda kapatma, risk kabulü ya da bir uyum beyanı (denetçiye cevap, yönetim kurulu raporu, "uyumluyuz" yazısı) öncesinde "Bunu bir avukatla gözden geçirdiniz mi?" diye sor. Hayırsa avukata götürülecek özet: boşluk ve kaynağı; önerilen çözüm neyi kapsıyor, neyi kapsamıyor; kalan risk; kapatmak yerine risk kabulü ya da dış danışman görüşü gerekip gerekmediği. Durum raporu kapıya tabi değildir.

## 5. Politika değişiklik önerisi (taslak)

Girdiler — üçü de gerekli; eksikse sor, tahmin etme:
1. Boşluk (ID ya da açıklama).
2. Belgenin **onaylı güncel metni**. Dosya verildiyse sor: "Bu, belgenin onaylı ve en son sürümü mü? Eski sürüm üzerine yapılan öneri ayrışma yaratır." Yapıştırıldıysa notta "metnin güncel onaylı sürüm olduğu varsayıldı" yaz.
3. Kural metni (madde farkından, etiketleriyle).

Yazım kuralları:
- **En küçük değişiklik:** bir sözcük, sonra cümle, sonra fıkra, sonra bölüm. Boşluğun dokunmadığı bölüme dokunma, üslubu yeniden yazma.
- Silinen: `~~metin~~` · eklenen: **metin** · her değişikliğin yanında gerekçe: `[Değişiklik: 6698 m.9/5 (7499) beş iş günlük bildirim [soorgla]]`.
- Model bilgisinden gelen her tarih, süre, eşik ve atıf metnin içinde de `[doğrula]` taşır, yalnız özet tabloda değil.
- Taslak sırasında başka bir uyumsuzluk görürsen düzeltme; gözden geçiren notuna yaz: "B-003 için çalışırken [hüküm]de [yükümlülük] ile ilgili ayrı bir sorun gördüm; bu taslağa almadım, ayrı boşluk açılabilir."

Çıktı:

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu … (Güvenmeden önce: belgenin güncel onaylı sürüm olduğunu teyit edin; kuralın yürürlüğünü ve tarihini doğrulayın; belge sahibinin incelemesi ve onay süreci; boşluk yalnız uygulanıp onaylanınca kapanır.)
## Politika değişiklik önerisi: [belge]
**Boşluk:** [ID] · **Kural:** [dayanak, yürürlük] · **Belge:** [ad, son onay] · **Durum:** ÖNERİ — incelenmedi, onaylanmadı
### Sonuç (3 cümle: boşluk ne, öneri ne yapıyor, neye bakılmalı)
### İşaretli metin (yalnız etkilenen bölümler)
### Değişiklik tablosu | # | Hüküm | Mevcut | Önerilen | Neden | Kaynak |
### Uygulamadan önce
- [ ] Onaylı güncel sürüm mü · [ ] Kural yürürlükte mi · [ ] Belge sahibi incelemesi · [ ] Onay süreci · [ ] Boşluk tablosu ancak onaydan sonra güncellenir
```

- Claude Code'da dosyaya yaz: `<belge-kisa-adi>-degisiklik-onerisi-AAAA-AA-GG.md`, kullanıcının belirttiği yere ya da çalışma klasörüne; **asıl belgenin bulunduğu klasöre ve asıl dosyanın üstüne asla.** "öneri" sözcüğü ve tarih dosya adından çıkarılmaz.
- Dosya sistemi yoksa sohbette ver.
- "Bunu asıl belgeye uygula" ya da "boşluğu kapat" denirse: "Değişikliği belge sahibi inceleyip onayladıktan sonra uygular; onaylandığını söylediğinizde boşluk tablosunu güncellerim."
- Belge dilekçe, ihtarname ya da resmî yazıysa bu bölüm değil, ORTAK-KURALLAR.md §14'teki dilekçe becerisi kullanılır.

---

## Kaynak
- Upstream `policy-diff` (Scope integrity, Steps 1-4, Pre-rule / Negative-finding / Gap branches), `gap-surfacer` (tracker şeması, gap_type, "Never classify a gap as Overdue on an unverified rule", Consequential-action gate, close / risk-accept), `gaps`, `policy-redraft` (Hard guardrails, smallest-possible edit, filename). Slack bildirimi ve hatırlatma gönderimi çıkarıldı.
