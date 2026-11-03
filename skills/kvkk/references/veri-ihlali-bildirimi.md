# Veri ihlali ve bildirim

## Ne zaman kullanılır
- Kişisel veri yetkisiz kişilerin eline geçti ya da geçmiş olabilir: siber saldırı, fidye yazılımı, yanlış alıcıya e-posta, kayıp/çalıntı cihaz, yetkisiz çalışan erişimi, açık bırakılan veritabanı, veri işleyende yaşanan olay.
- Kurul ihlal bildirimi sonrası bilgi istedi → ayrıca `kurul-sureci-ve-yaptirimlar.md`.

İhlal anında ilk iş **zaman çizelgesi** ve **öğrenme anı**dır; bildirim süreleri buradan işler.

---

## Süreler ve dayanakları

| Süre | Başlangıç | Dayanak | Not |
|---|---|---|---|
| Kurula ve ilgili kişilere bildirim: **en kısa sürede** | İşlenen verinin kanuni olmayan yollarla başkalarınca elde edilmesi (öğrenme) | 6698 m.12/5 | Kurul gerekirse ihlali internet sitesinde ilan edebilir. |
| Kurula bildirimde azami süre: **72 saat** (uygulamada) | Veri sorumlusunun ihlali öğrenmesi | Kurulun ihlal bildirimine ilişkin kararı (yaygın olarak 24.01.2019 t. 2019/10 s. karar olarak bilinir) | Gecikirse gecikme gerekçesi de bildirilir `[model bilgisi — doğrulayın]`. |
| İlgili kişilere bildirim: makul olan en kısa sürede | Etkilenenlerin belirlenmesi | Aynı karar; bildirimin asgari unsurları Kurulun 18.09.2019 t. 2019/271 s. kararında | Doğrudan (iletişim adresine); ulaşılamıyorsa web sitesinde yayım gibi uygun yöntemle. İçerik 2019/271'deki asgari unsurları taşımalı. |
| Veri işleyenin veri sorumlusuna bildirimi | Sözleşmede | → `veri-isleme-sozlesmesi.md` | m.12/2 müşterek sorumluluk. |
| Kurulun bilgi-belge istemine cevap: **15 gün** | Talebin tebliği | 6698 m.15/3 | |

`legal_calculate_deadline` bu süreleri hesaplamaz. 72 saat **saat** hesabıdır; hafta sonu ve tatil uzatmaz `[incele]`.

---

## Kontrol listesi

1. **Kişisel veri mi?** Yalnız anonim ya da yalnız tüzel kişi verisi ise KVKK bildirimi gerekmeyebilir; ama "anonim" iddiasını test et (yeniden kimliklendirme mümkün mü).
2. **Ne oldu, ne zaman öğrenildi?** Saat saat zaman çizelgesi: olayın başlangıcı, tespiti, veri sorumlusunun öğrenmesi, kontrol altına alınması.
3. **Hangi veriler, kaç kişi, hangi gruplar?** Özel nitelikli veri (sağlık, biyometrik, ceza mahkûmiyeti) varsa risk 🔴.
4. **Muhtemel sonuçlar**: kimlik hırsızlığı, dolandırıcılık, ifşa, ayrımcılık.
5. **Alınan ve alınacak tedbirler**: erişimin kesilmesi, parola sıfırlama, adli bilişim, delil koruma (logları silme!).
6. **Veri işleyen kaynaklı mı?** Sözleşmedeki bildirim ve iş birliği yükümlülüklerini işlet.
7. **Kurul bildirimi**: Kurumun ihlal bildirim formu alanlarını doldur (aşağıdaki iskelet). Formun güncel sürümünü ve gönderim kanalını (çevrim içi form, KEP, posta) beceride sabitleme; kullanıcıdan Kurum sitesindeki güncel formu iste ya da `legal_search_admin_guidance` (`kurum: "Kişisel Verileri Koruma Kurulu"`, `sorgu: "veri ihlal bildirim formu"`) ile ara; bulamazsan `[ARAŞTIRMA GEREKLİ: güncel ihlal bildirim formu ve kanalı]`. Aşağıdaki iskelet alan listesidir, resmî form değildir.
8. **İlgili kişi bildirimi**: anlaşılır dil, ne oldu, hangi veriler, olası sonuçlar, alınan tedbirler, kişinin yapabilecekleri, iletişim.
9. **Ceza yönü**: saldırgan hakkında TCK 136 (verileri hukuka aykırı verme/ele geçirme) ve bilişim suçları; veri sorumlusunun kendi personeli sızdırdıysa da aynı. Suç duyurusu ayrı karar `[incele]`.
10. **İdari para cezası riski**: veri güvenliği yükümlülüğüne aykırılık m.18/1-(b) aralığında; bildirim gecikmesi ve yetersiz tedbir Kurul kararlarında ağırlaştırıcı. Tutar için `kurul-sureci-ve-yaptirimlar.md`.
11. **Sektörel bildirimler**: bankacılık, elektronik haberleşme, sağlık, SPK gibi düzenleyicilere ayrı bildirim yükümlülüğü olabilir. `[incele]`
12. **Kayıt**: ihlal kayıt defteri (bildirilmeyenler dahil), alınan kararlar ve gerekçeleri.

**Sır ve gönderim kontrolü:** ihlal değerlendirmesi şirket içinde geniş dağıtılırsa ya da sigortacıya/tedarikçiye gönderilirse Kurul ya da mahkeme tarafından istenebilir; iç değerlendirme ile dışa giden bildirimi ayır (ORTAK-KURALLAR.md §1 sır saklama notu).

---

## Görüşme soruları

| Alan | Soru |
|---|---|
| Olay | Ne oldu? İlk belirti ne zaman, kim fark etti, veri sorumlusu ne zaman öğrendi (tarih-saat)? |
| Veri | Hangi kategoriler, özel nitelikli var mı, kaç kayıt/kişi? |
| Kişiler | Müşteri, çalışan, hasta, çocuk? Yurt dışındaki kişiler var mı? |
| Kaynak | Saldırı mı, çalışan hatası mı, veri işleyen mi? |
| Durum | Kontrol altına alındı mı? Veri geri alındı/yayıldı mı? |
| Tedbirler | Hangi teknik ve idari tedbirler vardı, hangileri alındı? |
| İletişim | İrtibat kişisi, VERBİS kaydı, sigorta? |

---

## soorgla çağrıları

```
legal_get_statute_article law_no: "6698" article_no: "12" | "15" | "17" | "18"
legal_get_statute_article law_no: "5237" article_no: "136"
legal_search_admin_guidance sorgu: "Kişisel Verileri Koruma Kurulunun kararı veri ihlali bildirimi geç bildirim idari para cezası" kurum: "Kişisel Verileri Koruma Kurulu" tarih_baslangic: "<son 3 yıl>"
legal_search_official_gazette query: "kişisel veri ihlali bildirim" sort_by: "date_desc"
legal_search_cases sorgu: "kişisel veri ihlali bildirim yükümlülüğü idari para cezası iptal" mahkeme: "danistay"
```

---

## Çıktı iskeleti — (1) iç değerlendirme, (2) Kurula bildirim, (3) ilgili kişi bildirimi

```markdown
(1) [TASLAK BAŞLIĞI]
> ⚠️ Gözden geçiren notu …
## Veri ihlali değerlendirmesi — [kısa ad]
### Zaman çizelgesi
| Tarih-saat | Olay | Kaynak |
### Süre tablosu
| Bildirim | Başlangıç (öğrenme) | Son an | Dayanak | Durum |
### Etki
[veri kategorileri, kişi sayısı, özel nitelikli, olası sonuçlar] — risk: 🔴/🟠/🟡
### Karar
[Kurula bildirim: evet/hayır — gerekçe] [ilgili kişilere bildirim: evet/hayır — gerekçe] `[incele]`
```

```markdown
(2) Kurula bildirim — alan listesi (resmî formun yerine geçmez; formdaki alanların içeriği)
- Veri sorumlusu, VERBİS irtibat kişisi
- İhlalin başlangıç ve tespit tarihi-saati; öğrenme anı; gecikme varsa gerekçesi
- İhlalin kaynağı ve nasıl gerçekleştiği
- Etkilenen veri kategorileri ve kişi grupları; yaklaşık kayıt/kişi sayısı
- Olası sonuçlar
- Alınan ve alınacak tedbirler
- İlgili kişilere bildirim yapıldı mı, nasıl, ne zaman
- Veri işleyen/yurt dışı unsuru
```

```markdown
(3) İlgili kişiye bildirim (dışa giden metin)
Konu: Kişisel verilerinizi etkileyen bir güvenlik olayı hakkında
[ne oldu — sade dil] [hangi verileriniz] [olası sonuçlar] [aldığımız tedbirler]
[sizin yapabilecekleriniz: parola değişikliği, şüpheli aramalara karşı uyarı]
[iletişim]
```

---

## Sık hatalar
- Süreyi "inceleme tamamlanınca" başlatmak (öğrenme anı esas).
- Kanıt toplamadan sistemleri silip yeniden kurmak.
- Veri işleyen kaynaklı ihlalde veri sorumlusunun sorumluluğunun bittiğini sanmak.
- İlgili kişi bildiriminde olayı küçümsemek ya da teknik jargon kullanmak.
- Bildirim yapmama kararını kayda geçirmemek.
- İç değerlendirmeyi geniş dağıtmak.
