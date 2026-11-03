# Açık kaynak lisans uyumu

## Ne zaman kullanılır
- "Ürünümüzde GPL'li kütüphane var, sorun olur mu?", "SaaS olarak sunuyoruz, AGPL tetiklenir mi?", "bağımlılık listemizi (package.json, requirements.txt, SBOM) incele", "kodumuzu açık kaynak yapmak istiyoruz", "satın alacağımız şirketin yazılımında açık kaynak riski".
- Teslim alınan yazılımda açık kaynak beyanı ve garantisi (sözleşme yönü `../../sozlesme-incelemesi-tbk/references/yazilim-lisans-ve-saas.md` "AÇIK-KAYNAK" satırı).

Eski YAML `analysis/ip_technology_docs/software_license_agreement.yaml` **boş**; bu dosya sıfırdan, upstream `oss-review` becerisi Türk hukukuna uyarlanarak yazıldı.

**Hukuki çerçeve:** Açık kaynak lisansları FSEK m.48'deki kullanma yetkisi (ruhsat) niteliğinde sözleşmelerdir; koşula aykırı kullanım hem sözleşme ihlali hem lisans kapsamı dışında kalan kullanım olarak FSEK m.68 bedel ve m.66 ref/men taleplerine yol açabilir `[incele]`. Açık kaynak lisans koşullarının ihlaline özgü Türk yargı kararı soorgla'da bulunamadı; FSHHM kararları kaynak kod kopyalamayı genel FSEK ihlali (işleme, çoğaltma) olarak inceliyor. Emsal varmış gibi yazma; çalışma anında güncel karar ara, bulamazsan `[ARAŞTIRMA GEREKLİ: açık kaynak lisans ihlali içtihadı]`. Yabancı hukuk seçimi içeren lisanslarda (ör. bazı kaynak-erişilebilir lisanslar) ORTAK-KURALLAR.md §2 yabancı unsur uyarısı.

---

## Adım 1 — Kapsam
Bağımlılık listesi mi (gelen), tek kütüphane mi, yoksa kendi kodumuzu açmak mı (giden)? Dosya biçimini oku (package.json, requirements.txt, go.mod, pom.xml, Cargo.toml, SBOM). Doğrudan ve geçişli bağımlılıkları ayır; geçişli liste yoksa iste.

## Adım 2 — Dağıtım modeli (sınıflandırmadan önce)
| Model | Tetiklenen yükümlülük |
|---|---|
| Yalnız iç kullanım | Copyleft çoğunlukla tetiklenmez |
| SaaS / ağ üzerinden sunum | AGPL (ağ etkileşimi) ve SSPL tetiklenebilir; GPL çoğunlukla tetiklenmez `[incele]` |
| Dağıtılan ikili dosya / mobil uygulama / gömülü cihaz | GPL/LGPL kaynak kodu sunma, lisans metni, değişiklik bildirimi |
| Müşteriye kaynak kodla teslim | Lisans uyumluluğu ve atıf dosyası |

## Adım 3 — Sınıflandırma
| Sınıf | Örnek | Ana yükümlülük | Varsayılan işaret |
|---|---|---|---|
| İzin verici | MIT, BSD, Apache-2.0, ISC | Telif bildirimi ve lisans metnini koruma; Apache'de NOTICE ve patent hükmü | 🟢 |
| Zayıf copyleft | LGPL, MPL-2.0, EPL | Değiştirilen dosyanın/kütüphanenin kaynağını açma; bağlama biçimi önemli | 🟡 |
| Güçlü copyleft | GPL-2.0, GPL-3.0 | Dağıtımda türev eserin kaynağını aynı lisansla açma | 🟠 (dağıtımda 🔴 olabilir) |
| Ağ copyleft | AGPL-3.0 | Ağ üzerinden sunumda da kaynak açma | 🔴 SaaS'ta |
| Kaynak-erişilebilir (OSI onaylı değil) | SSPL, BUSL, Commons Clause, Elastic License | Ticari kullanım/hizmet olarak sunma kısıtları | 🟠 |
| Lisans bilinmiyor | — | Kullanma hakkı yok sayılır (FSEK m.18/1: mali haklar eser sahibinde) | 🔴 "inceleme gerekli", izin verici sayma |

## Adım 4 — Hata modları (upstream listesi)
- [ ] Lisans dosyası ile dosya başlıkları çelişiyor → ikisini de raporla.
- [ ] Uyumsuz kombinasyon (ör. GPL-2.0-only + Apache-2.0) `[incele]`.
- [ ] **Lisans değişikliği:** bir sürüm izin verici, sonraki kaynak-erişilebilir (Redis, MongoDB, Elastic, HashiCorp örnekleri) — sabitlenen sürümün lisansını kontrol et.
- [ ] Çift lisanslı paket: hangi lisansı seçtiğimiz belgelenmiş mi?
- [ ] Bakımı bırakılmış paket.
- [ ] Geçişli copyleft (üst paket MIT, alt bağımlılık GPL).
- [ ] Yapay zekâ kod asistanı çıktısında lisanslı kod parçası `[incele]`.

## Adım 5 — Giden kontrol (kodumuzu açarken)
- [ ] Kodun **tamamının** mali hakları bizde mi? Çalışan kodu (FSEK m.18/2) ✅; freelance/yüklenici kodu yazılı devir (m.52) yoksa 🔴.
- [ ] Üçüncü kişi kodu ve lisans uyumu; seçilecek lisans ile bağımlılıkların uyumu.
- [ ] Ticari sırlar, kimlik bilgileri, kişisel veri (KVKK) depoda kalmış mı?
- [ ] Marka: proje adı tescilli markayla çakışıyor mu (`marka-tescil-itiraz-ve-turkpatent.md`).
- [ ] Patent: açık kaynak yapmak buluşun yeniliğini bozar; patent başvurusu düşünülüyorsa önce başvur (SMK m.84'teki 12 aylık hoşgörü yalnız belirli açıklamalar için).

## Adım 6 — Bilgi talebi ve satın alma
Şirket satın almada açık kaynak riski → `../../sirketler-ticaret/references/sirket-satin-alma-ve-inceleme.md` (fikri mülkiyet bölümü); bu dosyanın tablosu ek olarak kullanılır.

---

## Görüşme soruları

| Soru | Neden |
|---|---|
| Ürün nasıl sunuluyor (SaaS, mobil, kurulum dosyası, cihaz, iç kullanım)? | Tetikleyici |
| Bağımlılık listesi ve sürümleri; geçişli liste/SBOM? | Sınıflandırma |
| Açık kaynak kodu değiştirdiniz mi; nasıl bağlanıyor (statik/dinamik)? | Copyleft kapsamı |
| Müşteriye kaynak kod teslimi ya da açık kaynak beyanı taahhüdünüz var mı? | Sözleşme |
| Kodu kim yazdı (çalışan, yüklenici, yapay zekâ aracı)? | Giden kontrol |

---

## Çıktı iskeleti

```markdown
## Açık kaynak incelemesi — [proje] ([dağıtım modeli])
### Sonuç (tek paragraf) — yayımı durduran 🔴 kalemler
### Paket tablosu (önem sırasına göre)
| Paket@sürüm | Lisans | Doğrudan/geçişli | Yükümlülük (bu dağıtım modelinde) | İşaret | Not |
### Hata modları
### Giden kontrol (varsa)
### Uyum adımları: NOTICE/atıf dosyası, kaynak teklifi, değiştirilecek paketler
### Onay — [incele] (profildeki onay kişisi)
```

---

## Sık hatalar

- 🔴 Lisansı bilinmeyen paketi izin verici saymak.
- 🔴 SaaS ürününde AGPL bileşeni gözden kaçırmak.
- 🟠 Sabitlenen sürümün lisans değişikliğini kontrol etmemek.
- 🟠 Freelance kodunu açık kaynak yapmadan önce hak devrini kontrol etmemek.
- 🟡 GitHub'ın gösterdiği lisans etiketine güvenmek; dosyayı oku.

---

## Kaynak ve uyarlama

- `analysis/ip_technology_docs/software_license_agreement.yaml` — **boş** (0 bayt); dosya sıfırdan.
- Upstream: `ip-legal/skills/oss-review` (kapsam, dağıtım modeli önce, sınıflandırma, hata modları, giden kontrol), `ip-clause-review` (hak devri boşluğu kontrolü — Türk karşılığı FSEK m.52)
