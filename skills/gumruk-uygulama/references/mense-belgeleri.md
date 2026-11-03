# Tercihli menşe ve belge seçimi

## Ne zaman kullanılır
- "AB'den gelen bu eşya için A.TR mi EUR.1 mi?", "Malezya menşeli eşyada tercihli oran için ne lazım?", "GTS'den yararlanabilir miyiz?".
- İhracatçı olarak hangi belgeyi düzenleteceğiniz (→ ayrıca `ihracat-gunluk.md`).
- Belge **reddedildi**, sonradan kontrol ya da saptırma soruşturması başladıysa → `../../gumruk-dis-ticaret/references/mense-ve-ticaret-politikasi-onlemleri.md`.

---

## Ülke grubu → sütun → belge

Maliyet aracı menşe ülkenin girdiği sütunları kendisi seçer ve en düşük oranı alır; tercihli sütun seçildiyse açıklamada "menşe ispat belgesi gerekir" yazar. Belge yoksa **Diğer Ülkeler (DÜ)** oranı uygulanır; maliyeti iki senaryoda ver.

| Grup (İthalat Rejimi sütunu) | Kapsam | Belge (genel kural) | Kontrol |
|---|---|---|---|
| AB (Gümrük Birliği) — sanayi ve işlenmiş tarım ürünleri | AB üyesi ülkeler; Gümrük Birliği içinde serbest dolaşımdaki eşya | **A.TR dolaşım belgesi** (menşe değil, serbest dolaşım belgesi); AKÇT ürünleri hariç | Gümrük Birliği kapsamı dışındaki eşya için A.TR düzenlenemez (2006/10895 sayılı Karar m.5, m.33) |
| AB — işlenmemiş tarım ve AKÇT ürünleri; EFTA ve STA ülkeleri | Serbest ticaret anlaşmaları (ülke listesi İthalat Rejimi Kararı sütun başlıklarında) | **EUR.1 / EUR-MED** ya da fatura üzerinde **menşe beyanı** (anlaşmaya göre eşik ve onaylanmış ihracatçı şartı) `[doğrula: ilgili anlaşmanın menşe protokolü]` | Pan-Avrupa-Akdeniz kümülasyonu (PAAMK konvansiyonu) — form bankasında ekleri var |
| GTS (Genelleştirilmiş Tercihler Sistemi): EAGÜ, ÖTDÜ, GYÜ | Gelişme yolundaki ülkeler; **hariç sektörler** (S-xx) | Kayıtlı ihracatçı (REX) sistemine kayıtlı ihracatçının **menşe beyanı** (CB Kararı 501; Gümrük Genel Tebliği (GTS) Seri No: 5); tebliğde sayılan istisna ülkelerde Form A | Ülke o GTİP'in sektöründe hariçse tercih yok (araç kontrol eder) |
| Diğer Ülkeler (DÜ) | Tercih yok | Menşe şahadetnamesi yalnız önlem/kota/gözetim gerektiriyorsa | Damping ve İGV ülke bazlı → menşe şahadetnamesi istenebilir |

Kural ve eşikler anlaşmaya göre değişir; her anlaşmanın menşe protokolünü/yönetmeliğini çek:
```
legal_search_statute_semantic sorgu: "<ülke> serbest ticaret anlaşması tercihli menşe kuralları yönetmelik"
legal_search_official_gazette query: "Tercihli Menşe" search_in: "title" sort_by: "date_desc"
legal_search_admin_guidance sorgu: "<belge> menşe ispat" kurum: "Ticaret Bakanlığı"
```

---

## Kontrol listesi

1. Menşe ülke ve **üretim yeri** (ticari aracının ülkesi değil); üçüncü ülke girdisi varsa menşe kazanma kuralı (yeterli işçilik/işlem listesi — form bankasında "Menşeli Olmayan Girdilere Uygulanması Gereken İşçilik veya İşlem Listesi").
2. **Doğrudan taşıma** kuralı: üçüncü ülkede aktarma/depolama varsa belgenin geçerli kalıp kalmadığı anlaşmaya göre değişir; ilgili menşe protokolünden çek (A.TR'de 2006/10895 sayılı Karar).
3. Belge türü ve **düzenleyen** (ihracatçı ülke yetkilisi / onaylanmış ihracatçı); fatura beyanında imza ve eşik.
4. Belgenin **geçerlilik süresi** ve ibraz zamanı; tescilde yoksa sonradan ibraz ve geri verme imkânı → `../../gumruk-dis-ticaret/references/gumruk-kiymeti-ve-geri-verme.md` (süre anlaşmanın protokolünde; çek ve süre defterine ekle).
5. Liste dipnotunda ülke bazlı özel hüküm (ör. "Gürcistan için gümrük vergisi %0") — araç açıklamasında görünür.
6. Damping ve İGV için menşe şahadetnamesi gerekiyor mu (ülke bazlı önlemlerde).

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Eşya nerede üretildi; tedarikçi üretici mi? | Menşe ülke |
| Gönderi doğrudan mı geldi? | Doğrudan taşıma |
| Tedarikçi hangi belgeyi düzenleyebiliyor (A.TR, EUR.1, fatura beyanı)? Onaylanmış ihracatçı mı? | Belge türü |
| Önceki ithalatlarda belge reddi oldu mu? | Risk, sonradan kontrol |

---

## Çıktı iskeleti

```markdown
## Menşe ve belge — [eşya, GTİP] — [menşe ülke]
| Senaryo | Sütun | Gümrük vergisi | İGV | Belge | Şart |
| Belgeyle | … | … | … | … | … |
| Belgesiz (DÜ) | DÜ | … | … | — | — |
### Tedarikçiden istenecekler
### Anlaşma protokolünden çekilen kurallar (künyesiyle)
```

## Sık hatalar
- 🔴 A.TR ile AB'de serbest dolaşımda olmayan eşyaya Gümrük Birliği oranı uygulamak.
- 🟠 İşlenmemiş tarım ya da AKÇT ürününde A.TR istemek (A.TR yalnız sanayi ve işlenmiş tarım ürünleri, 2006/10895 m.5).
- 🟠 GTS hariç sektör kuralını atlamak.
- 🟡 Belgesiz senaryoyu maliyette göstermemek.
