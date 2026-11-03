# Takip yolu seçimi ve takip talebi

**Ne zaman kullanılır:** alacaklı (ya da vekili) takip başlatmak istiyor; elindeki belgeye göre hangi takip yolunun seçileceği, takip talebine ne yazılacağı, zamanaşımı ve faiz hesabı soruluyor. Takip başladıktan sonraki itiraz aşaması → `odeme-emri-itiraz-ve-sonrasi.md`.

Temel ilke: yol seçimi takibin kaderini belirler. Kambiyo senedi elde varken genel haciz yoluna gitmek borçluya 7 günlük ve icra dairesine yapılan basit bir itirazla takibi durdurma imkânı verir; ilam varken ilamsız takip yapmak gereksiz itiraz riskidir. Ama yanlış nitelendirilmiş bir "kambiyo senedi" ile kambiyo yoluna gitmek de 5 günlük şikâyetle takibin iptaline yol açar.

---

## Yol seçimi tablosu

| Alacaklının elindeki | Takip yolu | Ödeme/icra emri | Borçlunun itiraz yolu ve süresi | Dayanak |
|---|---|---|---|---|
| Mahkeme ilamı ya da ilam niteliğindeki belge | İlamlı takip | İcra emri | İcranın geri bırakılması için 7 gün içinde **icra mahkemesine** (zamanaşımı, itfa, imhal) | İİK m.24 vd., m.33 |
| Çek, bono, poliçe (kambiyo vasfı tam, vadesi gelmiş) | Kambiyo senetlerine özgü haciz yolu | Ödeme emri (10 gün ödeme) | Borca, imzaya, yetkiye itiraz ve "kambiyo senedi değil" şikâyeti **5 gün içinde icra mahkemesine** | İİK m.167-170 |
| Fatura, cari hesap, sözleşme, senetsiz alacak | Genel haciz yoluyla ilamsız takip | Ödeme emri | **7 gün içinde icra dairesine** itiraz; itiraz takibi durdurur | İİK m.58 vd., m.62, m.66 |
| Kira alacağı / tahliye | Kiralananın tahliyesi takibi | Tahliye ihtarlı ödeme emri / tahliye emri | → `kira-tahliye-takibi.md` | İİK m.269 vd. |
| Taşınır ya da taşınmaz rehni, ipotek | Rehnin paraya çevrilmesi yoluyla takip | Ödeme emri / icra emri | Taşınır rehninde ödeme süresi 15 gün, itiraz 7 gün (m.146); ipotekte icra emri, ödeme süresi 30 gün (m.149); diğer türler `[incele]` | İİK m.145 vd. |
| İflasa tabi borçlu (tacir) ve alacaklı iflas istiyor | İflas yoluyla takip | Ödeme emri (iflas ihtarlı) | → `iflas-ve-konkordato.md` | İİK m.155-156 |

**Seçimlik hak:** rehinli alacakta önce rehne başvurma kuralı (İİK m.45: borçlu iflasa tabi olsa bile yalnız rehnin paraya çevrilmesi; rehin yetmezse kalan için haciz ya da iflas). İstisnalar: konut finansmanı ve TOKİ'nin rehinli alacakları, kambiyo senedine dayalı takip (m.167), ipotekli faiz ve yıllık taksit alacakları. İflasa tabi borçluda haciz/iflas seçimi bir kez harçsız değiştirilebilir (m.43).

---

## Süre tablosu (alacaklı tarafı)

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Haciz isteme: **1 yıl** | Ödeme emrinin tebliği | İİK m.78/2 | Süre içinde istenmezse dosya işlemden kaldırılır; yenileme ilamsız takipte yeni harç doğurur. 🟠 |
| Satış isteme: hacizden itibaren **1 yıl** (taşınır/taşınmaz ayrımı yok) | Haciz tarihi | İİK m.106 (7343/9) | → `haciz-satis-istihkak-ve-sira-cetveli.md`. Satış giderleri peşin yatırılmazsa talep vaki olmamış sayılır. |
| İflas isteme: **1 yıl** | İflas yoluyla takipte ödeme emrinin tebliği | İİK m.156 son fıkra | |
| İtirazın kaldırılması **6 ay** / itirazın iptali **1 yıl** | İtirazın alacaklıya tebliği | İİK m.68/1, m.67/1 | → `odeme-emri-itiraz-ve-sonrasi.md` |

---

## Zamanaşımı kontrolü (kambiyo)

- **Çek:** hamilin düzenleyen ve cirantalara karşı başvuru hakları ibraz süresinin bitiminden itibaren **3 yıl**. İbraz süresi: düzenlendiği yerde ödenecekse **10 gün**, başka yerde ödenecekse **1 ay**; yurt dışında düzenlenende aynı kıtada 1 ay, ayrı kıtada 3 ay; süre düzenleme tarihinin ertesi günü başlar (TTK 796).
- **Bono / poliçe:** kabul edene (bonoda düzenleyene) karşı vadeden itibaren **3 yıl**; hamilin cirantalara karşı protesto ya da "gidersiz iade" kaydında vadeden itibaren **1 yıl**; cirantaların birbirine karşı **6 ay**. Bonoya poliçenin zamanaşımı hükümleri (m.749-751) TTK m.778/1-h atfıyla uygulanır.
- Kambiyo zamanaşımı dolmuşsa senet **adi senet** olarak genel haciz yoluyla takibe konu olabilir; sebepsiz zenginleşme talebi (TTK m.732) `[incele]`.
- Zamanaşımı itirazını borçlu kambiyo takibinde 5 gün içinde icra mahkemesine bildirir (m.168/5); ilamlı takipte m.33. İcra dairesi zamanaşımını re'sen dikkate almaz `[doğrula]`.

Eski YAML "Çek 3 yıl, Bono 3 yıl" diyordu: düzenleyene karşı doğru, ama cirantalara karşı bonoda 1 yıl ve 6 ay süreleri eksikti.

---

## Takip talebi kontrol listesi

1. **Taraflar:** alacaklı ve borçlunun adı, T.C. kimlik no / vergi no, adres. Tüzel kişi borçluya tebligat e-tebligatla yapılır (Tebligat K. m.7/a).
2. **Alacak:** asıl alacak, işlemiş faiz (başlangıç, bitiş, oran, dayanak), masraf; yabancı para alacağında Türk lirası karşılığı ve kur seçimi (`legal_get_exchange_rate`). Fazla faiz talebi borçlu itirazında inkâr tazminatı hesabını etkiler (m.67 son fıkra: talep esas alınır).
3. **Faiz:** sözleşme faizi yoksa yasal faiz ya da ticari işte avans faizi (3095 m.1-2). Oranı **beceriye yazma**; `legal_get_legal_interest_rates` ile dönem dönem çek. Eski YAML'daki sabit avans faizi oranı bayattı (RAPOR §8).
4. **Belge:** takibin dayanağı (fatura, sözleşme, senet aslı, ilam). Kambiyo takibinde takip talebine senedin aslı ve borçlu sayısı kadar onaylı örneği eklenir (m.167/2).
5. **Yetki:** borçlunun yerleşim yeri, sözleşmenin ifa yeri, kambiyo senedinde ödeme yeri. Para ve teminat borcu takibinde HMK yetki kuralları kıyasen uygulanır; ayrıca **sözleşmenin yapıldığı yer** icra dairesi de yetkilidir (İİK 50/1). Yetkisiz dairede takip borçlunun yetki itirazına açıktır; itiraz esasa ilişkin itirazla birlikte yapılır (50/2).
6. **Takip yolu ve örnek numarası** yukarıdaki tabloya göre.
7. **Harç:** icraya başvurma ve peşin harç `legal_get_social_parameters` (`tur: "harc_icra_basvurma"`); tahsil harcı `legal_calculate_court_fee` (`icra_tahsil_haciz_once` vb.). Tutar yazma.
8. **Mükerrer takip:** aynı alacak için başka takip var mı? 12. HD mükerrerliği şikâyetle incelenebilir sayıyor.
9. **Malvarlığı sorgusu:** ödeme süresi geçtikten (itiraz varsa kaldırıldıktan) sonra alacaklı haciz talep etmeden UYAP üzerinden borçlunun mal, hak ve alacaklarını sorgulayabilir ve elektronik haciz isteyebilir.
10. **İhtiyati haciz gerekir mi?** Borçlu mal kaçırıyorsa takipten önce → `menfi-tespit-istirdat-ve-ihtiyati-haciz.md`.

---

## Görüşme soruları

1. Alacağın kaynağı nedir (ilam, çek, bono, fatura, sözleşme, kira, kredi)? Belgenin aslı sizde mi?
2. Vade / temerrüt tarihi? Borçluya ihtar çekildi mi?
3. Borçlu gerçek kişi mi, şirket mi? Tacir mi? Adresi ve vergi/T.C. no?
4. Kambiyo senedinde: keşide yeri ve tarihi, ödeme yeri, ciro zinciri, karşılıksız şerhi tarihi?
5. Faiz konusunda sözleşmede hüküm var mı? Yabancı para mı?
6. Rehin, ipotek ya da kefil var mı?
7. Borçlunun bilinen malvarlığı (taşınmaz, araç, banka, maaş)?
8. Daha önce aynı alacak için takip ya da dava açıldı mı?
9. Borçlu konkordato ya da iflas sürecinde mi? (mühlet varsa takip yapılamaz → `iflas-ve-konkordato.md`)

## soorgla çağrıları

```
legal_get_statute_article law_no: "2004" article_no: "33" | "58" | "62" | "68" | "78" | "106" | "167" | "168" | "170"
legal_get_statute_article law_no: "6102" article_no: "749" | "814" | "796" | "778"
legal_get_legal_interest_rates # yasal / avans faizi, dönemli
legal_get_exchange_rate # döviz alacağı
legal_get_social_parameters tur: "harc_icra_basvurma"
legal_calculate_court_fee harc_turu: "icra_tahsil_haciz_once" deger: <tutar>
legal_search_cases mahkeme: "yargitay" daire: "12. Hukuk Dairesi" tarih_baslangic: <son 3 yıl>
    sorgu: "<ör. çekte ibraz süresi geçirilmesi kambiyo vasfını kaldırır mı>"
legal_search_cases mahkeme: "bam" sorgu: "<olay>"
```

## Çıktı iskeleti

```markdown
## Takip yolu değerlendirmesi: [alacaklı] / [borçlu] — [tarih]
### Sonuç (önerilen yol ve tek cümle neden)
### Belge ve zamanaşımı
| Belge | Kambiyo vasfı | Vade/ibraz | Zamanaşımı son günü | Durum |
### Kapak hesabı
| Kalem | Dönem | Oran (araçtan) | Tutar [doğrula] |
### Takip talebi alanları (eksikler [___])
### Riskler (itiraz senaryosu, yetki, mükerrerlik)
### Harç (araçtan)
### Eksik bilgi
```

## Sık hatalar

- Kambiyo vasfı eksik senetle (ör. düzenleme tarihi yok, bono kelimesi yok) kambiyo yoluna gitmek → 5 gün içinde "kambiyo senedi değil" şikâyetiyle takip iptal edilir.
- Elde ilam varken ilamsız takip yapmak.
- Faiz oranını ve başlangıcını belgesiz yazıp itiraz edilince inkâr tazminatının fazla istenen kısım için alınamaması.
- Haciz isteme süresini (1 yıl) ve satış isteme süresini kaçırmak.
- Konkordato mühleti içindeki borçluya takip açmak (m.294).
