# İnfazın ertelenmesi ve infaza ara verilmesi

## Ne zaman kullanılır
Kesinleşmiş hapis cezasının infazının hastalık, gebelik/doğum ya da hükümlünün istemi (mazeret) nedeniyle geri bırakılması. Karar mercii **Cumhuriyet başsavcılığıdır** (infaz bürosu); mahkeme ya da infaz hâkimliği değil.

## Yollar ve dayanak

### A. Hastalık nedeniyle (5275 m.16)
- **Akıl hastalığı:** infaz geri bırakılır, TCK 57'deki sağlık kurumunda koruma ve tedavi; orada geçen süre cezaevinde geçmiş sayılır (16/1).
- **Diğer hastalıklar:** infaz kural olarak mahkûmlara ayrılmış hastane bölümünde sürer; ancak infaz **hayatı için kesin bir tehlike** oluşturuyorsa iyileşinceye kadar geri bırakılır (16/2).
- **Rapor:** Adli Tıp Kurumu raporu ya da Bakanlıkça belirlenen tam teşekküllü hastane sağlık kurulu raporu + **ATK onayı**; kararı **infazın yapıldığı yer Cumhuriyet başsavcılığı** verir; yükümlülükler belirlenir, sağlık durumu periyodik incelenir; yükümlülük ihlalinde karar kaldırılır ve buna karşı **infaz hâkimliğine** başvurulabilir (16/3).
- **Ağır hastalık/engellilik:** ceza infaz kurumu koşullarında hayatını yalnız idame ettiremeyen ve toplum güvenliği bakımından ağır ve somut tehlike oluşturmayacak mahkûmun infazı 16/3 usulüyle geri bırakılabilir (16/6). Bu durumda **konutta infaz** (m.110/3) seçeneğini de değerlendir → `konutta-infaz.md`.

### B. Gebelik ve doğum (5275 m.16/4-5)
- Gebe olan ya da doğurduğu tarihten itibaren **bir yıl altı ay** geçmemiş kadınların hapis cezasının infazı geri bırakılır; çocuk ölür ya da başkasına verilirse doğumdan iki ay sonra infaz edilir (16/4).
- İstisna: kapalı kuruma girdikten sonra gebe kalan ve koşullu salıverilmesine **altı yıldan fazla** kalanlar ile tehlikeli sayılanlar (16/5).
 (Eski YAML'daki "1 yıl 6 ay" doğru çıktı.)

### C. Hükümlünün istemiyle erteleme ve ara verme (5275 m.17)
- **Erteleme:** kasten işlenen suçlarda **üç yıl**, taksirle işlenen suçlarda **beş yıl** veya daha az hapis cezasının infazı, **çağrı üzerine gelen** hükümlünün istemiyle başsavcılıkça ertelenebilir (17/1). Her defasında **bir yılı geçmemek üzere en fazla iki kez** (17/2). Erteleme süresinde kasıtlı suçtan kamu davası açılırsa ceza derhal infaz edilir (17/3).
- **Ara verme:** infaza başlanmış olsa bile yükseköğrenimi bitirme, ana/baba/eş/çocuğun ölümü ya da sürekli hastalığı nedeniyle ailenin ticari/tarımsal faaliyetinin imkânsızlaşması, eş/çocuğun bakıma muhtaç olması, hükümlünün sürekli tedavi gerektiren hastalığı gibi **zorunlu ve çok ivedi** hâllerde bir yılı geçmeyen sürelerle, en fazla iki defa (17/4).
- Güvence ya da başka şart istenebilir (17/5).
- **Uygulanmaz:** terör suçları, örgüt faaliyeti çerçevesinde işlenen suçlar, cinsel dokunulmazlığa karşı suçlar; mükerrirlere özgü infaz rejimi; disiplin/tazyik hapsi (17/6).

**Eski bilgi düzeltildi:** eski YAML ara verme için "ceza miktarına bakılmaksızın" diyordu. Madde 17/4 açıkça "**birinci fıkrada belirtilen** hapis cezalarının infazına başlanmış olsa bile" der; yani ara verme de **3 yıl / 5 yıl** sınırındaki cezalarla sınırlıdır.

## Süre
- Hastalık ve gebelikte sabit başvuru süresi yok; durum ortaya çıkınca derhal.
- İstek üzerine erteleme (17/1): **çağrı kâğıdı üzerine gelen** hükümlü ister; çağrı kâğıdındaki teslim süresi içinde başvur.
- Başsavcılığın ret kararına karşı: **infaz hâkimliğine şikâyet**, öğrenmeden 15 gün / her hâlde 30 gün (4675 m.5/1 "Cumhuriyet savcısının ceza ve güvenlik tedbirlerinin infazına ilişkin verdiği kararlar") → `infaz-hakimligi-sikayet-ve-disiplin.md`.

## Görüşme soruları
1. Hükümlü bilgisi, ilam (mahkeme, esas/karar), kesinleşme tarihi, cezanın türü ve süresi `[___]`
2. Suç kasıtlı mı taksirli mi? Terör, örgüt, cinsel suç ya da mükerrir rejimi var mı?
3. Çağrı kâğıdı geldi mi, tarihi? Cezaevine girildi mi?
4. Gerekçe: hastalık (tanı, rapor, ATK sevki), gebelik/doğum tarihi, okul (hangi dönem), aile durumu (ölüm, bakım)?
5. Daha önce erteleme ya da ara verme kullanıldı mı, kaç kez?
6. Teminat gösterilebilir mi?

## soorgla adımları
```
legal_get_statute_article law_no: "5275" article_no: "16" | "17" | "19"
legal_get_statute_article law_no: "4675" article_no: "5"
legal_search_statute_semantic sorgu: "hükümlünün hastalığı nedeniyle infazın ertelenmesi Adli Tıp Kurumu raporu usulü"
legal_search_cases sorgu: "infazın hastalık nedeniyle ertelenmesi hayatı için kesin tehlike Adli Tıp raporu" tarih_baslangic: <son 3 yıl>
legal_search_cases mahkeme: "anayasa" sorgu: "ağır hasta hükümlünün cezaevinde tutulması yaşam hakkı kötü muamele yasağı"
legal_get_case_document belge_id: <seçilen karar>
```

## Dilekçe iskeleti
```
[İL] CUMHURİYET BAŞSAVCILIĞINA (İnfaz Bürosu)

HÜKÜMLÜ : [Ad Soyad], T.C. [___], [ilam: mahkeme, E./K. no, kesinleşme]
CEZA : [tür, süre] · SUÇ: [kasıtlı/taksirli — ___]
KONU : 5275 s. Kanun m.[16/2 | 16/4 | 16/6 | 17/1 | 17/4] uyarınca hapis cezasının infazının
            [ertelenmesi / infaza ara verilmesi] talebidir.
AÇIKLAMALAR
1. Yasal dayanak ve şartların varlığı (ceza miktarı, suç türü, istisna yokluğu)
2. Gerekçe (sağlık durumu / doğum tarihi / mazeret — belgeyle)
3. [Hastalıkta] ATK'ya sevk talebi / mevcut sağlık kurulu raporu
4. [17/5] Teminat beyanı
HUKUKİ NEDENLER: 5275 m.16, 17 [MCP'den çekilmiş]
EKLER: Rapor, doğum belgesi, öğrenci belgesi, ölüm belgesi [___]
SONUÇ VE İSTEM : [Dayanak] uyarınca infazın [süre] süreyle ertelenmesine / ara verilmesine;
                 [hastalıkta] Adli Tıp Kurumuna sevkime karar verilmesini saygıyla talep ederim.
```

## Sık hatalar
- 🔴 Dilekçeyi mahkemeye ya da infaz hâkimliğine vermek; mercii **başsavcılıktır** (ret üzerine infaz hâkimliği).
- 17/4 ara vermeyi her ceza miktarı için mümkün sanmak.
- Hastalıkta ATK sürecini atlamak; özel hastane raporu tek başına yetmez.
- 17/6 istisnalarını (terör, örgüt, cinsel suç, mükerrir) kontrol etmemek.
- Erteleme ile konutta infazı karıştırmak: erteleme cezayı durdurur; konutta infaz cezanın evde çekilmesidir.
