# Rejimlerin günlük takibi (DİR, HİR, geçici ithalat, antrepo, serbest bölge, transit)

## Ne zaman kullanılır
- "DİİB süresi ne zaman doluyor, ek süre alabilir miyiz?", "geçici ithal ettiğimiz makine ne zaman çıkmalı?", "antrepoda ne kadar kalabilir?", "serbest bölgeye gönderirsem ne olur?".
- Rejim kapatma, teminat çözümü, sarfiyat/fire hesabı hazırlığı.
- Süre **aşıldıysa** ve ceza/ek tahakkuk geldiyse → `../../gumruk-dis-ticaret/references/gumruk-rejimleri-ve-serbest-bolge.md`.

---

## Rejim kartları

Süre ve teminat oranları **yönetmelik ve tebliğden** çekilir; aşağıdaki tablo neyin sorulacağını gösterir.

| Rejim | Takip edilecekler | Kaynak (çek) | Form bankası |
|---|---|---|---|
| **Dahilde işleme (DİR)** | DİİB/izin süresi ve ek süre; ihracat taahhüdü; teminat; eşdeğer eşya; sarfiyat ve fire; kapatma başvurusu süresi | Dahilde İşleme Rejimi Kararı ve Tebliği (İhracat: 2006/12) → `legal_search_statute_semantic`; Gümrük Yönetmeliği DİR bölümü | DİR tebliğ ekleri (MEV), hammadde sarfiyat tablosu (Ek-9), "Özetle DİR" rehberi, fire oranları |
| **Hariçte işleme (HİR)** | İzin süresi; ikame ürün; yeniden ithalde vergi farkı | Hariçte İşleme Rejimi Tebliği (İhracat: 2007/5) | HİR tebliğ ekleri (MEV) |
| **Geçici ithalat** | Rejimde kalma süresi (eşya türüne göre); tam/kısmi muafiyet; teminat; ATA karnesi | 4458 geçici ithalat maddeleri, Gümrük Yönetmeliği; e-ATA/TR | ATA ve geçici ithalat formları `legal_search_forms` |
| **Antrepo** | Antrepoda kalma, elleçleme faaliyetleri, stok kaydı, antrepo türü (A–F) | Gümrük Yönetmeliği antrepo bölümü; antrepo genelgeleri (`legal_search_admin_guidance` "antrepo" `kurum: "Ticaret Bakanlığı"`) | Geçici depolama/antrepoya alınması özellik gösteren eşya listesi |
| **Serbest bölge** | Faaliyet ruhsatı süresi; Türkiye'ye girişte vergi (menşe ve serbest dolaşım durumu); kira | 3218 sayılı Kanun ve yönetmelik | Faaliyet ruhsatı müracaat formu (2026), ruhsat prosedürü, kira tarifeleri, serbest bölgeler listesi |
| **Transit (NCTS)** | Transit süresi; teminat (bireysel, kapsamlı, vazgeçme); izinli gönderici/alıcı | Transit rejimi tebliği; NCTS | TC31/TC33 teminat sertifikaları, transit süre sınırı tablosu, NCTS cep kitabı, kapsamlı teminat bölge listesi |

Kaynak çağrıları:
```
legal_search_statute_semantic   sorgu: "<rejim> süre ek süre teminat"  mevzuat_tur: "teblig"
legal_search_admin_guidance     sorgu: "<rejim> <konu>"  kurum: "Ticaret Bakanlığı"  belge_tur: "genelge"
legal_search_forms              sorgu: "<rejim> başvuru formu"     (araç yoksa: FORM-KAYNAKLARI / ticaret.gov.tr Bilgi Bankası)
```

---

## Süre ve teminat tablosu (her rejim için doldur)

| Belge/izin no | Rejim | Başlangıç | Süre (dayanak) | Son gün | Ek süre imkânı | Teminat (tutar, tür) | Kapatma işi |

Son günü `legal_check_holiday` ile kontrol et; rejim süreleri belge/izin bazlı olduğu için `legal_calculate_deadline` kodu yok; ödeme, itiraz ve geri verme süreleri için `customs_*` kodları (`arac-kullanimi.md`) → `[doğrula]`. Tablo bitince "Süre defterine ekleyeyim mi?" → [sure-takibi](../../sure-takibi/SKILL.md). Çok sayıda DİİB/izin varsa her biri ayrı satır; profilde "beyanname ölçeği" yüksekse dosya klasörü öner.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Belge/izin tarihi ve numarası, kapsamındaki eşya ve miktar? | Süre ve kapatma |
| Taahhüt ne kadar gerçekleşti (ihracat, kullanım)? | Ek süre ve kapatma |
| Teminat türü (nakit, mektup, götürü/kapsamlı)? | Çözüm ve risk |
| Eşya üçüncü kişiye devredildi mi, yer değiştirdi mi? | Rejim ihlali riski 🟠 |

---

## Çıktı iskeleti

```markdown
## Rejim takibi — [rejim] — [belge no]
| Kalem | Durum | Son gün | Yapılacak | Dayanak |
### 🔴 7 günden az kalan süreler
### Kapatma için gereken belgeler (form bankası künyeleriyle)
```

## Sık hatalar
- 🔴 Ek süre başvurusunu süre bittikten sonra yapmak.
- 🟠 Sarfiyat ve fire oranını tahminle yazmak; belge/tebliğ eki esas.
- 🟠 Serbest bölgeden Türkiye'ye girişte eşyanın menşe ve serbest dolaşım durumunu sormamak.
- 🟡 Teminat çözümü için kapatma sonrası başvuruyu unutmak.
