# Uluslararası koruma ve geçici koruma

## Ne zaman kullanılır
- "Sığınma başvurusu yapmak istiyor", "ülkesine dönerse öldürülür", "mülteci başvurusu reddedildi", "başvurusu kabul edilemez bulundu", "hızlandırılmış değerlendirme", "Uluslararası Koruma Değerlendirme Komisyonuna itiraz", "geçici koruma kimliği iptal edildi".
- Sınır dışı kararı alınmış kişinin ülkesinde ciddi risk varsa bu dosya ile `sinir-disi-ve-idari-gozetim.md` birlikte okunur.

**Bu dosya YAML'sız, madde metinlerinden kuruldu.** Eski backend'de uluslararası koruma görevi yoktu.

---

## Temel ilke

**Geri gönderme yasağı:** hiç kimse işkenceye, insanlık dışı ya da onur kırıcı muameleye tabi tutulacağı veya ırkı, dini, tabiiyeti, belli bir toplumsal gruba mensubiyeti ya da siyasi fikirleri nedeniyle hayatının veya hürriyetinin tehdit altında olacağı yere gönderilemez (6458 m.4). Sınır dışı kararında bu, m.55/1-a engeli olarak somutlaşır. 

**Başvuru:** valiliklere bizzat; kolluğa yapılan başvuru derhâl valiliğe bildirilir; makul sürede kendiliğinden başvurana, geçerli neden açıklamak kaydıyla yasa dışı giriş/kalış nedeniyle cezai işlem yapılmaz; hürriyeti kısıtlananın başvurusu derhâl bildirilir, ama diğer adli ve idari işlemlerin uygulanmasını kendiliğinden engellemez. 

Statü türleri (mülteci, şartlı mülteci, ikincil koruma) ve tanımları 6458 m.61-63'tedir: Avrupa'da meydana gelen olaylar nedeniyle zulüm korkusu → mülteci (m.61); Avrupa dışındaki olaylar → şartlı mülteci, üçüncü ülkeye yerleştirilinceye kadar kalış (m.62); bunlara girmeyen ama geri gönderilirse ölüm cezası, işkence/insanlık dışı muamele ya da silahlı çatışmada ayrım gözetmeyen şiddet tehdidi altındaki kişi → ikincil koruma (m.63). Hariçte tutulma m.64 (Sözleşme 1F fiilleri; ikincil korumada ayrıca kamu düzeni/güvenliği tehlikesi). 

---

## Süreler ve dayanakları

| İşlem | Süre ve başlangıç | Merci | Dayanak |
|---|---|---|---|
| Hızlandırılmış değerlendirmede mülakat | Başvurudan en geç **3 gün** | Valilik | 6458 m.79/2  |
| Hızlandırılmış değerlendirmede karar | Mülakattan en geç **5 gün** | Valilik | 6458 m.79/2 |
| Uluslararası koruma kararlarına **idari itiraz** | Tebliğden **10 gün** (m.68, 72, 79 kararları hariç: onlara yalnız yargı yolu) | Uluslararası Koruma Değerlendirme Komisyonu | 6458 m.80/1-a  |
| **Kabul edilemezlik (m.72)** ve **hızlandırılmış değerlendirme (m.79)** kararlarına dava | Tebliğden **15 gün**; mahkeme **15 gün** içinde karar verir; karar **kesin** | Yetkili idare mahkemesi | 6458 m.80/1-ç, d |
| Diğer idari karar ve işlemlere dava (ör. esastan ret) | Tebliğden **30 gün** | Yetkili idare mahkemesi | 6458 m.80/1-ç |
| Başvuru sahibinin idari gözetimi | En çok **30 gün**; sulh ceza hâkimine başvuru, 5 gün, kesin | Sulh ceza hâkimi | 6458 m.68/5, 7  |
| Ülkede kalış | İtiraz ya da yargılama sonuçlanıncaya kadar kalışa izin verilir | — | 6458 m.80/1-e |

YUKK Uygulama Yönetmeliği m.101 aynı süreleri tekrarlar (m.72 ve m.79 kararlarına 15 gün; diğerlerine 30 gün). 

`legal_calculate_deadline` bu süreleri tanımıyor; elle hesapla, `legal_check_holiday`.

**Kanun yolu:** m.72 ve m.79 davalarında karar kesindir; diğer 6458 davalarında BİM kaldırıp yeniden karar verse de temyiz yoktur (2577 m.46/2-d, 7589). Sonraki yol AYM bireysel başvuru (tedbir) → `../../aym-aihm-basvuru/SKILL.md`. 

---

## Kontrol listesi

1. **Hangi karar?** Kabul edilemez (m.72), hızlandırılmış (m.79), esastan ret, statü sona erme/iptal, idari gözetim (m.68)? → süre ve merci bunlara göre değişir (10 / 15 / 30 gün).
2. **Kabul edilemezlik sebebi (m.72):** farklı gerekçe sunmadan aynı başvuruyu yenileme; muvafakatten sonra haklı neden göstermeden ayrı başvuru; ilk iltica ülkesinden (m.73) ya da güvenli üçüncü ülkeden (m.74) gelme. Yeni gerekçe var mı? 
3. **Hızlandırılmış değerlendirme sebebi (m.79/1):** koruma gerekçesine hiç değinmeme, sahte belge, kimlik belgesini kötü niyetle imha, **sınır dışı edilmek üzere idari gözetimde olma**, yalnız sınır dışını erteletme amacı, kamu düzeni tehlikesi ya da önceki sınır dışı, geri çekilmiş sayıldıktan sonra yeniden başvuru. **Refakatsiz çocuk** başvurusu hızlandırılamaz (m.79/4) 🔴. 3+5 günlük takvime uyuldu mu? 
4. **Mülakat ve avukat:** kayıttan itibaren 30 gün içinde bireysel mülakat; talep üzerine avukat gözlemci olarak katılabilir; yapılamazsa yeni tarih tebliğ edilir (arada en az 10 gün); kayıt alınabilir, her mülakatta tutanak ve bir örneği kişiye (m.75). Avukatla temsil; ücreti karşılayamayana yargı önündeki başvurularda adli yardım (m.81). Tercüman güvencesi m.75'te yok, ayrıca kontrol et `[incele]`. 
5. **Risk delili:** menşe ülke raporları (BMMYK, AİHM kararları), kişisel belgeler, tanık; risk "ciddi emare" düzeyinde mi? `[incele]`
6. **İdari gözetim:** yalnız başvuru yapmış olmak gözetim sebebi değildir; dört istisnai hâl (kimlik şüphesi, sınır kapısında alıkoyma, başvuru unsurlarının belirlenmesi, ciddi kamu düzeni tehlikesi); önce ikamet zorunluluğu/bildirim değerlendirilir; en çok 30 gün (m.68). 
7. **Sınır dışı ile ilişki:** uluslararası koruma başvuru sahibi ya da statü sahibi hakkında sınır dışı kararı **yalnız** m.54/1-(b), (d), (k) kapsamında işlemlerin her aşamasında alınabilir (m.54/2); diğer hâllerde son karardan sonra ve kalma hakkı yoksa (m.54/1-i). Başvurunun geri çekilmesi sınır dışı sebebidir → gönüllü dönüş baskısına karşı uyar 🔴. 
8. **Çalışma ve ikamet:** başvuru sahibi ve şartlı mülteci için çalışma izni istisnası (6735 m.16/1-f); mülteci ve ikincil koruma sahipleri uzun dönem ikamete geçemez (6458 m.42/2). 

### Geçici koruma (kısa)
Kitlesel olarak sınıra gelen ya da sınırı geçen, ülkesine dönemeyen yabancılara geçici koruma sağlanabilir; kabul, kalış, hak ve yükümlülükler Cumhurbaşkanınca çıkarılan **Geçici Koruma Yönetmeliği** ile düzenlenir (m.91). Geçici koruma kimliğinin iptali, il dışına çıkma izni, adres değişikliği ve gönüllü geri dönüş konuları yönetmelikte; yönetmelik metnini her seferinde çek `[doğrula]`.  Soorgla'da `law_no: "20146883"` (RG 22.10.2014/29153). Katalogda aynı numarayla iki kayıt var (statute_id 40488 — 66 madde, 19360 — 69 madde); madde çekerken `legal_get_statute_article_by_id` ile hangisinin güncel olduğunu karşılaştır.  RG başlık aramasında görünen son değişiklik: CB Kararı 10658, RG 28.11.2025 (m.27 sağlık hizmetleri; 01.01.2026'da yürürlük). İptal ve sona erme kuralını beceriye yazma; ilgili maddeyi her dosyada çekip oku.  Geçici koruma sağlananların çalışma izni ayrı yönetmelikle düzenlenir (Geçici Koruma Sağlanan Yabancıların Çalışma İzinlerine Dair Yönetmelik). 

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Hangi karar, ne zaman tebliğ edildi? Kararda "kabul edilemez" ya da "hızlandırılmış" ibaresi var mı? | 10/15/30 gün |
| Başvuru ne zaman, nereye yapıldı; mülakat ne zaman, hangi dilde? | Usul güvenceleri |
| Ülkesinde neyle karşılaştı, kimden, hangi tarihte? Belgeler? | Risk delili |
| Daha önce başka ülkede ya da Türkiye'de başvuru yaptı mı? | m.72 |
| Refakatsiz çocuk mu? Aile üyeleri? | m.79/4; aile başvurusu |
| Şu an idari gözetimde mi? | m.68, sulh ceza |
| Sınır dışı kararı da var mı? | 7 gün; m.54/2 |
| Geri çekme ya da gönüllü dönüş belgesi imzaladı mı? | m.54/1-i |

---

## İdare tarafı (valilik / il göç idaresi)

- Hızlandırılmış değerlendirmede 3+5 gün takvimine uy; refakatsiz çocuğu bu usule alma.
- Kabul edilemezlik ve ret kararlarında itiraz yolunu ve süresini tebligata yaz; avukatı olmayanı bilgilendir (m.72/3).
- Başvuru sahibini yalnız başvurusu nedeniyle gözetime alma; m.68/3'teki alternatifleri önce değerlendir ve yaz.
- Sınır dışı kararını m.54/2 dışında, başvuru sürerken alma.

---

## Komisyona itiraz iskeleti (10 gün)

```markdown
[TASLAK — avukat incelemesi bekliyor]

ULUSLARARASI KORUMA DEĞERLENDİRME KOMİSYONUNA
Gönderilmek üzere [___] VALİLİĞİNE (İl Göç İdaresi Müdürlüğü)

İTİRAZ EDEN: [ad, uyruk, YKN / başvuru no, adres]
VEKİLİ: [___]
İTİRAZ EDİLEN KARAR: [tarih, sayı] — [karar türü]
TEBLİĞ TARİHİ: [___]

AÇIKLAMALAR
1. Başvuru ve mülakat süreci: [___]
2. Kararın gerekçesi ve hatası: [___]
3. Menşe ülkedeki risk ve deliller: [___]
4. Usul eksiklikleri (tercüman, mülakat, bilgilendirme): [___]

HUKUKİ SEBEPLER: 6458 m.4, m.61-63, m.80; 1951 Cenevre Sözleşmesi; AİHS m.3
SONUÇ VE İSTEM: Kararın kaldırılarak [mülteci / şartlı mülteci / ikincil koruma] statüsü verilmesine karar verilmesini arz ederim.
[Tarih — imza]
```

İdare mahkemesindeki dava dilekçesi → `../../idare-davalari-imar/references/idari-dava-dilekcesi.md`; başlıkta "6458 m.80/1-ç uyarınca 15 günlük süre — ivedi" (m.72/79 kararlarında).

---

## soorgla çağrıları

```
legal_get_statute_article  law_no: "6458"  law_type: "Kanun"  article_no: "4" | "54" | "61" | "62" | "63" | "65" | "68" | "72" | "75" | "79" | "80" | "91"
legal_search_statute_semantic  mevzuat_no: "21460"  sorgu: "<ör. kabul edilemez başvuru kararına karşı on beş gün içinde idare mahkemesi>"
legal_search_statute_semantic  sorgu: "Geçici Koruma Yönetmeliği <konu>"
legal_search_cases  mahkeme: "anayasa"  sorgu: "<ör. uluslararası koruma başvurusu sınır dışı kötü muamele yasağı etkili başvuru>"  tarih_baslangic: "2023-01-01"
legal_search_cases  mahkeme: "aihm"  sorgu: "<ör. Turkey expulsion asylum Article 3>"   # kapsam ölçülmedi
```

İdare mahkemesi kararları soorgla'da yok; m.72/79 davaları idare mahkemesinde kesinleştiği için içtihat yalnız AYM ve AİHM'den kurulabilir. AİHM'de Türkiye aleyhine geri gönderme ve idari gözetim kararları var (M.N. ve Diğerleri, G.B. ve Diğerleri, Akkad, Amerkhanov). 

---

## Çıktı iskeleti

```markdown
## Uluslararası koruma değerlendirmesi — [ad, uyruk] — [tarih]
| Karar | Tebliğ | Yol | Süre | Son gün | Merci |
### Karar türü ve gerekçesi
### Risk ve deliller (m.4)
### Usul güvenceleri (mülakat, tercüman, çocuk)
### İdari gözetim / sınır dışı bağlantısı
### Öneri
```

---

## Sık hatalar

- 🔴 Kabul edilemezlik ya da hızlandırılmış değerlendirme kararına önce Komisyona itiraz edip 15 günlük dava süresini kaçırmak (bu kararlara yalnız yargı yolu).
- 🔴 Esastan ret için 10 günlük itiraz ile 30 günlük dava süresini karıştırmak.
- 🟠 Refakatsiz çocuğun başvurusunun hızlandırılmış usulle reddine itiraz etmemek.
- 🟠 Başvuru sahibinin idari gözetiminde 6 ay kuralını (m.57) uygulamak (m.68: 30 gün).

---

