# Dosya sistemi olmayan istemciler: claude.ai web, Claude masaüstü sohbeti, ChatGPT

Bu ortamlarda `~/.claude/plugins/config/...` yoktur; yazılan "dosya" kaybolur. Profil, kullanıcının kendi yapıştırdığı bir **profil bloğu** olarak yaşar.

## 1. Ortamı anlama

- Dosya yazma aracı yoksa ya da yazma denemesi başarısızsa dosya sistemi yok kabul et. Sessizce "kaydettim" deme.
- Konuşmanın başında, proje talimatında ya da kullanıcının ilk mesajında `SOORGLA-HUKUK PROFİLİ` başlıklı blok varsa profil odur; kurulum önerme.

## 2. Akış

1. Kısa kurulumun 5 sorusunu sor (`kisa-gorusme.md`); kullanıcı isterse tam kurulumdan üslup ve yükseltme sorularını ekle. Bağlantı kontrolü aynı şekilde yapılır (soorgla bağlayıcısı bu ortamlarda da çalışabilir).
2. Aşağıdaki biçimde **tek bir kod bloğu** üret. Hedef 1.200 karakterin altı (ChatGPT özel talimat alanı kısa olabilir `[model bilgisi — doğrulayın: alan sınırı istemciye göre değişir]`).
3. Kullanıcıya nereye yapıştıracağını söyle (§3).
4. Bloğun dışında, sohbete de 3-4 satırlık özet yaz; kullanıcı yapıştırmasa bile bu konuşma boyunca profil olarak kullan.

## Blok biçimi

```text
SOORGLA-HUKUK PROFİLİ (sürüm: [TARİH])
Rol: [Avukat/hukukçu | Avukat olmayan, avukata erişimi var | Avukat olmayan, avukata erişimi yok]
Kullanıcı türü: [ör. serbest avukat / şirket hukukçusu / vatandaş / hukuk öğrencisi]
Taraf: [ör. iş: işçi; kira: kiracı; diğer: her dosyada sor]
Ana alanlar: [ör. iş, sosyal güvenlik, icra]
Şehir/adliye: [ör. İzmir, Bayraklı Adliyesi]
Dil: [hukukçu | sade | çok sade]
Risk iştahı: [temkinli | dengeli | atak]
Yükseltme: [kişi/rol ya da "kendim"]
Dilekçe biçimi: [kısa not ya da "genel iskelet"]
İmza: [ör. "Av. Ad Soyad, X Barosu" ya da "boş bırak"]
UYAP/UETS: [var/yok]
Kurallar: Türk hukuku; çıktılar avukat incelemesine sunulan taslaktır; atıflarda soorgla kaynağı yoksa [model bilgisi — doğrulayın] yaz; tutar, oran ve süreyi araçtan çek.
Müvekkil bilgisi bu blokta yoktur ve eklenmemelidir.
```

`Kurallar` satırı, eklentinin ORTAK-KURALLAR.md korkuluklarının en kısa özetidir; eklenti becerileri yüklü değilse (yalnız bağlayıcı varsa) modelin en azından bunları uygulamasını sağlar. ChatGPT paketinde becerilere gömülü kurallar varsa bu satır kısaltılabilir (bkz. TODO "Tek kaynak, iki paket").

## 3. Nereye yapıştırılır

Arayüz adları zamanla değişebilir `[model bilgisi — doğrulayın]`; kullanıcıya en yakın adı söyle, bulamazsa "sohbetin ilk mesajına yapıştırın" yedeğini ver.

| İstemci | Yer | Not |
|---|---|---|
| claude.ai (web, masaüstü) — Proje kullanıyorsa | Proje → **Proje talimatları** (project instructions) | Projedeki bütün sohbetlere uygulanır. Hukuk işleri için ayrı bir proje önerilir. |
| claude.ai — proje yoksa | Ayarlar → Profil → Claude'un dikkate almasını istediğiniz tercihler (kişisel tercihler) | Bütün sohbetlere uygulanır; hukuk dışı sohbetleri de etkiler, bunu söyle. |
| ChatGPT — Proje kullanıyorsa | Proje → **Talimatlar** | |
| ChatGPT — proje yoksa | Ayarlar → Kişiselleştirme → **Özel talimatlar** | Alan kısaysa `Kurallar` satırını kısalt. |
| Hiçbiri | Her yeni sohbetin ilk mesajı | En güvenli yedek; elle yapıştırılır. |

Kullanıcıya söylenecek metin:

> Bu ortamda dosyaya kaydedemiyorum. Aşağıdaki bloğu kopyalayıp **[yukarıdaki yer]** alanına yapıştırın; sonraki sohbetlerde profiliniz oradan okunur. Bu blok [Anthropic / OpenAI] hesabınızda, proje ayarlarında saklanır; içinde müvekkil bilgisi yoktur, eklemeyin.

## 4. Güncelleme

Dosya olmadığı için güncelleme **yeni blok** demektir: kullanıcının mevcut bloğunu iste (ya da konuşmadakini kullan), `profil-guncelleme.md` akışıyla tek alanı değiştir, bloğun tamamını yeniden üret ve "eski bloğun yerine bunu yapıştırın" de. Sürüm tarihini yenile. Yalnız değişen satırı vermek hata üretir; her zaman bütün bloğu ver.

## 5. Ortam değişirse

Kullanıcı daha sonra Claude Code ya da Cowork'e geçerse: "Elinizdeki profil bloğunu yapıştırın, dosyaya çevireyim" — blok `profil-sablonu.md` yapısına genişletilir, eksik alanlar `[VARSAYILAN]` olur.

## 6. Gizlilik notu (bu ortama özgü)

- Proje talimatı ve özel talimatlar sağlayıcının sunucusunda tutulur. Büro düzeyindeki bilgiler (rol, şehir, üslup) için bu genellikle sorun değildir; müvekkil bilgisi için değildir.
- Sohbette paylaşılan belgelerin (dilekçe örneği) saklanması hesabın veri ayarlarına bağlıdır `[model bilgisi — doğrulayın: hesap türüne göre saklama ve eğitim ayarları]`. Örnek dilekçeyi kişisel verileri silinmiş olarak iste.
