# Makalenin Araştırma Yönteminin İncelenmesi

## 1. Araştırmanın Gerçekleştirildiği Ortam

Yanakiev, Lazar ve Capiluppi (2025) tarafından gerçekleştirilen araştırma, Hollanda merkezli ASML şirketinin mevcut C++ yazılım sistemi üzerinde yürütülmüştür.

Çalışmanın odak noktası, ASML'nin görüntüyle ilgili işlemler gerçekleştiren daha büyük bir fonksiyonel kümesinde yer alan "reticle align" yazılım deposudur.

Sistem, yirmi yılı aşkın geliştirme sürecinde çeşitli değişikliklere uğramış ve mimari düzeyde teknik borç biriktirmiştir. Araştırmacılar özellikle bileşenler arasındaki istenmeyen bağımlılıkları ve mimari kurallara aykırı ilişkileri azaltmayı hedeflemiştir.

## 2. Araştırma Yönteminin Genel Yapısı

Makalenin 4. Methodology bölümünde araştırma süreci beş temel aşama üzerinden açıklanmaktadır:

1. Mevcut şirket içi yazılım metriklerinin incelenmesi (Review of Available Internal Metrics).
2. Olası iyileştirmelerin etkilerinin değerlendirilmesi (Impact Analysis).
3. Bakım çalışmalarının önceliklendirilmesi (Prioritisation).
4. İlgili akademik literatürün incelenmesi (Literature Review).
5. Seçilen bileşenlerde refactoring işlemlerinin uygulanması (Implementation of Refactoring).

Bu süreç, hangi bileşenlerin yeniden düzenleneceğinin belirlenmesinden somut refactoring faaliyetlerine kadar uzanmaktadır.

## 3. Kullanılan Yazılım Metrikleri

Araştırmacılar, ASML'nin mevcut kalite izleme araçlarından elde edilen ölçümleri kullanmıştır.

Şirketin iç kuralları nedeniyle araştırma kapsamında ek dış statik analiz araçları kullanılamamıştır. Dolayısıyla değerlendirmeler, şirketin hâlihazırda topladığı verilerle sınırlandırılmıştır.

Makaledeki metrikler üç grupta incelenmektedir.

### 3.1. Kod Seviyesindeki Metrikler (Code-Level Metrics)

- **Cyclomatic Complexity:** Programdaki kontrol akışının karmaşıklığını ölçmektedir.
- **Code Coverage:** Testlerin kod üzerindeki kapsamına ilişkin bilgi sağlamaktadır.
- **Compiler Warnings:** Derleyici tarafından bildirilen uyarıların sayısını ifade etmektedir.

### 3.2. Kalite Metrikleri (Quality Metrics)

- **Coding Standards:** Kodun ASML'nin belirlediği yazılım geliştirme standartlarına uygunluğunu değerlendirmektedir.
- **Security:** Yazılımın güvenlik özellikleri ve bilinen güvenlik açıklarıyla ilgilidir.
- **Code Duplication:** Kod parçalarının tekrar edilme durumunu incelemektedir.

### 3.3. Mimari Metrikler (Architectural Metrics)

- **Fan Out:** Makaledeki tanımıyla mevcut bileşenin kaç başka bileşen tarafından kullanıldığını göstermektedir.
- **Abstract Interpretation:** Program çalıştırılmadan, soyut bir model üzerinden olası davranışların analiz edilmesine dayanmaktadır.
- **Dealed Interfaces:** Bir arayüzün doğrudan içerdiği arayüzlerin sayısını göstermektedir.
- **Indirectly Dealed Interfaces:** Bir arayüzün dolaylı olarak içerdiği arayüzlerin sayısını ifade etmektedir.
- **Build Dependencies:** Belirli bir arayüze bağımlı kaynak dosyaların sayısını göstermektedir.

Bu metrikler, yazılımın yalnızca kod kalitesini değil, mimari yapısını da değerlendirmeye yardımcı olmaktadır.

## 4. Etki Analizi (Impact Analysis)

Araştırmacılar, ölçüm sonuçlarını inceleyerek hangi problemlerin giderilmesinin araştırma açısından daha yararlı olacağını değerlendirmiştir.

Makalenin 4.2 bölümünde özellikle Fan Out, Code Duplication, Code Coverage ve Cyclomatic Complexity metrikleri tartışılmaktadır.

Değerlendirmede yalnızca metrik değerleri değil, ilgili sorunun giderilmesinin beklenen faydası, uygulama maliyeti ve araştırmanın hedefleriyle uyumu da dikkate alınmıştır.

Örneğin Fan Out probleminin azaltılması mimari açıdan önemli görülmüştür. Ancak bu tür bir iyileştirme birden fazla ekibin uzun süreli çalışmasını gerektirebileceği için araştırmanın sınırları içerisinde en yüksek önceliğe yerleştirilmemiştir.

## 5. Veriye Dayalı Önceliklendirme

Araştırmacılar, ölçüm sonuçlarını ASML mimarının değerlendirmeleriyle birlikte kullanarak beş seviyeli bir önceliklendirme oluşturmuştur.

Makaledeki Table 1'de belirtilen sıralama şöyledir:

| İyileştirme Alanı | Öncelik |
|---|---|
| Reduce Illegal Dependencies | Highest |
| Code Duplication | High |
| Fan Out | Average |
| Code Coverage | Low |
| Cyclomatic Complexity | Lowest |

Mimari kurallara aykırı bağımlılıkların azaltılması, araştırmanın temel hedefiyle doğrudan ilişkili olduğu için en yüksek önceliğe alınmıştır.

Kod tekrarı, bağımlılık düzenlemelerini kolaylaştırabilecek bir alan olarak değerlendirilmiştir.

Kod kapsamı ve döngüsel karmaşıklık gibi metrikler ise önemli olmakla birlikte araştırmanın mimari bağımlılıkları azaltma hedefine daha sınırlı katkı sağlayabilecekleri gerekçesiyle alt sıralarda yer almıştır.

Bu öncelikler ASML'deki araştırmanın koşullarına özgüdür; tüm yazılım projeleri için geçerli genel bir sıralama olarak değerlendirilmemelidir.

## 6. Refactoring İçin Bileşenlerin Seçilmesi

Önceliklendirme sürecinden sonra araştırmacılar, bakım faaliyetlerinin etkili olabileceği üç bileşen üzerinde yoğunlaşmıştır.

Makalenin 4.4 bölümünde bu bileşenler gizlilik nedeniyle A, B ve C olarak adlandırılmaktadır.

**Component A:** İki adet mimari kurallara aykırı çıkış bağımlılığı bulunmaktadır. Bu bileşende gerçekleştirilecek refactoring işlemlerinin B ve C bileşenlerindeki bağımlılık sorunlarının azaltılmasına da katkı sağlayabileceği değerlendirilmiştir. Bu nedenle ilk sırada yer almıştır.

**Component B:** Bir adet mimari kurallara aykırı giriş bağımlılığı bulunmaktadır. Bileşendeki sorunların giderilmesi önemli olmakla birlikte A bileşenindeki müdahalenin daha yüksek etki sağlayacağı değerlendirilmiştir.

**Component C:** Genel kod kalitesi diğer bileşenlere kıyasla daha iyi durumdadır. Üç adet mimari kurallara aykırı giriş bağımlılığı bulunmakla birlikte araştırma kapsamındaki önceliklendirmede üçüncü sırada değerlendirilmiştir.

Bileşenlerin seçimi yalnızca mevcut sorunların sayısına değil, bu sorunları gidermenin sistemin geri kalanına sağlayacağı katkıya da dayanmaktadır.

## 7. Araştırma Sorusu RQ1 ile İlişkisi

Makalenin ilk araştırma sorusu, veriye dayalı bir yaklaşımın mimari teknik borcun azaltılmasına yönelik bakım çalışmalarının önceliklendirilmesine nasıl katkı sağladığını incelemektedir.

Kullanılan yöntem, bu soruyla doğrudan ilişkilidir.

Araştırmacılar önce mevcut ölçümleri incelemekte, ardından olası iyileştirmelerin etkisini değerlendirmekte ve son olarak bakım açısından öncelikli bileşenleri belirlemektedir.

Böylece büyük ölçekli bir sistemde bütün sorunların aynı anda ele alınması yerine, araştırmanın hedeflerine ve mevcut kaynaklara uygun bir müdahale alanı seçilmektedir.

## 8. İlk Değerlendirme

Bu aşamadaki değerlendirmeme göre çalışmanın dikkat çekici yönlerinden biri, yazılım metriklerini doğrudan bir karar mekanizması olarak kullanmaktan ziyade endüstriyel kısıtlar ve uzman görüşleriyle birlikte değerlendirmesidir.

Araştırmacıların mevcut ölçümlerle sınırlı kalması, yöntemin endüstriyel koşullara uyarlanması açısından anlamlıdır. Bununla birlikte ek analiz araçlarının kullanılamaması, değerlendirilebilecek metriklerin kapsamını da sınırlandırmıştır.

Çalışmanın sonraki aşamalarında seçilen bileşenlerde uygulanan refactoring kalıpları ve elde edilen sonuçlar incelenerek bu yöntemin etkinliği daha ayrıntılı değerlendirilecektir.

## Kaynakça

Yanakiev, I., Lazar, B.-M., & Capiluppi, A. (2025). Applying SOLID principles for the refactoring of legacy code: An experience report. *Journal of Systems and Software, 220*, 112254. https://doi.org/10.1016/j.jss.2024.112254