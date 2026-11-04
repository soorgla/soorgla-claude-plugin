# Hükümlünün kendi isteğiyle başka kuruma nakli

## Ne zaman kullanılır
Hükümlü aile ikametine yakın, eğitim ya da sağlık imkânı daha uygun bir ceza infaz kurumuna nakil istiyor. (Toplu sevk, disiplin, güvenlik, hastalık nedenli nakiller idarenin işlemidir; bunlara karşı yol için `infaz-hakimligi-sikayet-ve-disiplin.md`.)

## Dayanak ve şartlar
Nakil nedenleri 5275 m.53/1'de sayılır (kendi istek, toplu sevk, disiplin, asayiş ve güvenlik, hastalık, eğitim-öğretim, suç ve yargılama yeri). 

**Kendi isteğiyle nakil şartları (5275 m.54/1) — hepsi birlikte:** 
- (a) Gitmek istenen kurumlardan durumuna uygun **en az üç yeri** belirten dilekçe,
- (b) Nakil giderlerini **peşin ödemeyi kabul** — çocuk hükümlüler ve **maddi durumunun yetersiz olduğunu belgelendirenler** için aranmaz (6411 ek cümle),
- (c) Kurumda bulunulması gereken sürenin **üç aydan fazla** olması (7242 ile değişik),
- (d) İyi hâl; disiplin cezası almamış ya da cezası kaldırılmış olmak,
- (e) İstenen kurumda yer, kapasite ve sınıf uygunluğu; **tutukevi olmaması**,
- (f) Mahkûmiyet süresine uygun hükümlülerin barındırıldığı kurum olması,
- (g) Daha önce disiplin nedeniyle ayrılmak zorunda kalınan kurum olmaması.

**Nakledilen kurumda kalma:** eğitim-öğretim ya da hastalık nedenli nakil hariç **bir yıl** (çocuklarda altı ay) (54/2). Hükümlüyü bu konuda uyar. 

Açık kurumlar arası nakilde ayrıca Açık Ceza İnfaz Kurumlarına Ayrılma Yönetmeliği m.11 (en az üç kurum, peşin gider, Bakanlığa gönderim) uygulanır.  

Eski YAML'daki şartlar (54/1-a, b, c, d) doğru çıktı; (e), (f), (g) ve 54/2 eksikti, eklendi.

## Süre ve mercii
- Başvuru süresi yok.
- Dilekçe **bulunulan kurum müdürlüğü aracılığıyla** Adalet Bakanlığı Ceza ve Tevkifevleri Genel Müdürlüğüne gönderilir; infaz hâkimliğinin yetkisi kendi yargı çevresiyle sınırlı olduğundan **başka ildeki kuruma nakil** kararı Bakanlığındır (CTE Genel Müdürlüğü) ve yargı faaliyeti değil idari işlemdir.
- **Ret hâlinde:** AYM'ye göre iller arası nakil işlemine/reddine karşı tüketilmesi gereken etkili yol **idari yargıda iptal davasıdır** (İYUK m.2); infaz hâkimliğine götürülen nakil şikâyeti bu yolu tüketmiş saymaz (AYM İkinci Bölüm, Mesut Güney, B. No: 2021/26480, 17.07.2025, § 21-23; atıf: Y.Ş., B. No: 2017/37742, 18.06.2020). Kalabalık oda gibi **barınma koşullarına** ilişkin şikâyetler ise 4675 m.4 kapsamında infaz hâkimliğince esastan incelenmeli; incelenmeden ret etkili başvuru hakkını ihlal eder (aynı karar § 14-16). Dava açma süresini İYUK'tan çek (`legal_get_statute_article` 2577 m.7) `[incele]`. 
- Nakil masrafı tutarı beceri metnine yazılmaz; kurumdan öğrenilir `[doğrula]`.

## Görüşme soruları
1. Hükümlü: ad, T.C., baba adı, bulunduğu kurum, ilam/dosya no `[___]`
2. Kalan infaz süresi (müddetname) — üç aydan fazla mı?
3. Disiplin cezası var mı; kaldırıldı mı?
4. Tercih edilen en az üç kurum (sırayla)?
5. Gerekçe: ailenin ikameti, ziyaret güçlüğü, hasta yakın, eğitim, sağlık?
6. Nakil masrafını ödeyebilecek mi; ödeyemiyorsa yoksulluk belgesi var mı?
7. Daha önce disiplin nedeniyle ayrıldığı kurum var mı?

## soorgla adımları
```
legal_get_statute_article  law_no: "5275"  article_no: "53" | "54"
legal_search_statute_semantic  sorgu: "hükümlülerin kendi istekleriyle nakli usulü ceza infaz kurumları yönetmeliği"  mevzuat_tur: "cb_yonetmeligi"
legal_search_cases  mahkeme: "anayasa"  sorgu: "hükümlünün aileye yakın cezaevine nakil talebinin reddi aile hayatına saygı"
legal_get_case_document  belge_id: <seçilen karar>
```

## Dilekçe iskeleti
```
ADALET BAKANLIĞI CEZA VE TEVKİFEVLERİ GENEL MÜDÜRLÜĞÜNE
Sunulmak üzere
[KURUM] MÜDÜRLÜĞÜNE

HÜKÜMLÜ : [Ad Soyad], T.C. [___], Baba adı [___], [ilam/dosya no]
KONU    : 5275 s. Kanun m.54 uyarınca başka bir ceza infaz kurumuna nakil talebimdir.
NAKİL İSTENEN KURUMLAR (tercih sırasıyla):
 1. [___]  2. [___]  3. [___]
AÇIKLAMALAR
1. Şartlar: kalan infaz süresi [___] (3 aydan fazla); disiplin cezam yoktur / kaldırılmıştır; iyi hâlliyim.
2. Gerekçe: [aile ikameti, ziyaret güçlüğü — belgelerle]
NAKİL GİDERLERİ: Nakil giderlerini peşin ödemeyi kabul ediyorum.
                 [ya da: Maddi durumumun yetersizliğini gösteren belge ektedir (m.54/1 son cümle).]
HUKUKİ NEDENLER: 5275 m.53, 54 [MCP'den çekilmiş]
SONUÇ VE İSTEM : Yukarıda belirtilen kurumlardan birine naklime karar verilmesini saygıyla talep ederim.
```

## Sık hatalar
- Üçten az kurum yazmak.
- Tutukevine nakil istemek.
- Disiplin cezası kaldırılmadan başvurmak.
- Yeni kurumda bir yıl kalma zorunluluğunu söylememek.
- Masraf muafiyeti için belge eklememek.

