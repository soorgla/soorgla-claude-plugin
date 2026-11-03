# İhale danışmanı — çok dosyalı şikâyet ve itiraz takibi

**Kim için:** birden çok istekli firma adına doküman tarayan, şikâyet ve itirazen şikâyet yürüten kullanıcı. Profildeki
ihale rolü "İhale danışmanı" ya da kullanıcı birden çok firmanın birden çok ihalesini aynı anda soruyor. Ürün metninde
"ihale danışmanı", "şikâyet ve itiraz takibi" de; argo ad kullanma.

**Hukuki yeri:** danışman başvuru sahibi değildir. Şikâyeti ve itirazen şikâyeti **müvekkil firma** (aday, istekli,
istekli olabilecek) kendi adına yapar; ehliyet, hak kaybı ve süre firmaya göre değerlendirilir. Bu dosya istekli
modunun (`istekli-sikayet-itirazen.md`) **üstüne** çok dosya düzenini koyar. Esas ve süre kuralları aynıdır.

## 1. Dosya düzeni — ihale × firma başına bir klasör

- Her **(İKN, müvekkil firma)** çifti ayrı dosyadır → `../../dosya-klasoru/SKILL.md`.
  - Klasör adı: İKN + firma kısa adı.
  - İçerik:
    - ihale künyesi: İKN, idare, tür, usul, ilan ve ihale tarihi, 21/b-c mi;
    - doküman indirme tarihi;
    - tarama sonucu;
    - süre satırları;
    - numaralı iddia listesi;
    - bedel ve iade hesabı;
    - durum.
- **Müvekkil firma adları profile yazılmaz,** yalnız dosya klasörüne (profil bütün dosyalarda okunur).
- Bir ihalede **birden çok müvekkil** varsa dur ve kullanıcıya sor 🟠:
  - Aynı ihalede rakip firmalara birlikte danışmanlık çıkar çatışması doğurur.
  - Tekliflerin ortak hazırlanması ya da birbirine göre ayarlanması 4734 m.17/a-b ve d kapsamında yasak fiil riski
    taşır: anlaşma, rekabeti etkileme, dolaylı birden fazla teklif. `[soorgla]`
  - Dosyaları ayrı tut, belgeleri karıştırma `[incele]`.

## 2. Çok dosyalı süre tablosu

Bütün açık dosyaların halkalarını tek tabloda, **son güne göre sıralı** ver. Her satır `legal_calculate_deadline` ile
hesaplanır (kodlar `sure-zinciri.md` §3; olay günü sayılmaz). Tablo `../../sure-takibi/SKILL.md` defterine aktarılır:
her halka ayrı satır.

| İKN | Firma | Halka | Başlangıç olayı (tarih) | Kod | Son gün | Kalan | Durum |
|---|---|---|---|---|---|---|---|
| … | … | İlan / doküman şikâyeti | ilana yansıyan hususta **ilk ilan**; diğerlerinde doküman indirme | `kik_complaint_before_tender` + ihaleden geriye 3 iş günü | erken olan | | 🔴/🟠/✅ |
| … | … | Açıklama talebi son günü | ihale / son başvuru tarihi (geriye doğru) | kod yok — ihaleden 20 gün önce, elle (4734 m.29) | | | şikâyet süresini **durdurmaz** |
| … | … | Sonuç şikâyeti | kesinleşen karar bildirimi | `kik_complaint` (21/b-c: `kik_complaint_21bc`) | | | |
| … | … | İdare kararı | şikâyet kaydı | `kik_complaint_decision` | | | bekleniyor |
| … | … | İtirazen şikâyet | idare kararı bildirimi / karar süresi bitimi | `kik_objection` / `kik_objection_no_decision` | | | |
| … | … | Dava | Kurul kararı tebliği | `kik_lawsuit` (güvenli gün) | | | |

- **İşaretler:** son güne ≤ 3 gün kaldıysa 🔴; ≤ 7 gün kaldıysa 🟠. Süresi geçen satır silinmez, "kaçtı" yazılır.
- **Doküman şikâyeti:** iki sınır var; erken olan son gündür:
  - araç 10 günü verir (`kik_complaint_before_tender` canlı);
  - ihaleden geriye 3 iş günü `legal_check_holiday` ile ayrıca sayılır.
  - Başlangıç: iddia ilanda da yer alan bir hususa (benzer iş, iş deneyimi oranı, yeterlik kriterleri) yönelikse **ilk
    ilan tarihi**, değilse doküman indirme tarihi (4734 m.55/1). Bir dosyada iki tür iddia varsa iki ayrı satır aç.
- **Açıklama talebi** ayrı satırdır (ihaleden 20 gün önce); şikâyet süresini durdurmaz, uzatmaz. Aynı dosyada iki son
  gün birlikte izlenir; aykırılık iddiası açıklama cevabına bırakılmaz.
- **Sözleşme imzalandıysa** o dosyada şikâyet yolu kapanır (4734 m.55/1); satır "kapandı" olur.
- **Tarih bilinmiyorsa** hesap uydurulmaz:
  - Bilinmeyen tarih satırda boş kalır, "Eksik bilgi"ye yazılır.
  - Doküman indirme tarihi EKAP hesabındaki indirme kaydından alınır; **ilk ilan tarihi** EKAP ilanından (düzeltme
    ilanı varsa ikisi de yazılır `[incele]`).

## 3. Doküman tarama — "şikâyete dayanak" listesi

Her yeni dokümanda sırayla bak. Bulguyu "hukuka aykırı mı (şikâyet konusu) yoksa ticari risk mi (fiyata yansıt)"
diye ayır; esası **tür becerisi** değerlendirir (`ihale-yapim`, `-mal`, `-hizmet`, `-danismanlik`).

| # | Bak | Dayanak / araç | Esas |
|---|---|---|---|
| 1 | **Marka, model, menşe** ya da belirli ürüne yönelik özellik; "veya dengi" yok | 4734 m.12 (standart yoksa ancak "veya dengi" ile) `[soorgla]` | tür becerisi (malda teknik şartname) |
| 2 | **Benzer iş** tanımı: ihale konusundan **dar** (tek ürün/tek hizmet, ana kalemlerden yalnız biri) ya da yapımda grup seçimi işe uymuyor. Tanım ihale konusuyla aynı ya da daha genişse "dar tanım" emsalleri uygulanmaz (`kik-emsal-arama.md`). İlana yansıdığı için süre ilk ilandan | ilgili uygulama yönetmeliği + Benzer İş Grupları Tebliği (yapım) | tür becerisi |
| 3 | **Orantısız yeterlik:** iş deneyimi oranı, ciro, personel, makine, kalite belgesi işin ölçeğini aşıyor | yönetmelikteki oran aralığı (araçtan çek, metne yazma) | tür becerisi |
| 4 | **Tipten sapma:** idari şartnamede tip maddeye ekleme, çıkarma, değiştirme (yeterlik, teminat, fiyat dışı unsur, fiyat farkı, iş ortaklığı) | tip şartname: form bankası `KIK-YON-<no>-EK<n>` (KİK) / `MEV-…` (mevzuat.gov.tr); `legal_get_form` gelene kadar KİK sitesindeki tip metin | tür becerisi |
| 5 | **İlan süresi ve usul:** eşik, ilan süresi, 21/b-c gerekçesi, kısmi teklif | `legal_calculate_tender` `usul_kontrol` (ilan tarihiyle) | `../../kamu-ihale/SKILL.md` |
| 6 | **Rekabeti daraltan diğer şartlar:** yer şartı, kısa teslim, gereksiz numune, orantısız ceza | 4734 m.5 (rekabet, eşit muamele), m.12 `[soorgla]` | tür becerisi |
| 7 | **Fiyat farkı ve yerli malı maddeleri** esaslara ve listelere uygun mu | fiyat farkı esasları (tür becerisi); yerli malı listeleri | tür becerisi |

- Doküman şikâyeti **ihaleden önce** yapılır; ihaleden sonra aynı doküman iddiası çoğu zaman süre yönünden reddedilir.
- Tarama sonucu dosyaya "bulgu / şikâyet edilir mi / gerekçe / son gün" olarak yazılır.

## 4. Emsal ve mahkeme etkisi

Her iddia için en az bir yakın tarihli KİK kararı → `kik-emsal-arama.md`.

- **Kontrol:** emsal gösterilen Kurul kararının mahkeme kararıyla iptal ya da kısmen iptal edilip edilmediğine bakılır.
- **Kontrol edilmemiş** karar emsal diye müvekkile sunulmaz.
- **Satır yoksa:** karar metninin başında "Mahkeme etkisi" satırının olmaması etkilenmediği anlamına gelmez; ek mahkeme
  kararı araması gerekir.

## 5. Bedel ve iade — dosya başına

- **Bedel:** `usul_kontrol` ile yaklaşık maliyet dilimine ve **ilan dönemine** göre çekilir. Tutar metne yazılmaz.
  Dosyaya bedel, dönem ve dayanak yazılır.
- **İade:** haklı bulunan iddia sayısı / toplam iddia × bedel (Başvurular Yön. m.18/A; iddia sayımı m.18/6)
  `[soorgla]`.
  - Talep süresi: Kurul kararının bildiriminden 30 gün (4734 m.53/j; kod yok, elle).
  - Usulden ret ve eşit muamele incelemesiyle iptal ya da düzeltici işlem hallerinde iade yok (m.18/A-1).
- **İddia sayısının bedele etkisi:** iddiaları gereksiz bölmek iade oranını düşürür; birleştirmek "aynı hususa ilişkin"
  ölçütüne bağlıdır (m.18/A-2-a). İddia listesini buna göre kur → `istekli-sikayet-itirazen.md`.

## 6. Çıktı — danışman görünümü

```markdown
## Şikâyet ve itiraz takibi — [tarih] — [n] açık dosya

### Bu hafta son günü dolanlar (🔴/🟠)
| İKN | Firma | Halka | Son gün | Yapılacak |

### Dosya özetleri
**[İKN] — [firma] — [tür, usul]**
- Aşama: [doküman taraması / şikâyet / itirazen şikâyet / dava / kapandı]
- Bulgular: [numaralı]; şikâyet edilecekler: [n]
- Bedel: [dönem, tutar araçtan] · iade beklentisi: [oran]
- Emsal: [künye, MK durumu]
- Eksik bilgi: [ ]
```

Sonra tek dosyaya inilecekse o dosya için `SKILL.md` Adım 5 çıktısı. Dilekçe metni → `../../ihale-belgeleri/SKILL.md`
(her firma kendi adına imzalar).

## 7. Sık hatalar

- 🔴 Bütün dosyalara tek süre saymak: başlangıç olayı firma ve ihaleye göre değişir (indirme tarihi, bildirim tarihi).
- 🔴 Doküman şikâyetinde 3 iş günü sınırını kaçırmak.
- 🔴 Aynı ihalede birden çok müvekkilin dosyasını birlikte yürütmek (m.17 riski; bkz. §1).
- 🟠 Müvekkil adlarını profile yazmak.
- 🟠 MK kontrolü yapılmamış Kurul kararını emsal göstermek.
