# Yol seçimi: tüketici hakem heyeti, arabuluculuk ve tüketici mahkemesi

## Ne zaman kullanılır
- Esas değerlendirmesi (ayıp, cayma, kredi, konut) bitti; **nereye, hangi sırayla** başvurulacağı belirlenecek.
- THH kararı geldi; **itiraz** edilecek (tüketici ya da işletme tarafı) ya da karşı taraf itiraz etti.
- Arabuluculuk dava şartı mı, değil mi? Tüketici mahkemesi yetkili yer, harç, kanun yolu.
- İşletme tarafı: THH başvurusuna cevap, THH kararının icrası, itiraz stratejisi.
- **Metinler başka becerilerde:** avukatsız THH başvurusu → `../../vatandas-basvurulari/references/tuketici-hakem-heyeti.md`; arabuluculuk başvurusu ve dava/itiraz dilekçesi → `../../hukuk-yargilamasi-dilekce/SKILL.md`.

---

## Karar ağacı

```
1. Tüketici işlemi ya da tüketiciye yönelik uygulama mı? (6502 m.3, m.83/2)
   └─ Hayır → genel mahkeme (asliye hukuk / ticaret), TBK/TTK → başka beceri
2. Uyuşmazlık değeri, başvuru tarihindeki THH sınırının altında mı?
   (legal_get_social_parameters tur:"thh_parasal_sinir")
   ├─ Altında → THH ZORUNLU (İİK hakları saklı). Arabuluculuk yok (m.73/A-1-a).
   │ └─ THH kararı → 2 hafta içinde tüketici mahkemesine itiraz → karar KESİN
   └─ Üstünde → THH'ye başvurulamaz (ya da aşan kısımdan feragatle THH)
         ├─ Taşınmazın aynından doğan uyuşmazlık mı? → arabuluculuk yok, doğrudan dava (m.73/A-1-d)
         └─ Diğer → önce ARABULUCULUK (dava şartı) → anlaşmazlık → tüketici mahkemesi
                   → istinaf/temyiz kesinlik sınırına göre
```

---

## Süreler ve dayanakları

| Süre / kural | Başlangıç | Dayanak | Not |
|---|---|---|---|
| THH sınırı: başvuru tarihindeki yılın sınırı; her yıl yeniden değerleme oranıyla artar | Başvuru tarihi | 6502 m.68/1, 68/4; THH Yön. m.6 | **Tutarı beceriye yazma**; her seferinde çek |
| THH kararına itiraz: **iki hafta** | Kararın **tebliği** | 6502 m.70/3 | Eski YAML "15 günlük hak düşürücü süre" diyordu; kanun metni **iki hafta**. İtiraz kararın icrasını durdurmaz; talep edilirse hâkim tedbirle durdurabilir. |
| THH tebligatı: önce elektronik (VUK m.107/A), olmazsa 7201 | — | 6502 m.70/2 (7392/14) | Tebliğ tarihini e-tebligat kaydından al; usulsüz tebligatta süre `[incele]` |
| İtiraz üzerine tüketici mahkemesi kararı **kesin** | — | 6502 m.70/5 | İstinaf/temyiz yok; tek şans 🔴 |
| Arabuluculuk sonuçlanmadan dava açılamaz; son tutanak tarihi ve dava açma süresi 6325 m.18/A'ya göre | Son tutanak | 6502 m.73/A; 6325 m.18/A `[doğrula]` | 6325 m.18/A-11 (toplantıya katılmayan tarafa yargılama gideri) **tüketici aleyhine uygulanmaz** (m.73/A-2) |
| Ayıplı mal zamanaşımı vb. esas süreleri | — | ilgili referans dosyası | Arabuluculuk başvurusunun zamanaşımına etkisi `[incele]` |

`legal_calculate_deadline` "thh_itiraz" kodunu tanımıyor; elle hesapla, son günü `legal_check_holiday` ile kontrol et, `[doğrula]`.

---

## Kontrol listesi — THH

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| THH-DEĞER | Uyuşmazlık değeri doğru belirlendi mi (fatura bedeli, istenen iade, tazminat toplamı)? Sınır başvuru yılınınki mi? | 6502 m.68/1 | Aşan kısımdan feragat edilen tutar bir daha istenemeyebilir `[incele]` |
| THH-YER | Tüketicinin yerleşim yeri ya da işlemin yapıldığı yerdeki THH; THH yoksa ilçe kaymakamlığı (yetkili heyete iletir) | 6502 m.68/3 (7392/13) | |
| THH-YETKİ | Heyetlerin yetki alanı ve iş bölümü Bakanlıkça belirlenir | 6502 m.66/1 (7392/12) | Görevsizlik/yetkisizlik riskine bak |
| THH-DELİL | **Bütün** belgeler THH'ye verildi mi? Tüketici lehine kararın, THH'ye verilmeyen belge mahkemeye sunulduğu için iptalinde tüketici aleyhine gider ve vekâlet ücreti yok; diğer iptallerde tüketici aleyhine nispi vekâlet ücreti | 6502 m.70/6 (7392/14) | İşletme tarafı: THH'ye savunma ve belge **vermemek** itirazda yeni belge sunmayı ucuzlatmaz; THH aşamasında eksiksiz savun |
| THH-MASRAF | THH vekâlet ücretine hükmedemez; tüketici aleyhine kararda tebligat ve bilirkişi giderini Bakanlık karşılar | 6502 m.70/1, 70/7 | |
| THH-İCRA | THH kararı ilam gibi icra edilir; kesinleşme beklenmez | 6502 m.70/2 son cümle, m.70/3 | İcra takibine karşı tedbir talebi `[incele]` |

## Kontrol listesi — THH kararına itiraz

| Kod | Kontrol | Not |
|---|---|---|
| İT-SÜRE | Tebliğ tarihi ve iki haftalık son gün; e-tebligatta okunma/5. gün kuralı `[doğrula]` | 🔴 süre geçtiyse |
| İT-MERCİ | Kararı veren THH'nin ya da tüketicinin yerleşim yerindeki tüketici mahkemesi (m.70/3) | Tüketici mahkemesi yoksa asliye hukuk mahkemesi tüketici mahkemesi sıfatıyla `[model bilgisi — doğrulayın]` |
| İT-HUSUMET | İtiraz karşı tarafa (tüketici ya da satıcı) yöneltilir; heyet taraf değildir | `[model bilgisi — doğrulayın]` |
| İT-ARABULUCULUK | THH kararına itirazda dava şartı arabuluculuk **yok** (m.73/A-1-b) | Eski YAML'da doğru |
| İT-DENETİM | Usul: tebligat, görev/yetki, değer; esas: bilirkişi incelemesi yapılmış mı, rapor denetime elverişli mi, ispat yükü (m.10/1 karinesi) doğru mu? | Mahkeme evrak üzerinden düzelterek onayabilir (m.70/4) |
| İT-TEDBİR | Kararın icrasının tedbirle durdurulması talep edilecek mi? | m.70/3 son cümle |
| İT-KESİNLİK | Mahkeme kararı kesin; bütün delil ve itirazları ilk dilekçede topla | m.70/5 |

## Kontrol listesi — tüketici mahkemesi

| Kod | Kontrol | Dayanak | Not |
|---|---|---|---|
| TM-GÖREV | Tüketici işlemi ve tüketiciye yönelik uygulamadan doğan davada tüketici mahkemesi görevli; başka kanunda özel düzenleme görevi değiştirmez | 6502 m.73/1, m.83/2 | Görev dava şartıdır |
| TM-YETKİ | Tüketici kendi yerleşim yerindeki tüketici mahkemesinde de dava açabilir; sözleşmedeki yetki şartı bunu kaldırmaz | 6502 m.73/5 | |
| TM-HARÇ | Tüketicinin (ve Bakanlık/tüketici örgütünün) açtığı dava harçtan muaf; işletmenin açtığı davada harç `legal_calculate_court_fee` | 6502 m.73/2 | Muafiyet yargılama giderlerini (bilirkişi, tanık) kapsamayabilir `[incele]` |
| TM-USUL | HMK Altıncı Kısım (basit yargılama) | 6502 m.73/4 | Dilekçe teatisi ve süreler buna göre → hukuk-yargilamasi-dilekce |
| TM-ARABULUCU-ÜCRET | Anlaşmazlık, ulaşılamama ya da katılmama hâlinde tüketicinin payına düşen arabuluculuk ücreti Adalet Bakanlığı bütçesinden (iki saatlik tarife sınırı); dava tüketici lehine biterse davalıdan tahsil | 6502 m.73/A-3, 73/A-4 | Tüketiciye maliyet açısından anlat |
| TM-TOPLU | Bakanlık ve tüketici örgütlerinin genel nitelikli davaları, seri malın toplatılması davası (m.74) arabuluculuktan muaf | 6502 m.73/6, m.74, m.73/A-1-c, ç | |
| TM-KANUN-YOLU | THH itirazı dışındaki kararlarda istinaf/temyiz kesinlik sınırına göre → `legal_get_social_parameters` ya da HMK m.341, 362 metni | `[doğrula]` | → `../../kanun-yollari-dilekce/SKILL.md` |
| TM-GEÇİŞ | Arabuluculuk şartı yürürlüğünden (7251) önce açılmış davalara uygulanmaz | 6502 geçici m.2 | |

---

## Görüşme soruları

| Alan | Soru |
|---|---|
| Değer | Toplam talep (iade + tazminat + faiz) ne kadar? Hangi tarihte başvuracaksınız? |
| Yer | Yerleşim yeriniz ve işlemin yapıldığı yer? |
| Önceki adım | Daha önce THH'ye/arabulucuya başvurdunuz mu? Derdest başka dava var mı? |
| THH kararı | Karar tarihi, **tebliğ tarihi ve yöntemi** (e-Devlet, posta)? Karar kimin lehine, gerekçesi, bilirkişi raporu var mı? |
| Belgeler | THH'ye hangi belgeleri verdiniz, hangilerini vermediniz? |
| İcra | THH kararıyla icra takibi başlatıldı mı? |

---

## soorgla çağrıları

```
legal_get_social_parameters tur: "thh_parasal_sinir" # ÖNCE BU
legal_search_official_gazette query: "Parasal Sınırların Artırılmasına İlişkin Tebliğ" search_in: "title" sort_by: "date_desc"
legal_get_statute_article law_no: "6502" article_no: "66" | "68" | "69" | "70" | "73" | "74" | "83"
legal_get_statute_article law_no: "6502" law_type: "Kanun" article_no: "73/A" # harfli madde doğrudan gelir
legal_list_statute_articles law_no: "6502" article_kind: "gecici" include_content: true
legal_get_statute_article law_no: "39730" article_no: "<madde>" # Tüketici Hakem Heyetleri Yönetmeliği
legal_search_statute_semantic mevzuat_no: "6325" sorgu: "dava şartı arabuluculuk son tutanak dava açma"
legal_calculate_court_fee ... # yalnız işletmenin açtığı davada
legal_check_holiday tarih: "<itiraz son günü>"
legal_search_cases mahkeme: "bam" sorgu: "tüketici hakem heyeti kararına itiraz süre tebliğ iki hafta"
```

---

## Çıktı iskeleti — yol ve süre notu

```markdown
[TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu … (Güncellik: THH sınırı [yıl] dönemi çekildi — [tarih])

## Başvuru yolu: [olay] — [tarih]

### Sonuç
[THH zorunlu / arabuluculuk + tüketici mahkemesi / doğrudan dava — tek cümle neden]

### Değer ve sınır
| Kalem | Tutar | Toplam | THH sınırı ([yıl], soorgla) | Sonuç |

### Süre tablosu
| Süre | Başlangıç | Son gün | Dayanak | Durum |

### Sıradaki adım ve devir
[THH başvurusu → vatandas-basvurulari / arabuluculuk → hukuk-yargilamasi-dilekce / itiraz dilekçesi → hukuk-yargilamasi-dilekce]

### Dayanaklar · Eksik bilgi · Şimdi ne yapalım?
```

---

## Sık hatalar
- Eski yılın THH sınırını kullanmak (YAML'daki 2024/2025 tutarları bayat).
- THH itiraz süresini 15 gün sanmak (iki hafta; hafta sonu ve tatil kontrolü ayrıca).
- THH görevindeki uyuşmazlıkta arabulucuya gitmek ya da sınır üstünde arabuluculuğu atlamak.
- THH'ye belge vermeyip itiraz aşamasında sunmak (m.70/6 sonucu).
- THH itirazı sonrası istinaf yoluna gitmeye çalışmak (karar kesin).
