# 3D yazıcı baskı sorunlarını tespit rehberi

FDM/FFF yazıcılarda **belirtiyi tarif etmek, olası nedenleri ayırmak ve güvenli bir sonraki adımı seçmek** için Türkçe başvuru kaynağı. Yeni başlayanlar, atölye kullanıcıları ve teknik destek ekipleri için hazırlanmıştır. Reçineli yazıcıları ve elektrik/elektronik onarımını kapsamaz.

Bir fotoğraf çoğu zaman kesin teşhis için yeterli değildir. Aynı boşluk, besleme sorunu veya yanlış dilimleme ayarı nedeniyle oluşabilir. Bu rehber, doğrudan parça değiştirmek yerine gözlemi kaydetmenize ve küçük, geri alınabilir denemelerle ihtimalleri daraltmanıza yardımcı olur. Buradaki test önerileri bir laboratuvar doğrulaması veya her yazıcı için sonuç garantisi değildir.

**Hazırlayan ve ticari ilişki:** [MetatechTR](https://store.metatechtr.com/), 3D yazıcı ürünleri satan bir mağazadır. Rehberdeki teknik kaynaklar üreticilerin resmî dokümantasyonudur; MetatechTR bağlantıları ticari bağlantı olarak açıkça ayrılmıştır. Rehberi uygulamak için satın alma gerekmez.

## Buradan başlayın

1. Aşağıdaki güvenlik kontrolünü okuyun.
2. Sorunun ne zaman başladığını karar ağacında bulun.
3. İlgili [ayrıntılı belirti kartını](docs/tespit-rehberi.md) açın.
4. [Deney günlüğüne](templates/deney-gunlugu.md) başlangıç durumunu yazın.
5. Yardım gerekirse [sorun bildirim şablonunu](.github/ISSUE_TEMPLATE/baski-sorunu.md) kullanın.

## Önce güvenlik

**Duman, yanık kokusu, kıvılcım, hasarlı kablo, sıcaklık güvenlik hatası veya kontrolsüz hareket varsa baskıyı sürdürmeyin.** Güvenliyse cihazın durdurma/kapatma prosedürünü uygulayın; dumanlı veya elektriksel tehlike bulunan alana yaklaşmayın. Tehlike geçmeden tekrar çalıştırmayın. Gerektiğinde acil yardım ve üretici desteği alın.

Normal baskı gözlemi uzaktan yapılır. Fiziksel inceleme için cihazın durmasını, güvenli şekilde kapatılmasını ve tamamen soğumasını bekleyin; üretici kılavuzundaki enerji ayırma adımlarını izleyin. Hareketli parçaları elle durdurmayın. Enerjili bağlantı sökme, sıcak nozul sıkma, güç kaynağı açma, sensör atlatma ve koruma devrelerini kapatma bu rehberin dışındadır.

Nozul çevresinde büyük plastik birikimi, hasarlı plaka veya tekrarlayan çarpışma varsa yeni deneme başlatmayın. Plastik yığınını kablo ve ısıtıcıdan zorla koparmayın. Rehberde geçen “kalibrasyon”, yalnızca modelinizin resmî kullanıcı prosedürüdür; başka cihazın Z ofseti, kayış gerginliği veya motor ayarını kopyalamak değildir.

## Belirtiye göre karar ağacı

```text
Güvenlik belirtisi var mı?
├─ Evet → Durdur; yeniden başlatma; üretici/servis desteği.
└─ Hayır → Sorun hangi aşamada?
   ├─ Baskı başlamadan
   │  ├─ Filament ilerlemiyor veya yükleme hatası → Kart 03 ve 16
   │  └─ Dosya/profil uyuşmuyor → Proje ve donanım kaydını doğrula
   ├─ İlk katmanda
   │  ├─ Çizgiler tutunmuyor veya sürükleniyor → Kart 01
   │  └─ Alt kenar taşmış veya yüzey kazınıyor → Kart 02
   ├─ Baskı sırasında
   │  ├─ Akış kesiliyor → Kart 03 ve 04
   │  ├─ Yüzeyde fazla malzeme birikiyor → Kart 05
   │  ├─ İnce teller oluşuyor → Kart 06
   │  ├─ Köşeler kalkıyor → Kart 07
   │  ├─ Katmanlar çatlıyor → Kart 08
   │  ├─ Üst bölüm yana kayıyor → Kart 09
   │  └─ Köprü/destek altı sarkıyor → Kart 12 ve 13
   └─ Bitmiş parçada
      ├─ Köşe sonrası dalga veya ince dikey iz → Kart 10
      ├─ Yatay bantlar → Kart 11
      ├─ Üst yüzeyde delik → Kart 14
      └─ Ölçü veya geçme uyumsuz → Kart 15
```

Birden fazla belirti varsa **ilk ortaya çıkanı** araştırın. Köşe kalktıktan sonra meydana gelen kayma, ilk olaydan bağımsız olmayabilir. “Son katman kötü” kaydı yerine “önce sağ köşe kalktı, ardından kafa sesi değişti, sonra X yönünde kayma görüldü” sıralaması daha değerlidir.

## Ayar değiştirmeden önce

Aynı projeyi ve mevcut profili ayrı adla saklayın. Yazıcı, nozul çapı, plaka yüzü ve filament seçiminin fiziksel donanımla eşleştiğini kontrol edin. Dilimleyici önizlemesinde parçanın tabladaki temasını, boşlukları, destekleri ve şüpheli katmanı inceleyin. Geometri dosyasında görünen kusuru mekanik arıza sanmayın.

**Asgari kayıt:** Yazıcı modeli ve yazılımı; nozul çapı/malzemesi; plaka türü/yüzü; dilimleyici sürümü; profil adları; filament ürün/malzeme/renk/partisi; saklama geçmişi; sıcaklık, hız, fan, akış ve geri çekme ayarları; model yönü; sorunun başladığı katman; son başarılı baskıdan sonra değişenler. Bilmediğiniz değeri tahmin etmeyin.

Ortamı da kaydedin: kabin durumu, kapı/pencere kaynaklı hava akımı ve ölçülmüşse sıcaklık/nem. Bir odanın nem değeri, filamentin içindeki nemi doğrudan ölçmez. Bir fotoğrafa bakarak “filament kesin nemli” demeyin. Malzemelerin nem davranışı farklıdır; saklama ve kurutma yöntemi ürünün kendi talimatına dayanmalıdır. [Prusa filament kurutma açıklaması](https://help.prusa3d.com/article/drying-filament_332086).

## Tek değişkenle deneme yöntemi

- **Bir soru seçin:** “Bu boşluk yalnızca hızlı bölgede mi oluşuyor?” gibi gözlenebilir bir soru yazın.
- **Başlangıcı koruyun:** Aynı model, makara, konum ve profil ile referans kaydı oluşturun. Tehlikeli veya çarpışan baskıyı referans uğruna tekrarlamayın.
- **Tek müdahale yapın:** Eski ve yeni ayarı, birimini ve gerekçeyi yazın. Üretici sınırlarından çıkmayın.
- **Sonucu önceden tanımlayın:** “Aynı iki sütun arasındaki iplik sayısı azalsın, duvarda yeni boşluk oluşmasın” gibi bir ölçüt belirleyin.
- **Geri alın veya doğrulayın:** Fayda yoksa önceki ayara dönün. Fayda varsa aynı küçük testi tekrarlayın; ardından asıl parçada kontrol edin.

Farklı bir makarayla iyi sonuç almak, eski makaranın nemli olduğunu tek başına kanıtlamaz: ürün, renk, parti ve sarım da değişmiş olabilir. Yazıcıyı, filament markasını ve beş ayarı aynı anda değiştirmek bir çözüm bulabilir ama nedeni göstermez. Başarısız denemeleri de saklayın; destek ekibinin aynı işlemleri tekrar önermesini önler.

## Yardım isterken

Parça soğuduktan sonra genel görünüm, kusurun yakını ve alt yüzey fotoğrafını paylaşın. Fotoğrafta baskı yönünü ve kusurun yerini belirtin. Ölçü sorunu varsa ölçüm aracını ve noktalarını yazın; görüntüye göre milimetre tahmini istemeyin. Güvenle çekilebiliyorsa hata anının kısa videosu yararlı olabilir; video için hareketli alana el veya kamera uzatmayın.

Proje dosyası STL'den daha fazla ayar bilgisi taşıyabilir, fakat özel tasarım ve kişisel bilgiler içerebilir. GitHub issue açmadan önce dosyayı, ekran görüntülerini ve günlükleri gözden geçirin. Seri numarası, adres, erişim anahtarı, Wi-Fi bilgisi ve müşteriye ait tasarımları herkese açık paylaşmayın. Başkasının G-code dosyasını doğrudan çalıştırmak yerine modeli kendi yazıcınızın doğrulanmış profiliyle dilimleyin.

## Kapsam ve katkı

Rehberde evrensel sıcaklık, geri çekme mesafesi, kurutma süresi veya cold pull tarifi verilmez. Nozul/hotend yapısı, plaka kaplaması, malzeme ve yazılım sürümü bu işlemleri değiştirebilir. Başlıklar olası nedenleri gösterir; arızalı bileşeni kesin olarak belirlemez.

Düzeltme önerirken belirti kartının numarasını, ilgili cihazı, kaynak bağlantısını ve hangi cümlenin neden değişmesi gerektiğini yazın. Yeni bir çözüm eklerken başlangıç koşullarını ve başarısız denemeleri de belirtin. Bir kullanıcı deneyimini bütün yazıcılarda geçerli kural olarak sunmayın. Güvenlik açısından şüpheli öneriyi uygulamak yerine işaretleyin.

Teknik dayanaklar ve kapsam notları [kaynaklar sayfasındadır](docs/kaynaklar.md). Buradaki bağlantılar marka bağımsız garanti veya üretici onayı anlamına gelmez. Kritik yük taşıyan, elektriksel güvenlik sağlayan veya insan güvenliğini etkileyen parçalar yalnızca görünüşüne bakılarak uygun kabul edilmemelidir.
