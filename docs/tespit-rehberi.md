# Ayrıntılı baskı sorunu tespit rehberi

[Başlangıç ve güvenlik kurallarına dön](../README.md) · [Deney günlüğü](../templates/deney-gunlugu.md)

Her kart aynı sırayı izler: belirti, olasılıklar, ayırıcı test, geri alınabilir adım, başarı ölçütü ve destek eşiği. Testler önce yazılım incelemesini ve güvenli gözlemi kullanır. Fiziksel müdahalede README'deki soğutma ve kapatma kuralları geçerlidir. Güvenlik hatasını yeniden üretmeye çalışmayın.

## 01 İlk katman tutunmuyor

**Belirti:** Çizgiler yüzeyden ayrılır, nozulun arkasında sürüklenir veya yalnızca belirli bir bölgede yapışmaz.

**Olasılıklar:** Yanlış plaka profili, yüzeyde kalıntı, malzeme/yüzey uyumsuzluğu veya ilk katman mesafesi. İlk katman hatasını yalnızca “tabla kirli” diye adlandırmayın. Yüzey hazırlığı ve kalibrasyon yöntemi plakaya ve yazıcıya göre değişir. [Resmî ilk katman açıklaması](https://help.prusa3d.com/article/first-layer-issues_1804).

**Ayırıcı test:** Önce profili kontrol edin. Güvenlik sorunu yoksa küçük bir ilk katman modelinin hangi bölgede bozulduğunu kaydedin. Aynı bölgenin tekrar etkilenmesi yerel bir koşulu araştırmayı gerektirir; tek başına eğri tabla kanıtı değildir.

**Geri alınabilir adım:** Üreticinin o plaka için onayladığı temizlik yöntemini uygulayıp aynı testi tekrarlayın. Sonuç değişmezse bunu kaydedin; kalibrasyonu ayrı adım olarak ele alın. Tutunmayı artırmak için nozulu körlemesine aşağı indirmeyin.

**Başarı:** Çizgiler birleşir, yerinden sürüklenmez; yüzey kazınmaz.

**Destek eşiği:** Kazıma, plaka hasarı, kalibrasyon hatası veya aynı bölgedeki tekrarlayan başarısızlık. Plaka ve alt yüzey fotoğraflarını ekleyin.

## 02 Alt kenar dışarı taşıyor veya ilk katman fazla eziliyor

**Belirti:** Parçanın tabanında dışa taşan bir dudak vardır; üst ölçüler doğru görünürken alt bölüm geçmeye engel olur.

**Olasılıklar:** İlk katman geometrisi ve ısı koşulları etkili olabilir. “Fil ayağı” olarak bilinen taban genişlemesi, bütün yükseklik boyunca ölçü hatasından farklı ele alınır. [Prusa fil ayağı telafisi](https://help.prusa3d.com/en/article/elephant-foot-compensation_114487).

**Ayırıcı test:** Tamamen soğuyan parçanın altını ve daha yukarıdaki aynı kesitini ölçün. Kusurun yalnızca ilk katmanlarda mı bulunduğunu belirleyin. İlk katmanda kazıma varsa ölçü denemesini bırakın.

**Geri alınabilir adım:** Önce doğru ilk katman profilini ve kullanıcı kalibrasyonunu doğrulayın. Sonrasında, dilimleyicinin belgelenmiş taban telafisini ayrı bir denemede kullanın. Bütün modeli küçültmek üst bölgeleri de değiştireceği için ilk tercih değildir.

**Başarı:** Alt taşma azalır; yapışma ve üst kesit ölçüsü bozulmaz.

**Destek eşiği:** Kalibrasyon sonrasında sürtme sürüyorsa veya plaka zarar görüyorsa test yerine servis değerlendirmesi gerekir.

## 03 Filament ilerlemiyor veya nozuldan çıkmıyor

**Belirti:** Yükleme başarısız olur, akış durur veya besleyici tıklar. Tıklama tek başına nozul tıkanıklığını kesinleştirmez.

**Olasılıklar:** Makara yolunda engel, besleme mekanizması veya hotend boyunca kısmi/tam tıkanma. Hotend tıkanması ile yalnızca nozul deliğinin tıkanması aynı şey değildir; doğrudan nozul satın almak sorunu çözmeyebilir. [Prusa tıkanıklık açıklaması](https://help.prusa3d.com/article/clogged-nozzle-hotend-mk3-5-s-mk3s-mk2-5s_2008).

**Ayırıcı test:** Hatanın yükleme sırasında mı, yalnızca baskıda mı oluştuğunu ayırın. Durdurulmuş ve soğumuş cihazda, sökmeden görülebilen filament yolunu ve makaraya dolanan serbest ucu inceleyin. Hata kodunu aynen kaydedin.

**Geri alınabilir adım:** Görünür dış engel giderilebiliyorsa yalnızca üreticinin yükleme prosedürüyle yeniden deneyin. Filamenti zorla itmeyin; iğne, yüksek sıcaklık veya genel bir cold pull tarifini uygulamayın.

**Başarı:** Resmî yükleme işlemi hatasız tamamlanır ve küçük testte akış kesilmez.

**Destek eşiği:** Tekrarlayan öğütme, içeride kırılan filament, çıkarılamayan malzeme veya söküm ihtiyacı. Sorunun başlangıç zamanı ve yükleme ekranı destek kaydına eklenmelidir.

## 04 Eksik ekstrüzyon ve çizgiler arasında boşluk

**Belirti:** Duvarlarda eksik malzeme, ince çizgiler veya yer yer kayıp katmanlar vardır.

**Olasılıklar:** Besleme direnci, yanlış profil, kısmi tıkanma veya istenen akışın sistem kapasitesini aşması. Yüksek hızdaki eksik akış ile düşük hızda da süren akış sorunu aynı şekilde değerlendirilmez. [Eksik ekstrüzyon](https://help.prusa3d.com/article/under-extrusion_2007) ve [hacimsel hız sınırı](https://help.prusa3d.com/article/max-volumetric-speed_127176).

**Ayırıcı test:** Dilimleyici önizlemesinde kusurlu bölgenin hızını ve hacimsel akışını inceleyin. Boşluk yalnızca hızlı/dolgun bölgelerde mi, tüm parçada mı? Güvenlik belirtisi yoksa aynı küçük geometride yalnızca uygun hız veya hacimsel akış sınırını azaltarak karşılaştırın.

**Geri alınabilir adım:** Yanlış nozul/malzeme profilini düzeltin; sonra tek bir hız değişikliğini değerlendirin. Akışı sürekli artırarak fiziksel bir besleme sorununu maskelemeyin.

**Başarı:** Eksik çizgiler kaybolur; yeni kabarma ve tıklama oluşmaz.

**Destek eşiği:** Doğrulanmış profil ve düşük talepli testte sorun sürüyorsa besleme/hotend incelemesi gerekir. Çatlayan parçayı yük taşıyan işte kullanmayın.

## 05 Fazla malzeme ve kabarık üst yüzey

**Belirti:** Üst çizgiler arasında sırtlar oluşur; yüzey pürüzlüdür veya nozul malzeme üzerinden geçerken iz bırakır.

**Olasılıklar:** Akış çarpanı, profil uyuşmazlığı veya yalnızca ilk katmanla ilgili ezilme. Her pürüz fazla ekstrüzyon değildir; başlangıç/bitiş noktası ve geometri de incelenmelidir. Akış kalibrasyonu malzeme ve profil bağlamında değerlendirilir. [Resmî akış çarpanı kalibrasyonu](https://help.prusa3d.com/article/extrusion-multiplier-calibration_2257).

**Ayırıcı test:** Kusurun yalnızca tabanda mı, bütün üst yüzeylerde mi olduğunu kontrol edin. Aynı düz üst yüzeyli küçük örnekte, doğru profil ile mevcut profilin farklarını listeleyin. Kalibrasyon yapılacaksa üreticinin bu cihaz için önerdiği yöntemi kullanın.

**Geri alınabilir adım:** Gereksiz özel akış değişikliğini kayıtlı varsayılanına döndürün. Aynı denemede sıcaklık ve çizgi genişliğini değiştirmeyin.

**Başarı:** Üst çizgiler birleşir ama sırt oluşturmaz; duvarlarda yeni boşluk çıkmaz.

**Destek eşiği:** Görünür çarpışma veya birden fazla malzemede açıklanamayan akış düzensizliği varsa mekanik değerlendirme isteyin.

## 06 İpliklenme ve sızıntı

**Belirti:** Ayrı bölgeler arasında ince teller veya geçiş sonunda küçük birikintiler kalır.

**Olasılıklar:** Malzeme davranışı, sıcaklık, geri çekme ve hareket yolları. Nem bir ihtimaldir, fotoğraftan kesin sonuç değildir. Doğrudan ve Bowden besleme gibi farklı sistemlerde aynı geri çekme ayarı geçerli sayılmaz. [Resmî ipliklenme açıklaması](https://help.prusa3d.com/article/stringing-and-oozing_1805).

**Ayırıcı test:** Aynı iki çıkıntı arasındaki telleri aynı açı ve ışıkla kaydedin. Önizlemede geçiş yolunu kontrol edin. Filament geçmişi belirsizse bunu yazın; kurutma ancak ürün ve makara için onaylı cihaz/prosedürle ayrı bir deney olmalıdır.

**Geri alınabilir adım:** Doğru malzeme profiline dönün. Ardından yalnızca bir sıcaklık veya geri çekme değişkenini üretici sınırları içinde deneyin. En az tel veren ayarın katman bütünlüğünü bozup bozmadığını da inceleyin.

**Başarı:** Teller azalırken duvarlarda boşluk ve başlangıç eksikleri oluşmaz.

**Destek eşiği:** İpliklenmeyle birlikte sürekli tıklama veya akış kesilmesi varsa önce Kart 03–04'e dönün; geri çekmeyi artırmaya devam etmeyin.

## 07 Köşe kalkması ve eğilme

**Belirti:** Parça ilk başta tutunur fakat köşeleri daha sonra yukarı kıvrılır. İlk çizginin hiç yapışmamasıyla aynı zaman çizelgesine sahip değildir.

**Olasılıklar:** Isıl büzülme, ortam değişimi, geniş geometri veya yüzey tutunması. Malzeme ve kabin gereksinimleri farklıdır. [Prusa warping açıklaması](https://help.prusa3d.com/article/warping_2011).

**Ayırıcı test:** Kalkmanın ilk görüldüğü katmanı, tarafı ve o sıradaki ortam koşulunu yazın. Bir köşe sürekli açık pencere tarafındaysa hava akımı bir hipotezdir; gözlem nedenselliği kanıtlamaz.

**Geri alınabilir adım:** Üreticinin çalışma koşullarını bozmadan doğrudan hava akımını giderin veya ayrı bir denemede uygun brim kullanın. Brim, parçanın etrafındaki sökülebilir temas şerididir. Cihazın etrafına rastgele kapalı kutu yapmayın; havalandırmayı ve elektronik soğutmasını engellemeyin.

**Başarı:** Köşeler baskı boyunca yerinde kalır; soğuyan parça hedef düzlüğü sağlar.

**Destek eşiği:** Kalkmış parça nozula çarpıyorsa baskıyı durdurun. Büyük geometride devam eden sorun için malzeme, yönlendirme ve ortamı birlikte fakat ayrı deney kayıtlarıyla değerlendirin.

## 08 Katman ayrılması ve çatlama

**Belirti:** Parçada katman doğrultusunda çatlak veya ayrılma görülür. Eksik malzeme çizgisini gerçek çatlamadan ayırmak gerekir.

**Olasılıklar:** Profildeki sıcaklık/soğutma koşulları, ortam etkisi veya yetersiz malzeme birikimi. Katman ayrılması ve eksik ekstrüzyon benzer görünebilir. [Resmî katman ayrılması açıklaması](https://help.prusa3d.com/article/layer-separation-and-splitting-fdm_1806).

**Ayırıcı test:** Soğumuş parçadaki ayrılmayı yakın çekimde inceleyin: kesintisiz bir çatlak mı, yoksa baskı boyunca ince ve eksik çizgiler mi? Hatanın oluştuğu an bilinmiyorsa bunu açıkça yazın. Önizlemede aynı yükseklikte profil veya geometri değişimi olup olmadığını kontrol edin.

**Geri alınabilir adım:** Malzemeye uygun resmî profili doğrulayın. Yalnızca belgelenmiş tek soğutma ya da sıcaklık parametresini değiştirin; sınırları aşarak katmanları “kaynatmaya” çalışmayın.

**Başarı:** Tekrarlanan testte görünür ayrılma olmaz. Görsel başarı, mekanik dayanım sertifikası değildir.

**Destek eşiği:** Doğru profil ve düzenli akışa rağmen ayrılma sürüyorsa üreticiye başvurun. Parçayı elle kırarak yapılan kontrolü güvenlik açısından kritik kullanımın doğrulaması saymayın.

## 09 Katman kayması

**Belirti:** Belirli bir yükseklikten sonra üst bölüm X/Y düzleminde yer değiştirir; önceki duvarlarla hizalanmaz.

**Olasılıklar:** Eksen hareketindeki engel, çarpışma veya hareket mekanizmasıyla ilgili sorunlar. Kayış ve kasnaklar olası başlıklardır ama fotoğraf hangi bileşenin arızalı olduğunu göstermez. [Resmî katman kayması açıklaması](https://help.prusa3d.com/article/layer-shifting_2020).

**Ayırıcı test:** Kaymanın yönünü işaretleyin. Öncesinde köşe kalkması, destek devrilmesi veya anormal ses oldu mu? Dilimleyici önizlemesinde aynı kayma var mı? Kayma yalnızca fiziksel baskıdaysa proje görüntüsüyle gerçek parçayı birlikte paylaşın.

**Geri alınabilir adım:** Soğuk ve kapalı cihazın çevresindeki dış engelleri kaldırın. Üreticinin doğrulanmış hız profilini kullanın. Kayışı sesine göre gelişigüzel germeyin; hareket sistemini elle zorlamayın.

**Başarı:** Sorunlu yüksekliği içeren küçük güvenli testte hizalama korunur; çarpışma olmaz.

**Destek eşiği:** Tekrarlayan çarpışma, mekanik sürtme veya güvenli gözlemle açıklanamayan kayma. Kayıtlı hata/çarpışma günlüğünü silmeden destek alın.

## 10 Köşe sonrası dalgalar ve ince dikey izler

**Belirti:** Keskin köşeden sonra tekrarlayan dalgalar veya düz duvarda düzenli ince dikey çizgiler görülür.

**Olasılıklar:** Köşe sonrasındaki dalgalar ringing/ghosting ile uyumlu olabilir. Bu görünüm hareket titreşimi değerlendirmesine yönlendirir. [Prusa ghosting açıklaması](https://help.prusa3d.com/article/ghosting_1801). Düz duvardaki ince dikey izlere bazen VFA denir; bu etiket belirli motor, kayış veya rulman arızasını kanıtlamaz.

**Ayırıcı test:** Aynı parçayı yandan ışıkla fotoğraflayın. İzler yalnızca köşeden sonra mı başlıyor, bütün duvarda mı? Güvenli ve üretici sınırları içindeki tek dış duvar hızı değişikliğini karşılaştırın. İz sıklığı ve şiddetini ayrı not edin.

**Geri alınabilir adım:** Doğru hareket profilini geri yükleyin. Cihaz destekliyorsa yalnızca resmî titreşim kalibrasyonunu kullanın; rastgele motor akımı veya firmware parametresi değiştirmeyin.

**Başarı:** Aynı ışıkta dalga görünürlüğü azalır, ölçü ve köşe şekli bozulmaz.

**Destek eşiği:** Standart profilde devam eden düzenli izleri üreticiye gönderin. Fotoğrafla ringing/VFA ayrımı yapılamıyorsa kayda “ince dikey yüzey izi, neden belirsiz” yazın.

## 11 Yükseklik boyunca yatay bantlar

**Belirti:** Duvarlarda belli yüksekliklerde çıkıntı veya çöküntü bantları vardır; bütün parça yana kaymış değildir.

**Olasılıklar:** Geometri, katman süresi, akış veya mekanik hareket incelenebilir. Her yatay iz eğri Z mili değildir. Örneğin Benchy gövde çizgisi, geometri ve baskı koşullarıyla ilişkili ayrı bir örnektir. [Resmî Benchy gövde çizgisi açıklaması](https://help.prusa3d.com/article/the-benchy-hull-line_124745).

**Ayırıcı test:** Bantların tabandan yüksekliğini ölçün. Önizlemede aynı yerde dolgu, duvar, hız veya kesit değişimi var mı? Daha basit, benzer yükseklikte bir örnek ile karşılaştırın. Aynı fiziksel yükseklikte tekrar etmesi mekanik inceleme için veri sağlar, kesin teşhis değildir.

**Geri alınabilir adım:** Önce değişken katman/özel modifiye ayarlarını ayrı bir denemede kaldırın. Üretici talimatı olmadan Z bileşenlerini gevşetmeyin veya yağlamayın.

**Başarı:** Önceden tanımlanmış bant aynı testte azalır; toplam yükseklik ve duvar bütünlüğü korunur.

**Destek eşiği:** Farklı basit geometrilerde aynı yüksekliklerde tekrar eden bantları, ölçüleri ve bakım geçmişini servisle paylaşın.

## 12 Köprüler ve desteksiz çıkıntılar sarkıyor

**Belirti:** İki dayanak arasındaki çizgiler aşağı sarkar veya eğimli çıkıntının altı bozulur. Köprü ile tek taraftan uzayan çıkıntı aynı geometri değildir.

**Olasılıklar:** Desteksiz mesafe, model yönü ve köprüye özel hız/soğutma/akış davranışı. Köprüdeki değişiklik bütün modelin fanını artırmakla eşdeğer değildir. [Resmî köprüleme açıklaması](https://help.prusa3d.com/article/poor-bridging_1802).

**Ayırıcı test:** Önizlemede çizgilerin gerçekten iki uca bağlanıp bağlanmadığını kontrol edin. Modelin yalnızca sorunlu bölümünü içeren küçük bir örnek kullanın; ilk köprü çizgisi ile üst katmanları ayrı değerlendirin.

**Geri alınabilir adım:** Önce model yönünü veya destek ihtiyacını inceleyin. Ardından yalnızca köprüye özel tek parametreyi üreticinin profil sınırlarında deneyin. Desteksiz mesafeyi azaltmak için destek eklemek, bütün makine ayarını değiştirmekten daha anlaşılır bir test olabilir.

**Başarı:** Sarkma hedef kullanım için kabul edilebilir hale gelir; dayanaklarda ayrılma oluşmaz.

**Destek eşiği:** Standart küçük köprüde bile akış kesiliyorsa Kart 04'e dönün. Belirli bir geometri cihaz/malzemenin erişebileceği yüzey kalitesini aşabilir.

## 13 Destek devriliyor veya parçadan ayrılmıyor

**Belirti:** Destek baskı sırasında düşer ya da baskı sonunda parçaya kaynamış gibi kalır. Bunlar aynı sorun değildir.

**Olasılıklar:** Destek tabanı/yerleşimi, ince ve uzun yapı, arayüz geometrisi veya temas boşluğu. Farklı destek malzemeleri aynı ayrılma davranışına sahip değildir. [Resmî destek ayarları](https://help.prusa3d.com/article/support-material_1698).

**Ayırıcı test:** Önizlemede desteğin tabladan veya modelden nasıl başladığını inceleyin. Devrilmede ilk kopan yeri, ayrılmama durumunda yapışan arayüzü kaydedin. Tüm modeli yeniden basmak yerine bu bölgenin küçük bir kesitini kullanın.

**Geri alınabilir adım:** Devrilmede yalnızca destek yerleşimini/temasını; ayrılmamadaysa yalnızca belgelenmiş arayüz ayarını değiştirin. Çözünür destek için kullanılan sıfır boşluk yaklaşımını aynı malzemeli desteğe kopyalamayın.

**Başarı:** Destek baskı boyunca kalır ve soğuyan parçadan kabul edilebilir yüzeyle ayrılır.

**Destek eşiği:** Destekler nozula çarpıyorsa durdurun. Sökme sırasında zorlayarak elinize doğru kesici uygulamayın; keskin parçalar için göz koruması ve uygun üretici yöntemi kullanın.

## 14 Üst yüzeyde delikler ve kapanmayan alanlar

**Belirti:** Son katmanlarda dolgu görünür, küçük boşluklar veya aşağı çöken bölgeler kalır.

**Olasılıklar:** Yetersiz üst kabuk, altındaki geniş boşluklar, köprüleme davranışı veya genel eksik ekstrüzyon. Bu kart, [eksik ekstrüzyon](https://help.prusa3d.com/article/under-extrusion_2007) ve [köprüleme](https://help.prusa3d.com/article/poor-bridging_1802) kontrollerini üst yüzey için birleştirir.

**Ayırıcı test:** Önizlemede üst katmanların sayısını, kalınlığını ve altındaki dolgu desteğini inceleyin. Yan duvarlarda da boşluk varsa yalnızca üst katman ayarına odaklanmayın. Boşluğun her örnekte aynı geometride mi olduğunu kaydedin.

**Geri alınabilir adım:** İlk denemede yalnızca üst kabuk kalınlığını uygun profil kapsamında değiştirin. Sonuç yoksa eski ayara dönüp dolgu desteğini ayrı değerlendirin. Hem dolgu oranını hem akışı hem fanı değiştirmek karşılaştırmayı belirsizleştirir.

**Başarı:** Üst yüzey kapanır; yeni kabarma veya nozul sürtmesi oluşmaz.

**Destek eşiği:** Sağlam desteklenen küçük bir üst yüzeyde de boşluk sürüyorsa besleme ve akış kartlarına dönün. Üstü kapalı görünmesi iç yapının sağlam olduğunu kanıtlamaz.

## 15 Ölçü ve geçme uyumsuzluğu

**Belirti:** Delik dar, mil kalın, kapak sıkı veya parçanın bir ekseni hedef ölçüden farklıdır.

**Olasılıklar:** Tasarım boşluğu, alt kenar taşması, yönlendirme veya genel baskı koşulları. Taban hatasını bütün parçaya uygulanan ölçekleme ile düzeltmek yeni sorunlar oluşturabilir. [Fil ayağı telafisinin kapsamı](https://help.prusa3d.com/en/article/elephant-foot-compensation_114487).

**Ayırıcı test:** Parça tamamen soğuyunca aynı ölçüm aracıyla farklı yüksekliklerde ölçün. Hedefi, gerçekleşeni, ekseni ve ölçüm noktasını yazın. İki parçalı geçmede yalnızca deliği değil eşleşen parçayı da ölçün. Tasarımın gerçekten boşluk içerip içermediğini kontrol edin.

**Geri alınabilir adım:** Yerel sorunda yerel tasarım/telafi değişikliğini deneyin. Tek küçük küpün sonucuyla bütün yazıcının eksen adımlarını değiştirmeyin. Yeni profilin diğer ölçüler üzerindeki etkisini kaydedin.

**Başarı:** Kullanım için önceden belirlenmiş tolerans ve geçme sağlanır; diğer kritik ölçüler bozulmaz.

**Destek eşiği:** Farklı boyut ve yönlerde tekrarlanan ölçü sorunu için ölçüm tablosunu paylaşın. Güvenlik kritik parçaların uygunluğu bu pratik testle belirlenmez.

## 16 Çoklu makara sisteminde yükleme veya geri sarma hatası

**Belirti:** AMS veya benzeri sistem yükleyemez, geri çekemez ya da sürekli aynı kanalda hata verir.

**Olasılıklar:** Makara hareketi, filament yolu veya sistemin kendi hata koduyla tarif ettiği durum. Sistem adı tek başına makara ve filament uyumluluğunu belirlemez. Bu kart bir ürün uyumluluk tablosu değildir.

**Ayırıcı test:** Sistemin tam modelini, kanalını, hata kodunu, makarayı ve filament ürününü yazın. Hata makarayla mı, kanalla mı birlikte yer değiştiriyor sorusunu yalnızca üreticinin izin verdiği yükleme/değiştirme prosedürleriyle araştırın. Her seferinde tek unsur değişsin. Uyumluluğu doğrulanmamış malzemeyle deneme yapmayın.

**Geri alınabilir adım:** Görünür dış engelleri cihaz güvenli durumdayken giderin; onaylı makara yerleşimini doğrulayın. Otomatik sistemi zorlamayın, filament yolunu rastgele değiştirmeyin. Harici besleme seçeneği ancak cihazın kılavuzu izin veriyorsa ayrı test olabilir.

**Başarı:** Aynı kanalda yükleme, kısa baskı ve boşaltma hatasız tamamlanır.

**Destek eşiği:** Aynı kodun tekrarı, içeride kırılma veya söküm ihtiyacı. Üreticiye tam sistem modelini verin; farklı AMS sürümleri için tek bir uyumluluk kuralı kullanmayın.

## Sonucu nasıl kapatmalı

“Düzeldi” yerine koşulları yazın: hangi profil, makara ve modelde; hangi tek değişiklikle; kaç tekrar sonunda; hangi ölçüte göre başarılı? Asıl parçada henüz denenmediyse sonucu “küçük testte iyileşti” olarak bırakın. Hata yeniden çıkarsa önceki dosyayı değiştirmeyin; yeni kayıt numarası açıp eski kayda bağlayın.

Henüz neden bulunamadıysa “sebep belirsiz” geçerli bir sonuçtur. Denemeleri artırmak yerine eksik veriyi belirleyin: hata kodu, profil farkı, ilk olayın videosu veya üretici prosedürünün sonucu. Parça değiştirme kararı, yalnızca yüzey kusuruna veya mağaza ürün açıklamasına değil bu kayda dayanmalıdır.
