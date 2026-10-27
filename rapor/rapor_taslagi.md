# SOLID Tasarım Prensiplerinin Legacy Code Refactoring Sürecinde Kullanımı: Akademik Makale İncelemesi

## 1. Giriş

*Bu bölümde araştırmanın konusu, önemi ve incelemenin amacı açıklanacaktır.*

## 2. Makalenin Amacı ve Araştırma Soruları

Yanakiev, Lazar ve Capiluppi (2025) tarafından gerçekleştirilen araştırma, uzun yıllar boyunca geliştirilen yazılım sistemlerinde biriken mimari teknik borcun azaltılmasına odaklanmaktadır. Çalışma, Hollanda merkezli ASML şirketinin mevcut C++ yazılım sistemi üzerinde gerçekleştirilen endüstriyel bir refactoring deneyimini incelemektedir.

Araştırmada ele alınan temel problem, yazılım geliştirme standartları ve analiz araçları kullanılmasına rağmen bileşenler arasında sıkı bağlılıkların ve mimari kurallara aykırı bağımlılıkların oluşmasıdır. Bu tür sorunlar, yazılımın bakımını ve gelecekte geliştirilmesini zorlaştırmaktadır.

Çalışmanın temel amacı, mevcut yazılım ölçümlerinden yararlanarak bakım açısından öncelikli üç bileşeni belirlemek ve bu bileşenlerde SOLID tasarım prensiplerini uygulamaktır. Araştırmacılar özellikle Dependency Inversion Principle (DIP) prensibinin somut ve tekrarlanabilir refactoring işlemlerine dönüştürülmesini ele almaktadır.

Bu kapsamda çalışma iki araştırma sorusuna dayanmaktadır:

**RQ1 — Veriye Dayalı Önceliklendirme:** Veriye dayalı bir yaklaşım, endüstriyel ortamda mimari teknik borcun azaltılmasına yönelik çalışmaların önceliklendirilmesine nasıl katkı sağlar?

İlk araştırma sorusu, büyük ölçekli bir yazılım sisteminde bakım çalışmalarına hangi bileşenlerden başlanması gerektiğiyle ilgilidir. Araştırmacılar, mevcut yazılım ve süreç ölçümlerinin önceliklendirme kararlarını nasıl destekleyebileceğini incelemektedir.

**RQ2 — SOLID Prensiplerinin Somutlaştırılması:** SOLID tasarım prensipleri, mevcut yazılım sisteminde uygulanabilecek somut refactoring kalıplarına nasıl dönüştürülebilir?

İkinci araştırma sorusu, teorik tasarım prensiplerinin gerçek yazılım koduna nasıl uygulanabileceğine odaklanmaktadır. Özellikle DIP prensibinin uygulanması için gerekli kod düzenlemelerinin belirlenmesi ve bunların tekrarlanabilir kalıplar hâline getirilmesi araştırılmaktadır.

Bu iki soru birlikte değerlendirildiğinde RQ1'in hangi bileşenlere müdahale edileceğini, RQ2'nin ise bu bileşenlerin nasıl yeniden düzenleneceğini ele aldığı görülmektedir. Dolayısıyla çalışma, mimari teknik borcun azaltılmasında hem önceliklendirme hem de uygulama aşamalarını kapsamaktadır.

## 3. Teorik Arka Plan

### 3.1. Nesneye Dayalı Programlama (OOP)
Nesneye Dayalı Programlama (Object-Oriented Programming — OOP), yazılım sistemlerinin sınıflar ve nesneler aracılığıyla modellenmesine dayanan bir programlama paradigmasıdır. OOP yaklaşımı; kapsülleme (encapsulation), soyutlama (abstraction), kalıtım (inheritance) ve çok biçimlilik (polymorphism) gibi temel kavramları içermektedir.

Kapsülleme, bir nesnenin verilerinin ve bu veriler üzerinde gerçekleştirilen işlemlerin bir arada tutulmasını, nesnenin iç durumuna erişimin kontrollü şekilde yönetilmesini ifade etmektedir. Soyutlama, yazılım bileşenlerinin temel işlevlerini ön plana çıkarırken uygulama ayrıntılarını gizlemeyi amaçlamaktadır.

Kalıtım, sınıflar arasında tür ilişkileri kurulmasına ve belirli özelliklerin devralınmasına olanak sağlamaktadır. Çok biçimlilik ise farklı nesnelerin ortak bir üst tür veya arayüz üzerinden kullanılabilmesini mümkün kılmaktadır.

Bu kavramlar, büyük ölçekli yazılım sistemlerinde bileşenlerin sorumluluklarını ve birbirleriyle olan ilişkilerini düzenlemek açısından önem taşımaktadır. Bununla birlikte, OOP mekanizmalarının kullanılması tek başına sürdürülebilir bir yazılım mimarisi oluşturulduğu anlamına gelmemektedir. Bileşenler arasındaki bağımlılıkların uygun şekilde tasarlanması da gerekmektedir.

### 3.2. SOLID Tasarım Prensipleri
SOLID, nesneye dayalı yazılım tasarımında bakım yapılabilirliği, genişletilebilirliği ve esnekliği desteklemeyi amaçlayan beş temel tasarım prensibinin baş harflerinden oluşmaktadır.

Single Responsibility Principle (SRP): Bir sınıfın değişmesi için tek bir temel neden bulunması gerektiğini ifade etmektedir. Sınıfların farklı sorumluluklarla gereğinden fazla yüklenmesini önlemeye yönelik bir tasarım yaklaşımıdır.

Open/Closed Principle (OCP): Yazılım bileşenlerinin genişletilmeye açık, mevcut kodlarının değiştirilmesine ise mümkün olduğunca kapalı olması gerektiğini belirtmektedir. Yeni özelliklerin mevcut bileşenler üzerinde gereksiz değişikliklere neden olmadan eklenmesini hedeflemektedir.

Liskov Substitution Principle (LSP): Bir alt türün, üst türün yerine kullanıldığında beklenen davranış sözleşmesini koruması gerektiğini ifade etmektedir. Bu prensip, özellikle kalıtım ilişkilerinin doğru tasarlanması açısından önem taşımaktadır.

Interface Segregation Principle (ISP): Yazılım bileşenlerinin kullanmadıkları arayüz metotlarına bağımlı olmaya zorlanmaması gerektiğini belirtmektedir. Gereksiz bağımlılıkları azaltmak amacıyla arayüzlerin sorumluluklarına göre ayrılmasını desteklemektedir.

Dependency Inversion Principle (DIP): Yüksek seviyeli modüllerin düşük seviyeli modüllerin somut uygulamalarına değil, soyutlamalara bağımlı olması gerektiğini ifade etmektedir. Soyutlamaların uygulama ayrıntılarından bağımsız tutulması ve somut bileşenlerin bu soyutlamalara uygun şekilde geliştirilmesi amaçlanmaktadır.

SOLID prensipleri, OOP'nin sunduğu soyutlama, kalıtım ve çok biçimlilik gibi mekanizmaların daha sürdürülebilir tasarım kararlarıyla kullanılmasına rehberlik etmektedir.

İncelenen Yanakiev, Lazar ve Capiluppi (2025) çalışmasında SOLID prensipleri, mevcut C++ yazılım sistemindeki mimari teknik borcun azaltılmasında temel tasarım yaklaşımı olarak ele alınmaktadır. Araştırmanın uygulama aşamasında özellikle Dependency Inversion Principle (DIP) üzerinde durulmaktadır.

Bu bağlamda makale, nesneye dayalı tasarım prensiplerinin büyük ölçekli endüstriyel yazılım sistemlerindeki mimari bağımlılık sorunlarının giderilmesinde nasıl kullanılabileceğini ortaya koymayı amaçlamaktadır.

### 3.3. Legacy Code ve Teknik Borç

Legacy Code (miras kod), geçmişte geliştirilmiş ve günümüzde kullanılmaya devam edilen mevcut yazılım kodunu ifade etmektedir. Bu tür sistemler, uzun yıllar boyunca farklı gereksinimler doğrultusunda değiştirilmiş ve genişletilmiş olabilir. Bir yazılımın eski olması, mutlaka hatalı veya işlevsiz olduğu anlamına gelmemektedir. Bununla birlikte, zaman içerisinde oluşan karmaşık bağımlılıklar, yetersiz dokümantasyon ve tasarım sorunları mevcut sistemlerin bakımını zorlaştırabilmektedir.

Bu sorunlarla ilişkili temel kavramlardan biri Technical Debt (Teknik Borç) olarak adlandırılmaktadır. Teknik borç, yazılım geliştirme sürecinde alınan tasarım ve uygulama kararlarının gelecekte ek bakım ve geliştirme maliyetlerine neden olmasını ifade etmektedir. Teknik borç, kısa vadede zaman kazanmak amacıyla yapılan bilinçli tercihler sonucunda oluşabileceği gibi yazılımın zaman içerisinde değişen gereksinimlere yeterince uyarlanamaması nedeniyle de birikebilmektedir.

Teknik borç farklı seviyelerde ortaya çıkabilmektedir. Kod seviyesindeki teknik borç (Code-Level Technical Debt), metotların ve sınıfların iç yapısındaki karmaşıklıklar, tekrarlanan kod parçaları veya sorumlulukların uygun şekilde ayrılmaması gibi sorunları kapsamaktadır.

Mimari teknik borç (Architectural Technical Debt) ise daha geniş bir düzeyde, yazılım bileşenlerinin organizasyonu ve birbirleriyle olan bağımlılık ilişkilerinden kaynaklanmaktadır. Bileşenler arasında sıkı bağlılıkların oluşması, çok sayıda bağımlılığın bulunması ve mimari kuralların ihlal edilmesi bu tür teknik borcun örnekleridir.

Yanakiev, Lazar ve Capiluppi (2025) tarafından gerçekleştirilen araştırma, özellikle mimari teknik borcun azaltılmasına odaklanmaktadır. Çalışmada, ASML şirketinin yaklaşık yirmi yıllık geliştirme geçmişine sahip C++ yazılım sisteminde, kodlama standartları ve analiz araçları kullanılmasına rağmen mimari bağımlılık sorunlarının devam ettiği belirtilmektedir.

Araştırmacılar bu bağlamda özellikle sıkı bağlılık (tight coupling), fazla sayıda dış bağımlılık (large fan-out) ve mimari kurallara aykırı bağımlılıklar (illegal dependencies) üzerinde durmaktadır. Bu sorunlar, mevcut yazılım sisteminde bakım faaliyetlerinin karmaşıklığını artırabilen mimari teknik borç unsurları olarak ele alınmaktadır.

Dolayısıyla makalenin temel problemi, yalnızca eski kodların okunabilirliğini iyileştirmek değil, büyük ölçekli bir yazılım sistemindeki bileşenler arası ilişkileri daha sürdürülebilir biçimde yeniden düzenlemektir.

### 3.4. Refactoring Kavramı

Refactoring (yeniden düzenleme), bir yazılımın dışarıdan gözlemlenen davranışı korunurken iç yapısının iyileştirilmesi işlemidir. Bu yaklaşım, mevcut kodun bakım yapılabilirliğini, anlaşılabilirliğini ve gelecekte değiştirilebilirliğini artırmayı amaçlamaktadır.

Refactoring işlemleri arasında uzun metotların daha küçük metotlara ayrılması, sınıfların sorumluluklarının yeniden düzenlenmesi ve yazılım bileşenleri arasındaki bağımlılıkların iyileştirilmesi yer alabilmektedir.

Refactoring, yeni özellik geliştirme veya mevcut bir hatayı düzeltme işlemlerinden farklıdır. Temel amaç, sistemin sunduğu işlevleri değiştirmeden yazılımın iç tasarımını iyileştirmektir. Bu nedenle refactoring sürecinde mevcut davranışın korunmasının doğrulanması önem taşımaktadır.

İncelenen makalede refactoring, büyük ölçekli bir C++ yazılım sistemindeki mimari bağımlılık problemlerini azaltmak amacıyla kullanılmaktadır. Araştırmacılar, bakım açısından öncelikli bileşenleri belirledikten sonra bu bileşenler üzerinde SOLID tasarım prensiplerinden yararlanarak yeniden düzenleme işlemleri gerçekleştirmektedir.

Çalışmanın önemli özelliklerinden biri, tekrarlanan düzenleme işlemlerinin belirli refactoring kalıplarına (refactoring patterns) dönüştürülmesidir. Özellikle Dependency Inversion Principle (DIP) temelinde oluşturulan bu kalıplar, benzer mimari bağımlılık sorunlarının sistematik biçimde ele alınmasını amaçlamaktadır.

Bu açıdan refactoring, makalede yalnızca kodun okunabilirliğini artıran bir yöntem olarak değil, mimari teknik borcun azaltılması için kullanılan bir iyileştirme yaklaşımı olarak değerlendirilmektedir. Araştırmanın sonraki bölümlerinde, bileşenlerin nasıl önceliklendirildiği ve söz konusu refactoring kalıplarının nasıl uygulandığı ayrıntılı olarak incelenecektir.

## 4. Makalenin Araştırma Yöntemi

Yanakiev, Lazar ve Capiluppi (2025) tarafından gerçekleştirilen araştırma, Hollanda merkezli ASML şirketinin mevcut C++ yazılım sisteminde biriken mimari teknik borcun azaltılmasına yönelik endüstriyel bir deneyim raporudur. Çalışma, ASML'nin görüntüyle ilgili işlemlerden sorumlu bir fonksiyonel kümesinde yer alan *reticle align* yazılım deposuna odaklanmaktadır. Sistem, yirmi yılı aşan geliştirme süreci boyunca değişikliklere uğramış ve çeşitli mimari bağımlılık sorunları biriktirmiştir.

Araştırmacılar, mimari teknik borcun azaltılması amacıyla veriye dayalı bir önceliklendirme yaklaşımı benimsemiştir. Makalenin yöntem bölümü; mevcut yazılım metriklerinin incelenmesi, etki analizi, önceliklendirme, literatür incelemesi ve refactoring işlemlerinin uygulanması olmak üzere beş temel aşamadan oluşmaktadır.

### 4.1. Kullanılan Yazılım Metrikleri

Araştırmanın ilk aşamasında ASML'nin şirket içi kalite izleme sisteminden elde edilen ölçümler incelenmiştir. Şirket politikaları nedeniyle araştırmacıların ek dış statik analiz araçları kullanmalarına izin verilmemiştir. Bu nedenle çalışma, hâlihazırda toplanan yazılım metrikleriyle sınırlandırılmıştır.

Makaledeki ölçümler üç temel grupta ele alınmaktadır. Kod seviyesindeki metrikler (Code-Level Metrics); döngüsel karmaşıklık (Cyclomatic Complexity), kod kapsamı (Code Coverage) ve derleyici uyarılarını (Compiler Warnings) içermektedir. Kalite metrikleri (Quality Metrics); kodlama standartlarına uygunluk (Coding Standards), güvenlik (Security) ve kod tekrarı (Code Duplication) gibi özellikleri değerlendirmektedir.

Mimari metrikler (Architectural Metrics) ise bileşenler ve arayüzler arasındaki ilişkiler üzerine yoğunlaşmaktadır. Bu grupta Fan Out, Abstract Interpretation, Dealed Interfaces, Indirectly Dealed Interfaces ve Build Dependencies ölçümleri bulunmaktadır.

Özellikle mimari bağımlılıklara ilişkin ölçümler, sistemin bileşenler arası ilişkilerinin değerlendirilmesi açısından önem taşımaktadır.

### 4.2. Etki Analizi

Metriklerin incelenmesinin ardından araştırmacılar, olası iyileştirmelerin yazılım sistemine sağlayacağı katkıyı belirlemek amacıyla etki analizi (Impact Analysis) gerçekleştirmiştir.

Bu aşamada yalnızca metriklerin mevcut değerleri değil, sorunların giderilmesi için gerekli kaynaklar, beklenen bakım kolaylığı ve araştırmanın temel hedefiyle ilişkileri de dikkate alınmıştır.

Makalenin 4.2 bölümünde özellikle Fan Out, Code Duplication, Code Coverage ve Cyclomatic Complexity metrikleri üzerinde durulmaktadır.

Örneğin Fan Out probleminin azaltılması, bileşenler arasındaki bağımlılıkların iyileştirilmesine katkı sağlayabilecek önemli bir faaliyet olarak değerlendirilmiştir. Bununla birlikte, bu tür bir müdahalenin birden fazla geliştirme ekibinin koordinasyonunu ve uzun bir çalışma süresini gerektirebilmesi, araştırmanın mevcut sınırları içerisinde uygulanabilirliğini azaltmıştır.

Benzer şekilde kod kapsamının artırılması yazılımın doğrulanması açısından yararlı görülmekle birlikte, mimari kurallara aykırı bağımlılıkların azaltılması hedefine doğrudan hizmet etmediği için daha düşük öncelikte değerlendirilmiştir.

### 4.3. Veriye Dayalı Önceliklendirme

Araştırmacılar, ölçüm sonuçlarını ve ASML yazılım mimarının değerlendirmelerini birlikte kullanarak bakım faaliyetleri için beş seviyeli bir önceliklendirme oluşturmuştur.

Makalenin Tablo 1'inde belirtilen öncelik sıralaması şöyledir:

| İyileştirme Alanı | Öncelik |
|---|---|
| Mimari kurallara aykırı bağımlılıkların azaltılması | En yüksek |
| Kod tekrarının azaltılması | Yüksek |
| Fan Out değerinin azaltılması | Orta |
| Kod kapsamının artırılması | Düşük |
| Döngüsel karmaşıklığın azaltılması | En düşük |

Mimari kurallara aykırı bağımlılıkların azaltılması, araştırmanın temel hedefiyle doğrudan ilişkili olduğu için en yüksek önceliğe yerleştirilmiştir.

Bununla birlikte, bu sıralama yazılım kalitesi açısından bütün projelerde geçerli olan genel bir değerlendirme değildir. Araştırmacıların belirlediği öncelikler, ASML'nin mimari sorunları, bakım ihtiyaçları ve çalışmanın uygulanabilirlik sınırları çerçevesinde oluşturulmuştur.

### 4.4. Refactoring Yapılacak Bileşenlerin Seçilmesi

Etki analizi ve önceliklendirme sonucunda araştırmacılar, bakım çalışmalarının etkili olabileceği üç yazılım bileşeni belirlemiştir. Makalede bu bileşenler şirketin gizlilik gereklilikleri nedeniyle A, B ve C olarak adlandırılmaktadır.

A bileşeni, mimari kurallara aykırı iki çıkış bağımlılığına sahiptir. Bu bileşende yapılacak refactoring işlemlerinin B ve C bileşenlerindeki bağımlılık sorunlarını da olumlu yönde etkileyebileceği değerlendirilmiştir. Bu nedenle A bileşeni öncelikli müdahale alanı olarak belirlenmiştir.

B bileşeni, araştırma kapsamında ele alınan mimari bağımlılıklar açısından ikinci sırada değerlendirilmiştir. C bileşeni ise genel kod kalitesi bakımından daha iyi durumda olmasına rağmen diğer bileşenlerle ilişkili bağımlılıkların yeniden düzenlenmesi sürecinde çalışmanın kapsamına alınmıştır.

Bu seçim, araştırmacıların yalnızca en fazla soruna sahip bileşenleri belirlemek yerine, yapılan müdahalelerin sistemin genel mimarisine sağlayabileceği katkıyı da dikkate aldıklarını göstermektedir.

### 4.5. Araştırma Yönteminin RQ1 ile İlişkisi

Makalenin ilk araştırma sorusu (RQ1), veriye dayalı bir yaklaşımın endüstriyel yazılım sistemlerinde mimari teknik borcun azaltılmasına yönelik bakım faaliyetlerinin önceliklendirilmesine nasıl katkı sağladığını incelemektedir.

Araştırmacıların kullandığı yöntem bu soruyla doğrudan ilişkilidir. Öncelikle mevcut metrikler aracılığıyla sorunlu alanlar belirlenmekte, ardından bu alanlardaki iyileştirmelerin beklenen etkileri değerlendirilmektedir. Son aşamada ise mevcut kaynaklar ve mimari hedefler dikkate alınarak müdahale edilecek bileşenler seçilmektedir.

Bu yaklaşım, büyük ölçekli bir yazılım sistemindeki tüm teknik borcun aynı anda giderilmeye çalışılması yerine, bakım faaliyetlerinin ölçümlere ve uzman değerlendirmelerine dayalı şekilde planlanmasına olanak sağlamaktadır.

Araştırmanın yöntemsel açıdan dikkat çekici yönü, sayısal metriklerin tek başına karar vermek için kullanılmaması, endüstriyel koşullar ve yazılım mimarlarının görüşleriyle birlikte değerlendirilmesidir. Bununla birlikte, araştırmacıların yalnızca mevcut şirket içi ölçümlere erişebilmesi, yöntemin veri kapsamı bakımından bir sınırlılık oluşturmaktadır.
## 5. SOLID Prensiplerinin Uygulanması

### 5.1. Dependency Inversion Principle (DIP)

### 5.2. Refactoring Yaklaşımları

*Makaledeki somut refactoring uygulamaları ve bunların OOP prensipleriyle ilişkisi değerlendirilecektir.*

## 6. Bulgular ve Sonuçlar

*Makalenin elde ettiği sonuçlar, kullanılan ölçümler ve araştırma sorularına verilen yanıtlar incelenecektir.*

## 7. Literatür İncelemesi

*Makalenin kaynakçasında yer alan en az üç temel akademik çalışma incelenecek ve bu çalışmaların araştırma konusuyla ilişkisi açıklanacaktır.*

## 8. Kişisel Değerlendirme ve Geliştirme Önerileri

*Makalenin güçlü yönleri, sınırlılıkları ve geliştirilebilecek noktaları gerekçeleriyle değerlendirilecektir.*

## 9. Genel Sonuç

*İncelemeden elde edilen temel çıkarımlar ve çalışmanın nesneye dayalı programlama açısından önemi özetlenecektir.*

## Kaynakça

*İncelenen makale ve araştırma sürecinde yararlanılan akademik kaynaklar burada listelenecektir.*