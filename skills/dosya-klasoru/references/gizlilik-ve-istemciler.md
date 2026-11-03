# Gizlilik, dosyalar arası bağlam ve dosya sistemi olmayan istemciler

Kaynak: upstream `matter-workspace` "Cross-matter context" bölümü ve `litigation-legal/CLAUDE.md` "Matter workspaces" bölümü. ABD "attorney work product / privilege" kavramları yerine Av.K. m.36 sır saklama, CMK m.130 büro araması güvencesi ve KVKK kondu; claude.ai Projects ve ChatGPT kullanımı eklendi.

---

## 1. Dosyalar arası bağlam (varsayılan KAPALI)

Profilde `Dosyalar arası bağlam: kapalı` iken (varsayılan), A dosyasında çalışan hiçbir beceri B dosyasının klasöründeki hiçbir dosyayı okumaz. Bu kuralın iki gerekçesi:

- **Sır saklama.** Avukatın görevi dolayısıyla öğrendiklerini açığa vurması yasaktır (Av.K. m.36) `[soorgla]`. Bir müvekkilin bilgisinin başka bir müvekkilin taslağına sızması bu yasağın en olası ihlal yoludur.
- **Çıkar çatışması.** Aynı büroda karşıt çıkarlı müvekkiller (ör. aynı işverenin iki eski çalışanı; bir şirket ve onun bayisi) olabilir; Av.K. m.38 ret zorunluluğu ortakları ve büro avukatlarını da kapsar `[soorgla]`.

Kurallar:
- Portföy ve süre özetleri yalnız `_liste.yaml`'ı okur. Dizin bu yüzden en az bilgiyle tutulur (`sablonlar.md` §4).
- Dosyalar arasında taşınması gereken öğrenimler (ör. "X İş Mahkemesi bilirkişileri giydirilmiş ücreti şöyle hesaplıyor") bir dosyaya değil **profile** ya da büronun genel notuna, müvekkil bilgisi ayıklanarak yazılır; bunu kullanıcı onaylar.
- Profilde `açık` ise bile varsayılan yine yalnız etkin dosyadır; başka dosya **yalnız kullanıcının açık isteğiyle** okunur ("son beş kira dosyamızdaki artış maddelerini karşılaştır"). Okunan dosyalar gözden geçiren notunun **Okunan** satırına adlarıyla yazılır.
- Gizlilik sınıfı "çok yüksek" olan dosya, profil ne derse desin dosyalar arası okumaya kapalıdır.
- "İlgili dosyalar" bölümündeki bağlantı yalnız addır; okuma izni değildir.

## 2. Yerel dosyalarda tutulan veri: nerede ve hangi riskle

Kullanıcıya ilk `ac`'ta bir kez, kısa olarak söyle:

> "Dosya kartı ve günlük şu klasörde düz metin olarak tutulacak: `~/.claude/plugins/config/soorgla-hukuk/dosyalar/<kisa-ad>/`. Şifrelenmez. Bu klasör bilgisayarınızın yedeğine ya da bulut eşitlemesine (OneDrive, Dropbox, Google Drive) dahilse içerik oraya da gider. Müvekkil bilgisi meslek sırrıdır (Av.K. m.36) ve kişisel veridir (KVKK); veri güvenliği tedbirleri veri sorumlusu olarak sizin sorumluluğunuzdadır (KVKK m.12)."

Ayrıntılar:
- **Veri güvenliği:** veri sorumlusu, kişisel verilere hukuka aykırı erişimi önlemek ve muhafazayı sağlamak için teknik ve idari tedbirleri almakla yükümlüdür; veri ihlalinde ilgiliye ve Kurula bildirim yükümlülüğü vardır (KVKK m.12) `[soorgla]`. Disk şifrelemesi (BitLocker/FileVault), ekran kilidi ve bulut eşitlemesinden hariç tutma önerilir `[model bilgisi — doğrulayın]`. İhlal olursa → `kvkk` becerisi (veri ihlali bildirimi).
- **KVKK istisnası avukatı kapsamaz:** KVKK m.28/1-d yalnız yargı makamları ve infaz mercilerinin işlemesini kanun dışında tutar `[soorgla]`; avukatın müvekkil verisini işlemesi Kanun kapsamındadır. Özel nitelikli verinin işlenmesi KVKK m.6/3'teki hâllere (ör. bir hakkın tesisi, kullanılması veya korunması için zorunlu olması) bağlıdır `[soorgla]`. Avukatın hangi işleme şartına dayandığı ve aydınlatma yükümlülüğü → `kvkk` becerisi `[incele]`.
- **Büro araması:** avukat büroları ancak mahkeme kararıyla ve baro temsilcisi hazır bulunarak aranabilir; meslekî ilişkiye ait olduğu ileri sürülen şeyler mühürlenir ve hâkim karar verir (CMK m.130) `[soorgla]`. Bu güvencenin kişisel bilgisayardaki ya da bulut hizmetindeki dosyalara nasıl uygulandığı ayrı bir sorudur `[incele]`; "GİZLİDİR" başlığı koruma yaratmaz (ORTAK-KURALLAR.md §1).
- **Avukat olmayan kullanıcı** (İK, şirket içi uzman, vatandaş): meslek sırrı güvencesi onun kendi notlarına uzanmaz; bu notlar müfettiş ya da mahkeme tarafından istenebilir (ORTAK-KURALLAR.md §1). Kartın gizlilik satırı bunu değiştirmez.
- **Proje içi klasör** (`./dosyalar/`): yalnız kullanıcı isterse. Klasörü `.gitignore`'a ekle; depo paylaşılıyorsa ya da uzak sunucuya itiliyorsa kesinlikle önerme. Aynı çalışma klasöründe başka bir ajanın ya da betiğin dosyaları okuyabileceğini hatırlat.
- **Model sağlayıcısı:** dosya içeriği sohbete okunduğunda yapay zekâ sağlayıcısının sunucularında işlenir ve yurt dışına aktarım sayılabilir `[model bilgisi — doğrulayın]`. Müvekkil açık rızası ya da başka bir aktarım şartı gerekip gerekmediği → `kvkk` becerisi (yurt dışına aktarım) `[incele]`. Gizlilik sınıfı yüksek dosyalarda ad yerine kod ve gereksiz kimlik verisini ayıklama önerilir.

## 3. claude.ai Projects ile kullanım

claude.ai web ya da masaüstünde dosya sistemi aracı yoksa en yakın karşılık **dosya başına bir Proje**dir:

- Proje adı: kısa ad (gizlilik sınıfı yüksekse kod).
- Proje talimatları: `dosya.md`'nin güncel hâli (taraflar, merci, süreler, dosyaya özgü kurallar) ve "bu proje yalnız bu dosya içindir; başka müvekkil bilgisi kullanılmaz" satırı.
- Proje bilgisi: belgeler (dilekçeler, kararlar). `_gunluk.md` ayrı bir belge olarak yüklenir ve her güncellemede yenisiyle değiştirilir.
- **Bir Projeye birden çok müvekkil koymayın**; dosyalar arası bağlam kuralı Proje sınırıyla sağlanır.
- Hesap düzeyindeki **bellek** ya da "geçmiş sohbetlere başvurma" özellikleri açıksa bir müvekkilin bilgisi başka bir sohbete taşınabilir; bu özellikleri kapatmayı ya da Proje kapsamıyla sınırlamayı değerlendirin `[model bilgisi — doğrulayın]`. Ekip (Team/Enterprise) hesabında Projenin kimlerle paylaşıldığını kontrol edin.
- Portföy özeti için ayrı bir "Portföy" Projesine yalnız `_liste.yaml` içeriği konur; dosya kartları konmaz.

## 4. Dosya sistemi olmayan istemciler (claude.ai sohbeti, ChatGPT, diğer MCP istemcileri)

Bu ortamlarda beceri hiçbir şeyi "kaydettim" diye bildirmez. Bunun yerine:

1. **`ac`:** görüşmeyi aynı yürüt; sonunda tam `dosya.md` ve `_liste.yaml` satırını ayrı ayrı **kopyalanacak blok** olarak ver. "Bunu kendi bilgisayarınızda ya da Proje bilgisi olarak saklayın; bir sonraki konuşmanın başında yapıştırın" de.
2. **`guncelle`:** kullanıcıdan güncel kartı yapıştırmasını iste (yoksa yalnız kullanıcının anlattığıyla çalış ve bunu söyle). Çıktı: günlüğe eklenecek giriş bloğu + kartta değişen satırlar (önce/sonra) + dizin satırının yeni hâli.
3. **`brifing`:** yalnız yapıştırılan kart ve günlükle; yapıştırılmayan bilgiyi bilinen gibi sunma.
4. **`portfoy`:** kullanıcı `_liste.yaml` içeriğini yapıştırırsa çalışır; yoksa "elimde dizin yok" de.
5. **`kapat`:** kapanış girişini ve dizin satırını blok olarak ver; taşıma ve arşivi kullanıcının kendisinin yapacağını söyle.

ChatGPT'de Projeler aynı mantıkla kullanılabilir (dosya başına bir proje, yalnız o dosyanın belgeleri) `[model bilgisi — doğrulayın]`. Hangi istemcide olursa olsun §2'deki model sağlayıcısı uyarısı geçerlidir.

## 5. Kullanıcıya gösterilecek kısa uyarı (ilk kullanımda bir kez)

> "Dosya klasörü bilgileri bu bilgisayarda düz metin olarak, `[yol]` altında tutulur. Müvekkil bilgisi meslek sırrı ve kişisel veridir; diski şifreleyin, klasörü bulut eşitlemesinden çıkarın, gerekmeyen kimlik verisini (T.C. kimlik no, sağlık bilgisi) karta yazmayın. Bir dosyada çalışırken diğer dosyalar okunmaz."
