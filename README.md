# soorgla Hukuk

Türk hukuku için Claude eklentisi. 47 beceri ve soorgla MCP bağlayıcısı içerir; claude.ai (web, masaüstü,
mobil), Cowork ve Claude Code'da çalışır. Beceriler hukuki soruyu değerlendirir, dilekçe ve başvuru taslağı kurar,
süreleri ve dosyayı düzenler. Mevzuat maddesi, madde tarihçesi, Yargıtay, Danıştay, AYM, BAM, KİK, Sayıştay ve
AİHM kararları, kurul kararları ve idari görüşler, Resmî Gazete, süre, harç, faiz, kur, TÜFE ve sosyal
parametreler her seferinde soorgla araçlarından kaynağıyla çekilir. Beceri metinlerinde sabit tutar, oran ya da
parasal sınır yazılı değildir.

> **Taslaktır.** Bu eklentinin ürettiği her şey avukat incelemesine sunulan bir taslaktır; hukuki görüş değildir
> ve avukatın yerine geçmez. Avukat olmayan kullanıcıya her çıktıda "hukuki tavsiye değildir" başlığı konur ve
> dilekçe, ihtar ya da itiraz göndermeden önce bir avukata danışması istenir. Süre ve tutarları birincil
> kaynaktan kendiniz doğrulayın.

## Başlarken

1. Eklentiyi ekleyin, ardından eklentinin **Connectors** sekmesinden soorgla bağlayıcısını bağlayın. İlk
   kullanımda soorgla hesabınızla giriş istenir (OAuth).
2. Sorunu kendi cümlenizle anlatın; beceri adı yazmanız gerekmez. Örnekler:
   - "Müvekkilim performans gerekçesiyle çıkarıldı, işe iade için ne yapmalıyım?"
   - "Ev sahibim kira artışını yüzde 60 istiyor, yasal mı?"
   - "Bu istinaf dilekçesinin süresini ve harcını hesapla."
   - "İcra takibi başlatılmış, ödeme emrine nasıl itiraz ederim?"
   - "Mart KDV'sini 20 gün geç ödedim, gecikme zammı ne kadar?"
3. İsterseniz "kurulum yap" yazın: beş soruluk tanışmayla rolünüze (avukat, vatandaş, mali müşavir, gümrük
   müşaviri, kamu görevlisi…) ve tarafınıza göre cevaplar kişiselleşir.

## Beceriler

- **Alan becerileri (32):** iş hukuku, sosyal güvenlik (SGK), KVKK, sözleşme incelemesi (TBK/TTK), kira,
  tazminat ve haksız fiil, icra ve iflas, aile ve miras, kamu ihale (yapım, mal, hizmet, danışmanlık, şikâyet,
  belgeler, teminat ve yasaklama), hakediş, idare davaları ve imar, kamu personeli, vergi, muhasebe, şirketler ve
  ticaret, tüketici, fikri mülkiyet ve bilişim, gümrük ve dış ticaret, gümrük uygulaması, yatırım teşviki, kamu
  mali denetimi ve Sayıştay, ceza hukuku, yabancılar ve vatandaşlık, deniz ticareti ve taşıma, taşınmaz ve inşaat.
- **Dilekçe becerileri (6):** hukuk yargılaması (dava, cevap, ıslah, arabuluculuk, ihtarname), kanun yolları
  (istinaf, temyiz), ceza ve infaz, idari ve kurum başvuruları, vatandaş başvuruları (CİMER, bilgi edinme, icraya
  itiraz, tüketici hakem heyeti), AYM ve AİHM bireysel başvurusu.
- **İş akışı becerileri (9):** tanışma ve büro profili, dosya klasörü, süre takibi ve takvim, dava kronolojisi,
  müvekkil iletişimi, tablolu belge incelemesi, mevzuat değişikliği takibi, hesap araçları rehberi, genel hukuk
  araştırması.

## Eklenti ne çalıştırır, nereye ne gönderir

- **soorgla MCP sunucusu** (`https://mcp.soorgla.com/mcp`, HTTP, OAuth): beceriler arama terimlerini, kanun ve
  madde numaralarını, karar künyelerini, tarihleri ve hesap girdilerini (ör. tutar, tebliğ tarihi) bu sunucuya
  gönderir ve sonuçları kaynağıyla alır. Sunucu soorgla tarafından işletilir. Gizlilik politikası:
  <https://soorgla.com/gizlilik-politikasi/>. Olayın kendisini ya da yüklediğiniz belgeyi sunucuya göndermek becerilerin işi değildir;
  beceriler yalnız sorgu için gereken terimleri gönderir.
- **Ortak kurallar:** her becerinin başında kuralların kısa özeti, eklenti kökünde tam metni
  (`ORTAK-KURALLAR.md`) vardır. Eklenti hook ya da betik çalıştırmaz.
- **Yerel dosyalar (yalnız Claude Code):** büro profili, dosya klasörleri, süre defteri ve mevzuat takip listesi
  `~/.claude/plugins/config/soorgla-hukuk/` altında tutulur. Bu dosyalar meslek sırrı ve kişisel veri içerebilir;
  bulut eşitlemesi yapılan bir klasöre koymayın. claude.ai sohbetinde dosya yazılmaz; beceriler sohbette
  saklayabileceğiniz bir kopyalama bloğu verir.
- **Takvim:** süre takibi becerisi, bağlı bir takvim bağlayıcınız varsa son günleri önizleme gösterip yalnız
  onayınızla takvime yazar.
- Eklentinin kendisi telemetri toplamaz, paket indirmez, ikili dosya ya da betik çalıştırmaz.

## Lisans ve uyarlama notu

Apache License 2.0 (`LICENSE`). Biçim, korkuluk kuralları ve bazı iş akışları
[anthropics/claude-for-legal](https://github.com/anthropics/claude-for-legal) deposundan (Apache 2.0, Copyright
2026 Anthropic PBC) uyarlanmış ve değiştirilmiştir; ayrıntı `NOTICE.md` dosyasındadır. Türk hukuku içeriği
soorgla tarafından yazılmış ve soorgla MCP ile denetlenmiştir. Bu eklenti Anthropic tarafından yayımlanmamış,
onaylanmamış ya da desteklenmemiştir.
