# SGK itiraz dilekçesi (metin katmanı)

**Esas analiz bu dosyada değildir.** SGK idari para cezası (İPC), re'sen prim tahakkuku, yersiz teşvik geri alımı ya da denetim raporuna karşı itirazda **önce** `sosyal-guvenlik-sgk` becerisinin `../../sosyal-guvenlik-sgk/references/sgk-uyum-ve-itiraz.md` dosyasını oku ve oradaki işleri yap:

- süre tablosu (İPC → 15 gün Kurum, ret sonrası 30 gün **idare** mahkemesi; re'sen prim borcu → 1 ay Kurum, ret sonrası 1 ay **iş** mahkemesi) ve dayanakları (5510 m.102, m.86/7) — o dosyada soorgla ile doğrulandı;
- usul ve esas kontrol listesi (tebligat, zamanaşımı, fiilin oluşup oluşmadığı, ceza tutarının hesabı);
- soorgla çağrıları ve görüşme soruları (eski `data_schema` alanları).

Süreleri bu dosyaya kopyalamıyoruz: tek kaynak `../../sosyal-guvenlik-sgk/references/sgk-uyum-ve-itiraz.md`'dir; iki yerde tutulan süre zamanla ayrışır.

Bu dosya yalnızca o analizin çıktısını **dışarıya gidecek dilekçe metnine** çevirirken uygulanacak ek kuralları verir.

---

## Metin kuralları

1. **Makamı doğru yaz:** tebligatı gönderen birim (ör. "… Sosyal Güvenlik İl Müdürlüğü" ya da "… Sosyal Güvenlik Merkezi"). İPC itirazı Kuruma, ret sonrası dava idare mahkemesine; prim borcu itirazı Kuruma, ret sonrası dava iş mahkemesine. Bu dilekçe yalnızca **Kuruma itiraz** dilekçesidir; dava dilekçesi kapsam dışı.
2. **Süre cümlesi:** dilekçenin "Konu" satırının altına "Tebliğ tarihi: [___] — itiraz süresi içindedir." yaz; tebliğ tarihi yoksa `[___]` bırak ve süre hesabını değerlendirme bölümünde göster.
3. **Usul itirazları önce, esas itirazları sonra.** Her itiraz numaralı ve tek konulu.
4. **Peşin ödeme seçeneği** (İPC'de süresinde peşin ödemede indirim ve yargı yolu hakkının korunması) dilekçenin değil değerlendirmenin konusudur; dilekçede yer almaz, kullanıcıya ayrıca söylenir. Dayanak ve oranlar `../../sosyal-guvenlik-sgk/references/sgk-uyum-ve-itiraz.md`'de.
5. **Genelge atfı:** SGK genelgesine dayanırken numara ve tarihini yalnızca araç sonucundan aktar; genelgenin yargıyı bağlamadığını değerlendirmede belirt.
6. Dilekçede iç notlar ve kaynak etiketleri bulunmaz; dipnotta toplanır.

## Dilekçe iskeleti

`../../sosyal-guvenlik-sgk/references/sgk-uyum-ve-itiraz.md` dosyasının "Çıktı iskeleti — SGK itiraz dilekçesi" bölümündeki iskeleti kullan. Ek olarak:

```markdown
KONU             : [… tarih ve … sayılı … tebligatına (İPC / prim borcu / teşvik iptali) karşı itirazlarımızdır.]
                   Tebliğ tarihi: [___] — itiraz süresi içindedir.

İSTEM SIRASI     : 1) Usul yönünden iptal (tebligat, zamanaşımı, yetki)
                   2) Esas yönünden iptal (fiil oluşmamıştır / tutar hatalıdır)
                   3) Terditli: tutarın [___] olarak düzeltilmesi
```

## Sık hatalar

- 🔴 İPC ile prim borcunun yargı yerini karıştırmak (idare mahkemesi / iş mahkemesi).
- 🟠 Dilekçede peşin ödeme indirimini "talep" etmek (bu bir başvuru değil, ödeme davranışıdır).
- 🟡 Genelge numarasını tahmin etmek.

---

