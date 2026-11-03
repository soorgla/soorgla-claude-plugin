# Ceza mevzuatı değişiklik takibi — yargı paketleri ve lehe kanun

## Ne zaman kullanılır
- "Yeni yargı paketi dosyamı etkiler mi?", "kanun değişti, lehe olan uygulanır mı?", "uzlaştırma kapsamından çıkarıldı mı?".
- Her ceza analizinin başında: suç tarihi ile aşağıdaki değişikliklerin yürürlük tarihlerini karşılaştır.
- Becerideki bir bilginin güncelliğinden şüphelenildiğinde (yeni kanun çıkmış olabilir).

Upstream `regulatory-legal/reg-feed-watcher` fikri uyarlandı: yeni RG kayıtlarını tara, önem süzgecinden geçir, dosya etkisini tek satırla yaz.

---

## Takip yöntemi

1. **RG taraması:** `legal_search_official_gazette` `query: "Türk Ceza Kanunu"` `document_type: "kanun"` `date_from: "<son tarama>"` `sort_by: "date_desc"`; ayrıca `query: "Ceza Muhakemesi Kanunu"`, `"Çocuk Koruma Kanunu"`, `"Ceza ve Güvenlik Tedbirlerinin İnfazı"`. Başlık araması (`search_in: "title"`) torba kanunları kaçırır — torba kanunlar çoğu zaman "Bazı Kanunlarda Değişiklik" başlığı taşır; tam metin araması kullan.
2. **Madde metni:** değişen maddeyi `legal_get_statute_article` ile çek; metindeki "(Değişik/Ek: gg/aa/yyyy-KanunNo/madde md.)" notuna bak. soorgla madde metinleri 7593'e kadar işlenmiş görünüyor (TCK 31/4), ancak **madde tarihçesi** CMK için 2014'te duruyor.
3. **Geçiş maddesi:** değiştiren kanunun geçici maddelerini RG tam metninden oku (CMK geçici m.7, m.8; 7589 geçici m.1; 5235 geçici m.7).
4. **Lehe kanun:** maddi ceza hükümlerinde suç tarihindeki ve sonraki kanun ayrı ayrı uygulanır, lehe olan seçilir (TCK m.7/2); usul hükümleri kural olarak derhâl uygulanır — ancak CGK, uzlaştırmayı muhakemeyi engellediği için usul, ceza ilişkisini sona erdirdiği için maddi ceza hukuku kurumu sayar (karma nitelik) ve sonradan gelen lehe uzlaştırma hükmünü TCK m.7 uyarınca geçmişe uygular (Yargıtay CGK, E. 2017/375, K. 2021/35, 16.02.2021). Şikâyet, önödeme ve HAGB'nin de karma kurum sayıldığı daha yeni bir CGK kararı arama özetinde görüldü (CGK, E. 2024/175, K. 2025/5, 08.01.2025 — kullanmadan önce tam metnini oku) `[incele]`.

---

## 2023-2026 değişiklik tablosu (bu becerinin dosyalarına işlenenler)

| Kanun (RG) | Konu | Etkilenen dosya | Dayanak |
|---|---|---|---|
| 7445 (2023) | TCK 191: erteleme kararının kolluğa bildirimi; denetimli serbestlik en az 1 yıl, uzatma, yılda iki test | `uyusturucu-suclari.md` | |
| 7499 (12.03.2024) | CMK 231/6: HAGB'de sanığın kabulü şartı kalktı (1.6.2024 öncesi kararlarda sürer — geçici m.6/2-d); 231/12: HAGB'ye karşı istinaf; 231/14 kapsam dışı suçlar | `yaptirimlar-hagb-erteleme.md` | |
| 7528 (2024) | CMK 100/3-k: öğretmene karşı kasten yaralama katalog | `sorusturma-evresi-delil-ve-ifade.md` | |
| 7531 (14.11.2024) | TCK 73/2 hakarette 2 yıl üst sınır; TCK 75/6 hakaretin (125/2 vb.) önödemeye alınması; CMK 253/3 125/2 uzlaştırma dışı; 253/4 teklif cevabı 7 gün; 254/2 kovuşturmada uzlaşmada düşme/durma; CMK geçici m.7 | `sikayet-uzlastirma-onodeme-zamanasimi.md`, `hurriyet-ve-serefe-karsi-suclar.md` | |
| 7571 (25.12.2025) | TCK 32/2 ve 57 (akıl hastaları güvenlik tedbiri); 75/6 hakaret (125/3-a hariç) önödeme; 89 cezaları artırıldı; 155/3 motorlu taşıt; 170; 220; 223 yeniden yazıldı; CMK 128/A hesap askıya alma; 253/1-b-7 (155/3 hariç), 253/3 hakaretin tamamı uzlaştırma dışı + önödeme birlikte işlenme kuralı; CMK geçici m.8; 5235 m.12 nitelikli dolandırıcılık ağır ceza görevinden çıktı (5235 geçici m.7); 5275 geçici m.10/6; 1136 disiplin hükümleri | `malvarligi-suclari.md`, `hayata-ve-vucuda-karsi-suclar.md`, `orgut-teror-ve-devlet-guvenligi.md`, `sikayet-uzlastirma-onodeme-zamanasimi.md`, `suc-vasfi-ve-genel-hukumler.md` | |
| 7589 (31.07.2026) | TCK 158/4 hesap/kart kullandırmada yarı indirim (geçici m.1/6-7); CMK 80/2-4 inceleme sonuçlarının kaydı ve imhası; CMK 231/5-14 HAGB yeniden yazıldı (231/11 yükümlülük ihlalinde yeni hüküm kurma ve itiraz; 231/12 istinaf metni yenilendi; kabul şartı 7499'dan beri yok); CMK 247/3 kaçak sanık; CMK 308 Başsavcılık itirazı ve istem (geçici m.1/8) | `malvarligi-suclari.md`, `yaptirimlar-hagb-erteleme.md`, `sorusturma-evresi-delil-ve-ifade.md` | |
| 7593 (18.08.2026) | TCK 31/2-3 aralıkları, 31/4 yeni; TCK 233 cezaları ve 233/4; 6136 m.13/A; CMK 174/1-e (SİR'siz iddianame iadesi); 5395 m.5/A yönlendirme tedbirleri, 23/2-3 çocuklarda HAGB, 35/3 SİR zorunluluğu, 45/5 tazyik hapsi; "adli süreçteki çocuk" terimi; 5275 m.107/5; 5326 m.43/C (bıçak, 01.12.2026) | `adli-surecteki-cocuk.md`, `cinsel-ve-aile-duzeni-suclari.md`, `ceza-hesaplama.md` | |
| Yargıtay BGK 2026/1 (RG 30.06.2026) | Ceza daireleri iş bölümü; yayımı izleyen ay başından uygulanır | SKILL.md Adım 3 | |

**Son tarama:** 31.10.2026 — 7593'ten sonra (7596, 27.10.2026 dahil) TCK veya CMK'yı değiştiren kanun bulunmadı; `legal_search_official_gazette` 89 sonucun ilk 20'si incelendi. Özel kanunlardaki yeni suç tipleri: **7592** (RG 09.08.2026, 33335) 2547 sayılı Kanuna **ek m.47** (tez, makale vb. çalışmayı başkası adına yapma/aracılık ve bunları kullanarak derece alma — adli para cezası; tüzel kişiler için TCK m.60) ve **ek m.48** (mevzuata aykırı yükseköğretim programı/kurumu açma-işletme ve tanıtımı — hapis ve adli para cezası; diploma/mezuniyet belgesi sahteciliği TCK m.204'e göre) ekledi; TCK ve CMK'yı değiştirmedi. Bu suçlarda ceza aralığını her seferinde RG metninden ya da `legal_get_statute_article` (2547, "ek 47"/"ek 48") ile çek. **7590** (RG 31.07.2026, 33326) yalnız idari para cezaları içeriyor; hapis/adli para cezası ya da TCK-CMK değişikliği yok.

---

## Önem süzgeci

| Değişiklik türü | Önem | Eylem |
|---|---|---|
| Uzlaştırma / önödeme / şikâyet kapsamı | 🔴 | Derdest her dosyada usul ön kontrolünü yeniden yap; geçiş maddesine bak |
| Ceza aralığı artışı | 🟠 | Suç tarihi öncesi fiillere uygulanmaz; lehe kanun karşılaştırması |
| Ceza aralığı indirimi, yeni indirim nedeni (ör. 158/4) | 🔴 | Kanun yolundaki ve infazdaki dosyalarda uyarlama |
| Görevli mahkeme değişikliği | 🟠 | Geçiş maddesi (ör. 5235 geçici m.7) |
| HAGB, erteleme, infaz rejimi | 🟠 | Hüküm aşamasındaki dosyalar; infaz → `ceza-ve-infaz-dilekce` |
| Daire iş bölümü | 🟡 | Emsal aramasında daire filtresi |

---

## Çıktı iskeleti

```markdown
## Değişiklik etkisi — [dosya, suç tarihi]
| Değişiklik | Yürürlük | Suç tarihine göre uygulanır mı | Lehe mi | Geçiş maddesi | Önem |
### Yapılacaklar (uyarlama talebi, usul ön kontrolünün yenilenmesi) [incele]
```

---

## Sık hatalar

- 🔴 Yalnız başlık aramasıyla "yeni kanun yok" sonucuna varmak (torba kanunlar).
- 🔴 Geçiş maddesini okumadan yeni uzlaştırma/önödeme kuralını derdest dosyaya uygulamak.
- 🟠 Madde tarihçesi aracının boş ya da eski dönmesini "değişiklik yok" diye okumak.

---

## Kaynak ve uyarlama

- YAML karşılığı yok; sıfırdan kuruldu (upstream `regulatory-legal/reg-feed-watcher` iş akışı fikri).
