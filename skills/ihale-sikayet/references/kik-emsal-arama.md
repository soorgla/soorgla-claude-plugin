# KİK emsal kararı arama ve mahkeme etkisi (MK) kontrolü

Hem istekli (iddiayı desteklemek) hem idare (kararı savunmak) için aynı yöntem. KİK kararı **mahkeme kararı
değildir**: aynı konuda Danıştay'ın aksi yönde kararı varsa o ağır basar; ikisini ayrı etiketle. **Mahkeme kararı
üzerine iptal edilmiş Kurul kararı emsal değildir.**

---

## 1. Araç kapsamı (2026-11-01 durumu)

- `legal_search_cases` `mahkeme: "kik"` (durum 2026-11-02): uyuşmazlık kararları (UH/UM/UY/UD) 2007'den bu yana; geri doldurma sürüyor,
  2026 kararları görünüyor (ör. 2026/UM.II-951, 26.03.2026) `[soorgla]`. **MK kararları da aramada çıkıyor**
  (ör. 2026/MK-240, 16.07.2026; 2026/MK-70, 04.03.2026) `[soorgla]`.
- Kapsam henüz tam değil: sonuç yoksa "karar yok" deme; "soorgla'da bulunamadı" de
  (ORTAK-KURALLAR.md §5).
- **Düzenleyici kararlar (DK) ve ilke kararları araçta yok;** `legal_search_admin_guidance` KİK kararı döndürmüyor.
  RG'de yayımlanan DK için `legal_search_official_gazette` (`institution: "Kamu İhale Kurumu"`); bulamazsan
  `[incele — KİK düzenleyici kararı çekilemedi]`.
- Karar numarasıyla arama zayıf: sorguya "2026/UH.I-1013" yazmak o kararı getirmedi (anlam araması) `[soorgla]`;
  numaralı karar için tarih filtresini dar tut ve sonuçlarda `atif`'i karşılaştır. KİK kararlarında esas no yok;
  `legal_get_case_by_number` işe yaramaz.

## 2. Arama yöntemi

1. **Olay cümlesiyle sor**, anahtar kelime yığınıyla değil:
   `legal_search_cases` `mahkeme: "kik"` `sorgu: "özel sektöre gerçekleştirilen işte sözleşme ve fatura sunulduğu halde
   irsaliye istenerek iş deneyimi reddedildi"` `tarih_baslangic: "<son 3 yıl>"` `adet: 8`.
2. **Yönetmelik dönemini eşle:** ihalenin ilan tarihindeki uygulama yönetmeliği/tebliğ ile kararın dayandığı metin aynı
  mı? 2025-2026 değişikliklerinden (RG 30.07.2025, 09.04.2026, 13.05.2026, 16.10.2026) önceki kararı uyarıyla kullan.
3. **Tam metni oku:** `legal_get_case_document` `belge_id` (gerekirse `azami_karakter` yükselt). Önermenin kararın
   **Kurul gerekçesi** olduğunu, başvuru sahibinin iddia özeti ya da idare cevabı olmadığını kontrol et (KİK
   kararlarında "İtirazen şikâyet dilekçesinde özetle …" bölümü iddiadır, gerekçe değildir) — ORTAK-KURALLAR.md §7 alıntı-önerme.
4. **Hüküm fıkrasını oku:** ret / düzeltici işlem / iptal; oybirliği mi, karşı oy var mı; bedel iadesi kararı.
5. **Danıştay ile çapraz kontrol:** `legal_search_cases` `mahkeme: "danistay"` `sorgu: "<iddia> Kamu İhale Kurulu kararının
   iptali"` `tarih_baslangic: "<son 3 yıl>"` (görülen ihale temyizleri 13. Daire). Danıştay ters yöndeyse KİK kararını
   destek olarak değil, "Kurul uygulaması" olarak an.
6. **MK etkisi kontrolü (zorunlu, §3).**
7. **Yerleşik uygulama** demek için en az üç karar (biri tam metin, son 3 yıl) ve aksi yönde güncel karar olmaması
   gerekir (ORTAK-KURALLAR.md §15). Sonuç sayısı (`toplam_karar`) dayanak değildir.
8. **Emsal uygulanabilirlik ölçütü (olay eşlemesi).** Emsal, kararı doğuran olgu dosyada da varsa işler. Kararın
   hangi olguya dayandığını bir cümleyle yaz, sonra kendi dosyanla karşılaştır; olgu farklıysa emsali "destek" değil
   "ayırt edilen karar" olarak an `[incele]`.
   - **Benzer iş:** "benzer iş dar tanımlandı" gerekçeli iptal kararları yalnız tanım **ihale konusu işten dar**
     olduğunda işler (ör. ihale konusu üç ana kalemden yalnız birini kapsayan tanım — KİK 2026/UH.I-567; ihale konusu
     işin kapsamından da dar tanım — KİK 2025/UH.I-296). Tanım ihale konusuyla **aynı ya da daha genişse** bu emsaller
     uygulanmaz; o dosyada soru, belgenin tanıma girip girmediğidir (açıklama talebi konusu). Kontrol satırı:
     "Emsalde tanım ⊂ ihale konusu mu? Bizde tanım ⊂ ihale konusu mu?" — ikincisi hayırsa emsali kullanma.
     
   - Aynı yaklaşım diğer "rekabeti daraltan şart" emsallerinde de geçerlidir: kararda daraltıcı bulunan şartın ölçüsü
     (oran, belge, süre) dosyadakiyle aynı mı?

## 3. MK etkisi kontrolü

Kurul kararına karşı dava açılır, mahkeme kararını iptal ederse Kurul **MK** numaralı yeni bir karar alır ve önceki
kararı iptal eder, kısmen iptal eder ya da (Danıştay bozması sonrası) "hukuken geçerliliğini koruduğuna" karar verir
`[soorgla — 2026/MK-240, MK-260, MK-222, MK-70]`.

Kontrol sırası:
1. **Karar metninin başlığında "Mahkeme etkisi" satırı** (soorgla, `kik-toplayici mk-etki` ile işaretlenir). Satır,
   MK kararı üzerine **iptal ya da kısmen iptal edilmiş** Kurul kararlarında bulunur. **Satırın olmaması
   "etkilenmedi" anlamına gelmez:** işaretleme yalnız toplanmış MK kararlarına dayanır. 2026-11-02 itibarıyla 2026 MK
   kararları işlendi; 2024–2025 sırada; daha eskisi yok. Etkiyi ayrıca gösteren bir yanıt alanı henüz yok; satırı
   metnin başından oku.
2. Emsal tek dayanaksa, satır yoksa ya da Kurul kararı 2026'dan önceki bir MK kararıyla etkilenmiş olabilecekse ek MK
   araması yap: `legal_search_cases` `mahkeme: "kik"` `sorgu: "Kamu İhale Kurulunun <karar tarihi> tarihli ve
   <karar no> sayılı kararının iptaline mahkeme kararı"` `tarih_baslangic: "<emsal karar tarihi>"`. Sonuçlarda hüküm
   fıkrasında **o karar numarasını** ara.
3. Danıştay'da aynı ihalenin (İKN, idare adı) davasını ara.
4. Hâlâ belirsizse emsali **`[MK durumu doğrulanamadı]`** etiketiyle kullan ve okuyucuya KİK'in "Mahkeme Kararları"
   sorgulamasından teyit etmesini söyle; tek dayanak yapma.

| MK sonucu | Emsal olarak |
|---|---|
| İptal edildi | **Kullanma.** Varsa mahkeme kararının gerekçesini ve MK kararını kullan |
| Kısmen iptal | Yalnız iptal edilmeyen iddia yönünden; hangi iddia olduğunu yaz |
| Geçerli kaldı / dava açılmamış ya da reddedilmiş | Kullanılabilir (etiket: KİK, karar no, tarih, MK durumu) |
| Belirsiz | `[MK durumu doğrulanamadı]` ile, destekleyici olarak |

## 4. Atıf biçimi

`kaynak.atif` alanını aynen kullan: "Kamu İhale Kurumu, K. 2026/UM.II-951, 26.03.2026" `[soorgla]` + MK durumu.
Kurul kararının daire kodu (UH hizmet, UM mal, UY yapım, UD danışmanlık) türle uyumlu mu, kontrol et
`[model bilgisi — doğrulayın]`. Karar numarası, tarih ya da daire uydurulmaz; araçta bulunmayan kararı kullanıcı
verdiyse `[kullanıcı verdi]`.

## 5. İki rolde kullanım
- **İstekli:** her iddia satırına en güçlü bir KİK + bir Danıştay kararı; MK durumu tabloda ayrı sütun.
- **İdare:** şikâyet kararında ve Kuruma görüşte aynı yöntem; Kurul'un aynı konudaki güncel aksi kararını gizleme —
  kararın savunulabilirliğini düşürür `[incele]`.

## 6. Sık hatalar
- 🔴 Mahkemece iptal edilmiş Kurul kararını emsal göstermek.
- 🟠 İddia özetini Kurul gerekçesi sanmak.
- 🟠 Eski yönetmelik dönemine ait kararı değişiklik sonrası ihaleye uygulamak.
- 🟡 Tek KİK kararıyla "yerleşik uygulama" demek.
- 🟠 "Dar benzer iş" iptal emsalini, tanımı ihale konusuyla aynı ya da ondan geniş olan dosyaya uygulamak.
