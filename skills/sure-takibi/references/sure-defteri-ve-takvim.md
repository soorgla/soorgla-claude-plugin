# Süre defteri, rapor ve takvim (ICS)

**Ne zaman kullanılır:** defter okunurken ve yazılırken (`--rapor`, `--ekle`, `--guncelle`, `--tamamla`, `--kapat`), ICS üretilirken (`--takvim`), istemcide dosya sistemi yokken.

Upstream `legal-clinic/deadlines.yaml` (defter şeması, `--report` iskeleti) ve `commercial-legal/renewal-tracker` (yarı açık uyarı bantları, iş günü notu) uyarlaması.

---

## 1. Defter nerede?

Üç kip vardır. Hangisinde olduğunu her ilk yazmada ve her raporun altında tek satırla söyle.

| Kip | Ne zaman | Kaynak (okuma) | Yazma |
|---|---|---|---|
| **A. Dosya klasörlü** | Profilde "Dosya (müvekkil) çalışma alanları → Etkin: ✓" | Dosyalar arası rapor: yalnız `~/.claude/plugins/config/soorgla-hukuk/dosyalar/_liste.yaml` → her dosyanın `sureler` alanı. Dosya kartları ve belgeler **açılmaz**. | Süre eklenince/değişince ikisi birlikte (onayla): ilgili dosyanın `dosyalar/<kisa-ad>/dosya.md` "Kritik süreler" tablosu ve `_liste.yaml` satırı; `dosyalar/<kisa-ad>/_gunluk.md`'ye tek satır giriş. Ayrıntı: `../../dosya-klasoru/SKILL.md`. |
| **B. Tek defter** | Çalışma alanları kapalı (şirket içi hukuk, tek kullanıcı) ya da `dosya-klasoru` yüklü değil | `~/.claude/plugins/config/soorgla-hukuk/sure-defteri.yaml` | Aynı dosya |
| **C. Dosya sistemi yok** | claude.ai web, ChatGPT, dosya aracı kapalı masaüstü | Kullanıcının yapıştırdığı defter bloğu ya da bu sohbet | Hiçbir şey "kaydedildi" denmez; her değişiklikten sonra güncel defter **kopyalanacak blok** olarak verilir (§6) |

Kip A'da bir dosyada çalışırken başka dosyanın kartı okunmaz; dosyalar arası rapor yalnız `_liste.yaml`'daki künye alanlarıyla yapılır (`ORTAK-KURALLAR.md` "Büro profili").

**Gizlilik satırı** (raporun altında, A ve B kipinde): `Süre defteri bu bilgisayarda şifresiz tutuluyor: [yol]. Müvekkil sırrı (Av.K. m.36) ve kişisel veri (KVKK) içerir; yedekleme, bulut eşitlemesi ve paylaşım sizin sorumluluğunuzdadır.` `[model bilgisi — doğrulayın]` Proje klasörü ya da bulutla eşitlenen bir klasör kullanılıyorsa (OneDrive, Dropbox, Google Drive) bunu ayrıca söyle.

---

## 2. Satır şeması

Kip A'da `_liste.yaml` → her dosya satırının `sureler[]` alanı (dosya listesi kök düzeyde bir YAML dizisidir); kip B'de `sureler[]`. Kip A'nın zorunlu alanları `dosya-klasoru` ile aynıdır (`ne`, `son_gun`, `dayanak`, `hesap`, `durum`); diğerleri bu becerinin ek alanlarıdır, boş bırakılabilir.

```yaml
# soorgla-hukuk süre defteri — kip B (kip A'da aynı alanlar _liste.yaml içinde, dosya alanı olmadan)
# GİZLİDİR — müvekkil sırrı ve kişisel veri. Müvekkil adı yerine dosya kısa adı kullanın.
surum: 1
son_guncelleme: 2026-10-31
sureler:
  - id: "ise-iade-a-arabuluculuk-2026-11" # [dosya]-[kısa-iş]-[YYYY-AA]
    dosya: "2026-ise-iade-a" # kip A'da yok (üst satırdan gelir)
    alan: is-hukuku # alan becerisinin adı
    ne: "işe iade için arabulucuya başvuru" # tek satır: ne yapılacak
    tur: hak-dusurucu # bkz. sure-turleri-ve-kaynak-haritasi.md §1
    saat_sahibi: biz # biz | karsi-taraf | mahkeme-idare
    baslangic:
      olay: "fesih bildiriminin tebliği"
      tarih: 2026-10-20
      kesinlik: kesin # kesin | turetilmis | yaklasik
      kaynak: "[kullanıcı verdi] fesih bildirimi, elden imzalı"
    dayanak: "4857 m.20/1 [soorgla]"
    hesap: "elle [doğrula]" # legal_calculate_deadline:<kod> | elle [doğrula]
    gerekce: "Tebliğ 20.10.2026 → 4857 m.20/1 süresi (metinden) → ham bitiş … → tatil yok → son gün …; sağlama tuttu"
    son_gun: 2026-11-19 # ya da "[HESAPLANACAK]"
    son_saat: "gün sonu (UYAP) / mesai bitimi (fiziki)"
    olasi_uzama: null # geç tarih yalnız burada (ör. adli tatil tartışmalı)
    ic_hedef: 2026-11-16
    sorumlu: "Av. ___"
    bagli_sureler: ["ise-iade-a-dava-2026-12"]
    durum: acik # acik | durdu | yapildi | kapatildi | kacti
    tamamlanma: null # { tarih, kanit: "UYAP gönderim no / noter yevmiye / KEP alındısı" }
    takvim_uid: null # takvime yazıldıysa: google:<id> / outlook:<id> ya da ICS UID
    notlar:
      - "2026-10-31: eklendi (sure-takibi)"
    olusturma: 2026-10-31
```

Kurallar:
- `son_gun` hesaplanmadıysa `"[HESAPLANACAK]"`; asla tahmini tarih yazma.
- `gerekce` boş kalamaz. Tek satır özet + dayanak etiketi.
- `notlar` yalnız eklemeyle büyür; her değişiklik tarihli satırdır. Kullanıcının elle yazdığı notlar silinmez.
- `durum: kacti` ancak kullanıcı onayıyla yazılır; o zamana kadar süresi geçmiş satır `acik` kalır ve raporda ⛔ olarak görünür.
- `durum: durdu`: arabuluculuk gibi süreyi durduran bir olay; satır `notlar`'da durma sebebini ve yeniden hesap tetikleyicisini (ör. "son tutanak tarihi gelince") taşır.

---

## 3. `--ekle` akışı

1. Alanları topla: dosya, ne, tür, saat sahibi, başlangıç olayı ve tarihi (kaynağıyla), sorumlu. Eksik zorunlu alanı sor; uydurma.
2. Dayanağı çek ve son günü hesapla (`sure-hesap-kurallari.md`).
3. Mükerrer kontrolü: aynı `dosya` + `tur` + `son_gun` ya da aynı `dosya` + `ne` varsa göster ve sor.
4. Satırı göster → onay → yaz (kip A'da kart + dizin + günlük).
5. "Takvime de ekleyeyim mi?" — evet ise `--takvim <id>`.

**Başka becerilerden gelen devir:** alan becerisinin süre tablosu, dilekçe becerisinin süre satırı ya da `dava-kronolojisi`'nin "Süre aktarım bloğu" gelirse satırları tek tek değil **toplu** göster, her birinde dayanağı ve hesabı yeniden doğrula (ön hesap varsa sağlamaya katılır), sonra tek onayla yaz. Kronoloji bloğundaki "Tarih kesinliği: yaklaşık" satırlar `kesinlik: yaklasik` ve `[incele]` alır.

## 4. `--guncelle`, `--tamamla`, `--kapat`

- **`--guncelle`:** tarih (ör. mahkeme süre uzattı), sorumlu, durum. Tarih değişikliğinin kaynağı zorunlu (ara karar, tutanak). Eski tarih silinmez, `notlar`'a "eski son gün … → yeni …, kaynak …" yazılır.
- **`--tamamla`:** "İş gerçekten yapıldı mı?" diye sor ve kanıtı iste (UYAP gönderim bilgisi, noter yevmiye no, KEP alındısı, arabuluculuk başvuru no). Kanıt yoksa `tamamlanma.kanit: "[kullanıcı beyanı]"`. Bağlı süreler varsa ("son tutanak → dava süresi") başlangıç tarihini şimdi doldurmayı öner.
- **`--kapat`:** sulh, feragat, dosyanın bitmesi, sürenin artık uygulanmaması. Gerekçe zorunlu; gerekçesiz kapatma yok.

---

## 5. Rapor iskeleti (`--rapor`)

```markdown
[TASLAK BAŞLIĞI — ORTAK-KURALLAR.md §1, role göre]

> ⚠️ Gözden geçiren notu (ORTAK-KURALLAR.md §8) — Kaynaklar · Okunan: [defter: N satır, M dosya] · Güncellik: [tatil kontrolü legal_check_holiday ile yapıldı | yapılamadı] · Güvenmeden önce: [en yakın 🔴 satırın hesabını bağımsız kontrol edin] · Profil

# Süre raporu — [bugün, haftanın günü]

**Açık süre:** [N] · **⛔ Süresi geçmiş:** [N] · **🔴 0–6 gün:** [N] · **Hesaplanmamış:** [N]

## ⛔ Süresi geçmiş (çözülene kadar burada kalır)
| ID | Dosya | Ne | Tür | Son gün | Geçen gün | Sorumlu | Hesap gerekçesi |

## 🔴 0–6 gün
| ID | Dosya | Ne | Tür | Son gün (gün) | Kalan gün / iş günü | İç hedef | Sorumlu | Hesap gerekçesi |

## 🟠 7–13 gün
[aynı tablo]

## 🟡 14–29 gün
[aynı tablo]

## 🟢 30–89 gün
[aynı tablo]

## 90 gün ve sonrası
[yalnız sayı — `--ufuk=N` ile açılır]

## Hesaplanmamış süreler
| ID | Dosya | Ne | Eksik olan (başlangıç tarihi / dayanak / tebliğ türü) |

## Durmuş süreler
| ID | Dosya | Ne | Durma sebebi | Yeniden hesap tetikleyicisi |

## İzlenen karşı taraf / mahkeme saatleri
| ID | Dosya | Kimin saati | Son gün | Geçince bizim için ne doğar |

## Sorumluya göre
| Sorumlu | ⛔ | 🔴 | 🟠 | 🟡 | Toplam açık |

## Alana göre
[aynı tablo, alan becerisine göre]

## Sorumlusuz satırlar
[liste]

---
**Son günü beklemeyin.** [SKILL.md Adım 7'deki sabit uyarı]

Süre defteri: [kip ve yol | "yalnız bu sohbette"] · Gizlilik satırı (§1)

**Kontrol listemde olmayan ama soracağım bir soru:** …
**Şimdi ne yapalım?** 1. [🔴 satır için dilekçe becerisine geç] 2. Hesaplanmamış süreler için eksik bilgileri topla 3. Yükselt — [profildeki kişi] 4. Takvime aktar (takvim bağlayıcısı ya da ICS) 5. Başka bir şey
```

- Bant kalan güne göre; her satır yalnız bir banda düşer (yarı açık aralıklar: 0–6, 7–13, 14–29, 30–89). Kalan gün = son gün − bugün.
- İç hedef günü geçmiş ama son günü gelmemiş satıra `⚠ iç hedef geçti` yaz.
- Son gün arife, hafta sonu öncesi Cuma ya da adli tatil dönüşü ise "Tarih" hücresinde haftanın gününü ve notu göster (renewal-tracker: tarih **haftanın günüyle** yazılır; çıplak tarih yanıltır).
- Satır sayısı ~15'i geçerse ya da kullanıcı isterse görsel bir pano (artifact) öner: bant sayıları, zaman çizelgesi, sıralanabilir tablo. Önermek serbest, kurmak onayla.
- Avukat olmayan kullanıcıda her satırın yanına tek cümle sade açıklama: "(İstinaf: kararı üst mahkemeye taşıma süresi.)"

---

## 6. Dosya sistemi yokken (kip C)

- Defteri sohbet içinde yukarıdaki YAML biçiminde tut; her yazma kipinden sonra **tamamını** tek bir kod bloğu olarak ver ve "Bunu kendi dosyanıza kopyalayın; bir sonraki sohbette yapıştırırsanız devam ederim" de.
- Hiçbir zaman "kaydettim", "deftere işledim" deme; "aşağıdaki bloğu güncelledim" de.
- Sohbet geçmişinin bulut hizmetinde tutulduğunu ve müvekkil adı yerine kısa ad kullanmanın önemini bir kez söyle.
- ICS bloğunu yine üret (§7); kullanıcı metni `.ics` uzantılı bir dosyaya kaydedip takvime içe aktarır.

---

## 7. Takvime aktarım (`--takvim`)

Varsayılan çıktı bir **ICS (iCalendar, RFC 5545) bloğudur**. Kullanıcı bloğu `sureler.ics` adıyla kaydedip içe aktarır:
- **Google Takvim:** Ayarlar → İçe ve dışa aktar → İçe aktar → dosyayı seç → hedef takvim. Önce ayrı bir "Süreler" takvimi oluşturmak, toplu silmeyi kolaylaştırır.
- **Outlook (masaüstü/web):** Takvim → Takvim ekle → Dosyadan yükle (web) ya da Dosya → Aç ve Dışarı Aktar → İçeri/Dışarı Aktar (masaüstü).
- **Apple Takvim:** Dosya → İçe Aktar.

### 7.1 Takvime doğrudan yazma (takvim bağlayıcısı varsa)

Oturumda takvim etkinliği oluşturabilen bir araç varsa (Google Takvim, Microsoft 365 / Outlook Takvim bağlayıcısı;
araç adı istemciye göre değişir — listede "event", "calendar", "etkinlik" geçen oluşturma/güncelleme aracı) ICS
yerine doğrudan takvime yazmayı **öner**. Araç yoksa ya da kullanıcı istemezse ICS (aşağıda) — hiçbir şey bozulmaz.

1. **Önizleme ve açık onay.** Yazmadan önce her etkinliği tablo olarak göster (başlık, tarih, tüm gün, hatırlatıcılar,
   hedef takvim) ve "Bu N etkinliği [takvim adı] takvimine ekleyeyim mi?" diye sor. Onay yoksa yazma. Kullanıcı
   hangi takvimi kullanacağını söylemediyse sor; mümkünse ayrı bir "Süreler" takvimi öner.
2. **Ne yazılır:** ICS'teki iki etkinliğin aynısı — `İÇ HEDEF — …` ve `SON GÜN — …`, tüm gün; açıklamada hesap
   gerekçesinin özeti, dayanak madde ve **"Taslak hesap — avukat doğrulaması gerekir"** notu. Hatırlatıcıları aracın
   desteklediği biçimde ekle (profil eşikleri; varsayılan 14/7/3/1 gün önce); desteklemiyorsa söyle.
3. **Gizlilik** aynı: başlık ve açıklamada müvekkil adı, T.C. kimlik no, karşı taraf adı yok; yalnız dosya kısa adı.
4. **Kayıt:** aracın döndürdüğü etkinlik kimliklerini defterdeki satırın `takvim_uid` alanına yaz
   (`google:<id>` / `outlook:<id>`). Böylece sonraki işlemler takvimi de günceller.
5. **Güncelleme ve kapatma:** `--guncelle` ile son gün değişirse, `--tamamla` / `--kapat` ile süre kapanırsa ve
   satırda `takvim_uid` varsa takvimdeki etkinliği de güncellemeyi ya da silmeyi **öner** (yine onayla).
   Aracın güncelleme/silme yetkisi yoksa kullanıcıya eski etkinliği elle silmesini söyle.
6. **Hesaplanmamış süre** (`son_gun: [HESAPLANACAK]`) ve araç ile elle hesabın ayrıştığı süre takvime yazılmaz; önce
   hesap netleşir (erken tarih esas).
7. Araç hata dönerse ya da yanıt vermezse ICS'e düş ve durumu söyle; yarım kalan etkinlikleri listele.

**Her süre için iki etkinlik:**
1. `İÇ HEDEF — [dosya kısa adı] [iş]` — iç hedef gün, tüm gün.
2. `SON GÜN — [dosya kısa adı] [iş]` — son gün, tüm gün; hatırlatıcılar profildeki eşiklerden (varsayılan: 14, 7, 3, 1 gün önce ve aynı gün sabah).

**Gizlilik:** başlık ve açıklamaya müvekkil adı, T.C. kimlik no, karşı taraf adı, olay ayrıntısı yazma. Yalnız dosya kısa adı, iş türü, dayanak ve hesap gerekçesinin özeti. Takvim büyük ihtimalle bulutta eşitlenir ve başkalarıyla paylaşılabilir.

**Teknik kurallar:**
- Tüm gün etkinliği: `DTSTART;VALUE=DATE:YYYYMMDD`, `DTEND;VALUE=DATE:` ertesi gün.
- `UID` kalıcıdır: `<satır id>-songun@soorgla-hukuk` ve `<satır id>-ichedef@soorgla-hukuk`. Aynı UID ile yeniden içe aktarma, takvim uygulamasına göre günceller ya da çoğaltır `[incele]`; tarih değiştiyse kullanıcıya eski etkinliği silmesini söyle.
- `DTSTAMP` UTC (`YYYYMMDDTHHMMSSZ`), üretim anı.
- Metindeki virgül `\,`, noktalı virgül `\;`, satır sonu `\n` olarak kaçırılır. 75 baytı aşan satırlar katlanır (satır sonu + bir boşlukla devam). Türkçe karakterler UTF-8.
- RFC 5545 satır sonu CRLF'dir; dosyaya yazıyorsan CRLF kullan. Sohbet bloğunda LF ile verilen metni Google ve Outlook genellikle kabul eder; içe aktarma başarısız olursa CRLF ile yeniden kaydet.
- Saat dilimi gerekmez (tüm gün). Saatli etkinlik (duruşma) gerekiyorsa `DTSTART;TZID=Europe/Istanbul:YYYYMMDDTHHMMSS` ve `VTIMEZONE` bloğu ekle.

**Şablon** (bir süre, iki etkinlik):

```text
BEGIN:VCALENDAR
VERSION:2.0
PRODID:-//soorgla-hukuk//sure-takibi//TR
CALSCALE:GREGORIAN
METHOD:PUBLISH
X-WR-CALNAME:Süreler
BEGIN:VEVENT
UID:[id]-ichedef@soorgla-hukuk
DTSTAMP:[YYYYMMDDTHHMMSSZ]
DTSTART;VALUE=DATE:[iç hedef YYYYMMDD]
DTEND;VALUE=DATE:[iç hedef + 1 gün]
SUMMARY:İÇ HEDEF — [dosya kısa adı] [iş]
DESCRIPTION:Son gün [GG.AA.YYYY]. Dayanak: [madde]. Taslak — avukat do
 ğrulaması gerekir.
TRANSP:TRANSPARENT
BEGIN:VALARM
ACTION:DISPLAY
DESCRIPTION:İç hedef bugün — [dosya kısa adı] [iş]
TRIGGER;RELATED=START:PT9H
END:VALARM
END:VEVENT
BEGIN:VEVENT
UID:[id]-songun@soorgla-hukuk
DTSTAMP:[YYYYMMDDTHHMMSSZ]
DTSTART;VALUE=DATE:[son gün YYYYMMDD]
DTEND;VALUE=DATE:[son gün + 1 gün]
SUMMARY:SON GÜN — [dosya kısa adı] [iş]
DESCRIPTION:Hesap: [gerekçe özeti]. Dayanak: [madde]. Son günü bekleme
 yin. Taslak — avukat doğrulaması gerekir.
TRANSP:TRANSPARENT
BEGIN:VALARM
ACTION:DISPLAY
DESCRIPTION:7 gün kaldı — [dosya kısa adı] [iş]
TRIGGER;RELATED=START:-P7D
END:VALARM
BEGIN:VALARM
ACTION:DISPLAY
DESCRIPTION:3 gün kaldı — [dosya kısa adı] [iş]
TRIGGER;RELATED=START:-P3D
END:VALARM
BEGIN:VALARM
ACTION:DISPLAY
DESCRIPTION:1 gün kaldı — [dosya kısa adı] [iş]
TRIGGER;RELATED=START:-P1D
END:VALARM
END:VEVENT
END:VCALENDAR
```

- Şablonda yer kazanmak için 7/3/1 gün gösterildi; varsayılan 14/7/3/1 ve aynı gün sabah. Hatırlatıcı sayısını profildeki eşiklere göre artır ya da azalt; bazı takvimler (Google içe aktarma) VALARM'ı yok sayıp kendi varsayılan bildirimini kullanır, bunu kullanıcıya söyle.
- `son_gun: [HESAPLANACAK]` olan satır için etkinlik **üretme**; "hesaplanmadığı için takvime alınmadı" de.
- `--takvim hepsi`: yalnız `durum: acik` satırlar, tek VCALENDAR içinde.
- Takvime aktarılan satırda `takvim_uid` alanını doldurmayı öner (onayla).

