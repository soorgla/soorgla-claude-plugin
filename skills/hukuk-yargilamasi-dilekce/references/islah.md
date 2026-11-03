# Islah dilekçesi

## Ne zaman kullanılır
Bir tarafın yaptığı usul işlemini kısmen ya da tamamen düzeltmesi: en sık, bilirkişi raporundan sonra **dava değerinin artırılması** (kısmi ıslah); ayrıca iddia/savunmanın genişletilmesi yasağını aşmak, tamamen ıslahla davayı baştan kurmak.

31.07.2026'dan sonra açılan kısmi davada talep önce HMK m.109/4'teki **bir defalık artırımla** yükseltilir (7589; belirsiz alacak davası kalktı). 31.07.2026'dan önce açılmış belirsiz alacak davasında talebin artırılması HMK m.107/2'deki iki haftalık kesin süreyle yapılır; ıslah hakkını tüketmeden bu yolu kullanmak çoğu zaman daha iyidir `[incele]`.

---

## Süre ve sınır tablosu

| Kural | Dayanak | Not |
|---|---|---|
| Her taraf **aynı davada bir kez** ıslah yapabilir | HMK m.176/2 | Islah hakkı kullanılınca biter; kullanıcıyı uyar. |
| Islah **tahkikatın sona ermesine kadar** yapılabilir | HMK m.177/1 | Tahkikatın bittiği HMK m.184/2 ile taraflara tefhim edilir; tarihi duruşma tutanağından al. |
| **Bozma / kaldırma sonrası** da ıslah mümkün | HMK m.177/2 (7251/18 ile ek, 2020) | İlk derece mahkemesi tahkikata ilişkin bir işlem yaparsa tahkikat bitene kadar; ancak bozmaya uymakla oluşan hukuki durum ortadan kaldırılamaz. **Eski YAML bu fıkrayı bilmiyordu.** |
| Sözlü ya da yazılı | HMK m.177/3 | Duruşma dışında ya da karşı taraf yokken yazılı talep karşı tarafa haber amaçlı bildirilir. |
| **Tamamen ıslahta yeni dava dilekçesi: bir hafta** | HMK m.180 | Bildirimden itibaren bir haftada yeni dilekçe verilmezse ıslah hakkı kullanılmış sayılır, ıslah yapılmamış gibi devam edilir. |
| Islah teminatı: **bir hafta** | HMK m.178/1 | Islah yüzünden geçersizleşen işlemlerin giderleri ve karşı tarafın zararı için hâkimin takdir ettiği teminat bir haftada yatırılmazsa **ıslah yapılmamış sayılır**. Bu, harçtan ayrıdır; kısmi ıslahta (yalnız değer artırımı) genelde teminat istenmez `[incele]`. |
| Islahın etkisi | HMK m.179 | İkrar, tanık ifadesi, bilirkişi raporu, keşif ve isticvap tutanakları ıslahla geçersiz kılınamaz. |
| Islah harcı | 492 s. Harçlar Kanunu m.30; HMK m.181 | Artırılan kısım üzerinden peşin harç tamamlanır; `legal_calculate_court_fee` `pesin_harc` ile hesapla. Harçlar K. m.30 "noksan değer üzerinden peşin karar ve ilam harcı tamamlanmadıkça davaya devam olunmaz" der; ıslaha uygulanması uygulamadır `[incele]`. Kısmen ıslahta işlemi yapmak için **bir hafta** verilir (HMK m.181). |

## Faiz ve zamanaşımı (eski YAML'daki kural belirsizdi)
- Eski YAML: "kural olarak ıslah edilen kısma ıslah tarihinden faiz; temerrüt önceyse olay tarihinden". Bu bir kanun kuralı değil, içtihattır ve son yıllarda değişti. Bağlayıcı kural: **Yargıtay İçtihadı Birleştirme Büyük Genel Kurulu, 24.05.2019, E. 2017/8, K. 2019/3** — "Bir miktar para alacağının faizi ile birlikte tahsiline karar verilmesinin talep edildiği kısmî davada, dava konusu miktarın kısmî ıslahla faiz talebi belirtilmeksizin arttırılması hâlinde, arttırılan miktar bakımından **dava dilekçesindeki faiz talebine bağlı olarak** faize hükmedilecektir." Gerekçe: kısmi ıslahla miktar artırımı yeni ya da ek dava değildir. Faiz başlangıcını yine dilekçede açıkça yaz.
- **Islahla artırılan kısımda zamanaşımı (kısmi dava) — düzeltme:** eski metin 6. HD'nin Anayasa m.36'ya dayandığını söylüyordu; okunan kararlarda **çoğunluk** hâlâ yerleşik uygulamayı sürdürüyor: kısmi ıslahla artırılan kısım için zamanaşımı **ıslah tarihine göre** hesaplanır ve dolmuşsa o kısım reddedilir (Yargıtay 6. HD, E. 2024/2343, K. 2025/2983, 18.09.2025, oy çokluğu; 2. HD, E. 2024/9036, K. 2024/9932, 12.12.2024, oy çokluğu). YİBK 24.05.2019 (ıslah ek dava değildir) ve AYM bireysel başvuru kararlarına (ör. G.D., B. No: 2016/9312, 27.11.2019; Ç.A., B. No: 2019/430, 23.03.2023 — mahkemeye erişim hakkı ihlali) dayanan "zamanaşımı ilk dava tarihinde tüm alacak için kesilir" görüşü yalnız **karşı oylarda**. Kısmi davada zamanaşımı riski varsa ıslahı süre dolmadan yap ya da belirsiz alacak koşullarını değerlendir; savunmada AYM kararlarını ileri sürmeden önce künyelerini `legal_search_cases(mahkeme: "anayasa")` ile bulup tam metnini oku.
- Dilekçede faiz türünü ve başlangıcını **açıkça** yaz; "yasal faiz" mi, "avans faizi" mi `legal_get_legal_interest_rates` ile seç, oranı yazma.

---

## Görüşme soruları (eski `data_schema`)
1. Mahkeme ve esas no? — `court_name`, `file_number`
2. Taraflar (müvekkil davacı mı davalı mı)? — `plaintiff_info`, `defendant_info`
3. Bu davada daha önce **ıslah yapıldı mı**? (sizin tarafınızdan)
4. Tahkikat bitti mi? Son duruşma tutanağı ne diyor? Bozma/kaldırma sonrası mı?
5. Dava açılış değeri, bilirkişi hesabı ve fark — `financial_calculations` (`initial_claim`, `expert_calculation`, `increase_amount`)
6. Bilirkişi raporu tarihi ve tebliğ tarihi — `report_date`
7. Belirsiz alacak davası mı, kısmi dava mı?
8. Artırılan kısım için faiz türü ve başlangıç tarihi; temerrüt (ihtar) tarihi — `interest_request`
9. Kısmi mi, tamamen ıslah mı? Tamamen ise yeni dava dilekçesi hazır mı?

## soorgla çağrıları
```
legal_get_statute_article law_no: "6100" article_no: "176" | "177" | "178" | "179" | "180" | "181" | "107"
legal_calculate_court_fee harc_turu: "pesin_harc" deger: <artırılan tutar>
legal_get_legal_interest_rates
legal_search_cases sorgu: "ıslah ile artırılan kısma dava dilekçesindeki faiz talebine bağlı olarak faiz yürütülmesi" mahkeme: "yargitay" tarih_baslangic: <son 3 yıl>
legal_search_cases sorgu: "içtihadı birleştirme ıslah faiz başlangıcı" daire: "Hukuk Genel Kurulu"
legal_get_case_document belge_id: <seçilen karar>
```

## Dilekçe iskeleti (eski `ui_config`: başlık → esas no → taraflar → konu → uyarı kutusu → hesap tablosu → açıklamalar → hukuki sebepler → sonuç)
```markdown
[YER] [__]. [MAHKEME] MAHKEMESİ'NE
                                                    DOSYA NO: [___] E.
DAVACI : [___]
VEKİLİ : Av. [___]
DAVALI : [___]
KONU : HMK m.176 vd. uyarınca davamızın kısmen ıslahı ile dava değerinin [___] TL artırılarak toplam [___] TL üzerinden hüküm kurulması talebidir.

AÇIKLAMALAR :
1. Davamız [tarih]'de [___] TL değer üzerinden açılmıştır.
2. Dosyaya sunulan [tarih] tarihli bilirkişi raporunda alacak [___] TL hesaplanmıştır (rapor tebliğ: [___]).
3. Değer artırım hesabı:
   | Dava açılış değeri | [X] TL |
   | Bilirkişi hesabı   | [Y] TL |
   | Islah edilen fark  | [Y − X] TL |
4. Islah edilen kısım için harç tamamlanmış / tamamlanacaktır.
5. Artırılan kısma [faiz türü] faizinin [başlangıç] tarihinden itibaren yürütülmesi talep edilmektedir. [incele]

HUKUKİ SEBEPLER : HMK m.176, 177, [___]
SONUÇ VE İSTEM : Islah talebimizin kabulü ile [faiz] dâhil toplam [___] TL'nin davalıdan tahsiline, yargılama giderleri ve vekâlet ücretinin davalıya yükletilmesine karar verilmesini saygıyla arz ve talep ederim. [TARİH] [İmza]
```
Uyarı satırı (iç not, dilekçeye girmez): "Aynı davada ıslah bir kez yapılabilir (HMK m.176/2)."

## Sık hatalar
- 🔴 Tahkikat bittikten sonra ıslah (bozma sonrası m.177/2 hâli hariç).
- 🔴 Islah hakkı daha önce kullanılmış.
- 🟠 Harç tamamlanmamış; süre verildiyse kaçırılmış.
- 🟠 Faiz başlangıcı yazılmamış ya da içtihat sabit kural gibi yazılmış.
- 🟡 Kısmi davada m.109/4 artırımı (ya da eski davalarda m.107/2 yolu) varken ıslah hakkı tüketilmiş.
- 🟠 31.07.2026 sonrası açılan dava "belirsiz alacak" diye kurulmuş (HMK m.107 kalktı).
