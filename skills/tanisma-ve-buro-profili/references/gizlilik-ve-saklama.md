# Gizlilik ve saklama

Upstream `legal-clinic` "ethical & confidentiality preconditions" bölümünün Türk hukukuna uyarlanmış, büro profiline daraltılmış hâli. ABA Formal Opinion 512 ve Model Rules yerine Avukatlık Kanunu ve KVKK hükümleri kullanılır.

## 1. Kurulum sonunda kullanıcıya söylenecek kısa metin (bir kez)

> Profiliniz şurada duruyor: `~/.claude/plugins/config/soorgla-hukuk/profil.md`. Düz metin bir dosyadır, şifrelenmez; bu bilgisayara ve kullanıcı hesabına erişen herkes okuyabilir. İçinde müvekkil adı, dosya numarası ya da olay ayrıntısı **yoktur** ve olmamalıdır: profil büronuzun çalışma biçimini tutar, dosyalarınızı değil. Avukatın sır saklama yükümlülüğü (Avukatlık Kanunu m.36) ve kişisel veriler için veri güvenliği yükümlülüğü (KVKK m.12) bu dosya için de geçerlidir; ortak bilgisayar kullanıyorsanız dikkate alın.

Web/ChatGPT'de metnin ilk cümlesi `web-ve-chatgpt.md` §3'teki sürümle değişir.

## 2. Dayanaklar

- **Av.K. m.36:** avukatların görevleri dolayısıyla öğrendikleri hususları açığa vurmaları yasaktır; tanıklık iş sahibinin muvafakatine bağlıdır ve avukat yine de çekinebilir [soorgla]. Yükümlülük avukatı bağlar; bir dosyanın "gizli" etiketi taşıması onu ifşadan korumaz (ORTAK-KURALLAR.md §1 "Sır saklama notu"). 
- **CMK m.130:** avukat büroları ancak mahkeme kararıyla, kararda belirtilen olayla ilgili olarak ve Cumhuriyet savcısının denetiminde aranabilir; baro temsilcisi hazır bulunur; avukat-müvekkil ilişkisine ait olduğu ileri sürülen şeyler mühürlenir ve hâkim kararına kadar ayrı tutulur [soorgla]. Bu güvencenin bürodaki bilgisayar dışındaki cihazlara (ev bilgisayarı, bulut hesabı) nasıl uygulandığı `[model bilgisi — doğrulayın]`. 
- **KVKK m.12:** veri sorumlusu hukuka aykırı işleme ve erişimi önlemek, verilerin muhafazasını sağlamak için teknik ve idari tedbir almak zorundadır; veri işleyenle birlikte müştereken sorumludur; verilerin kanuni olmayan yollarla elde edilmesi hâlinde ilgiliye ve Kurula bildirim yapılır [soorgla]. 
- **KVKK m.6:** sağlık, cinsel hayat, ceza mahkûmiyeti ve güvenlik tedbirleri, sendika üyeliği, din, biyometrik ve genetik veriler özel nitelikli kişisel veridir; işlenmesi kural olarak yasaktır, sayılan hâllerde mümkündür ve Kurulun belirlediği yeterli önlemler şarttır [soorgla]. İş, ceza, aile ve sağlık dosyaları bu verileri sıkça taşır. 

## 3. Profile yazılmayanlar

| Bilgi | Neden | Nereye |
|---|---|---|
| Müvekkil adı, T.C. kimlik no, adres, telefon | Kişisel veri; profil her beceride okunur, her çıktıya sızabilir | Dosya çalışma alanı (ORTAK-KURALLAR.md "Büro profili" son paragrafı) ya da hiçbir yere |
| Dosya/esas numarası, olay ayrıntısı, karşı taraf | Sır saklama; dosyalar arası sızıntı | Dosya çalışma alanı |
| Sağlık, ceza, sendika gibi özel nitelikli veri | KVKK m.6 | Hiçbir yere |
| Kıdem tavanı, asgari ücret, harç, faiz, parasal sınır | Değişir; eski değer sessiz hata üretir | Araçtan çekilir (ORTAK-KURALLAR.md §5) |
| Örnek dilekçenin kendisi | Müvekkil bilgisi içerebilir; profili şişirir | Yalnız çıkarılan biçim notları (en fazla 10 madde) |
| Şirket ticari sırları, açık soruşturmanın ayrıntısı | Gereksiz risk | Yalnız "var/yok" |

Kullanıcı yine de bunlardan birini profile yazdırmak isterse uyar; ısrar ederse kişisel veri ve özel nitelikli veri için **yazma** ve nedenini söyle, diğerleri için (ör. baro sicil numarası, büro adı) kullanıcının açık seçimini uygula ve `## Notlar`'a düş.

## 4. İmza bloğu seçimi

- Varsayılan: ad soyad ve baro adı kullanıcı isterse yazılır; baro sicil no, T.C. kimlik no, telefon, adres `[___]` olarak kalır.
- Gerekçe: profil her dilekçe becerisinde okunur; yer tutucu, avukatın son aşamada kendi bilgisini eklemesini ve taslağın "hazır" sanılmamasını sağlar (ORTAK-KURALLAR.md §13/7 sunma kapısı).

## 5. Yazmadan önce kullanıcıya sorulacak tek soru (paylaşılan bilgisayar)

Kurulum sırasında, profil yazılmadan önce yalnız bir kez:

> Bu bilgisayarı ya da kullanıcı hesabını başkasıyla paylaşıyor musunuz? Paylaşıyorsanız profile büro adı ve imza bilgisi yazmayalım; yalnız rol, taraf ve üslup kalsın.

Cevaba göre `Kurum/büro` ve imza bloğu alanlarını boş (`[ATLANDI]`) bırak.

## 6. Profilin silinmesi

Kullanıcı "profilimi sil" derse: dosya yolunu ve içeriğin özetini göster, onay al, sil (dosya sistemi varsa). Web/ChatGPT'de: "Proje talimatından bloğu silmeniz yeterli; eklenti ayrı bir kopya tutmaz. Eski sohbetlerin saklanması hesabınızın veri ayarlarına bağlıdır `[model bilgisi — doğrulayın]`." Silme sonrası beceriler "Profil: yok — genel cevap" moduna döner.
