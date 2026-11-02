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

Yanakiev, Lazar ve Capiluppi (2025) tarafından gerçekleştirilen araştırmanın uygulama aşamasında, ASML'nin mevcut C++ yazılım sistemindeki mimari bağımlılık sorunlarını azaltmak amacıyla SOLID tasarım prensiplerinden yararlanılmıştır. Çalışmanın temel odağını özellikle Dependency Inversion Principle (DIP) oluşturmaktadır.

Araştırmacılar, soyut tasarım prensiplerinin büyük ölçekli bir yazılım sisteminde doğrudan uygulanmasının yeterince açık olmayabileceğinden hareketle, tekrarlanabilir refactoring kalıpları geliştirmiştir. Bu yaklaşım, makalenin ikinci araştırma sorusu olan RQ2 ile doğrudan ilişkilidir.

### 5.1. Dependency Inversion Principle (DIP)

Dependency Inversion Principle, yüksek seviyeli yazılım modüllerinin düşük seviyeli modüllerin somut uygulamalarına doğrudan bağımlı olmaması gerektiğini ifade etmektedir. Bunun yerine, modüller arasındaki ilişkilerin uygun soyutlamalar üzerinden düzenlenmesi amaçlanmaktadır.

Bu prensip, nesneye dayalı programlamadaki soyutlama ve kapsülleme kavramlarıyla yakından ilişkilidir. Modüllerin somut uygulama ayrıntılarından ayrılması, yazılımın bakımını ve değiştirilebilirliğini destekleyebilmektedir.

İncelenen makalede DIP, ASML'nin katmanlı yazılım mimarisinde ortaya çıkan uygunsuz bağımlılıkların giderilmesinde temel tasarım yaklaşımı olarak kullanılmıştır. Araştırmacılar, özellikle alt seviyedeki bileşenlerin üst seviyedeki bileşenlere mimari kuralları ihlal edecek biçimde bağımlı olduğu durumlara odaklanmıştır.

Çalışmada DIP prensibinin uygulanması yalnızca yeni arayüzler oluşturulmasıyla sınırlandırılmamıştır. Mevcut sembollerin doğru mimari katmanlara taşınması, kapsüllenmesi ve gereksiz derleme bağımlılıklarının kaldırılması gibi işlemler de uygulama kapsamına alınmıştır.

Bu yönüyle araştırma, DIP prensibinin yalnızca sınıf seviyesinde değil, bileşenler arasındaki mimari ilişkilerin düzenlenmesinde de kullanılabileceğini göstermektedir.

### 5.2. Refactoring Yaklaşımları

Araştırmacılar, mimari bağımlılık ihlallerini gidermek amacıyla tekrarlanabilir refactoring kalıpları geliştirmiştir. Makalenin beşinci bölümünde bu kalıplar, mevcut mimari durumu ifade eden AS-IS ve hedeflenen mimari durumu ifade eden TO-BE gösterimleriyle açıklanmaktadır.

Çalışmada toplam yedi refactoring kalıbı tanımlanmıştır. Bu kalıplar, makineye özgü bileşenler (Machine-Dependent) ve farklı makine türleri tarafından ortak kullanılabilen bileşenler (Machine-Independent) olmak üzere iki grupta incelenmektedir.

#### 5.2.1. Machine-Dependent Refactoring Patterns

Makineye özgü bileşenler için üç refactoring kalıbı geliştirilmiştir.

**R1M — Exported Symbols:** Alt seviyedeki bir bileşenin üst seviyedeki bir bileşenden dışa aktarılan sembolleri mimari kurallara aykırı biçimde kullanması durumunu ele almaktadır. Çözüm olarak ilgili sembollerin uygun alt seviye bileşene taşınması ve kapsüllenmesi önerilmektedir.

**R2M — Exported Symbols:** Alt seviyedeki bir bileşenin, üst seviyede dışa aktarılan sembol listesinin yalnızca belirli bir bölümünü kullanması durumuna odaklanmaktadır. Gerekli sembollerin uygun bileşene taşınmasıyla bağımlılıkların azaltılması amaçlanmaktadır.

**R3M — Derleme Bağımlılığının Düzeltilmesi:** Kaynak kodda gerçek bir sembol kullanımı bulunmamasına rağmen derleme yapılandırmasında gereksiz bağımlılık tanımlanması nedeniyle oluşan mimari ihlalleri ele almaktadır. Bu kalıpta derleme bağımlılıklarının düzeltilmesiyle yanlış pozitif bağımlılık ihlallerinin giderilmesi hedeflenmektedir.

Bu üç kalıp, mimari bağımlılık problemlerinin farklı nedenlerden kaynaklanabileceğini ve her problemin aynı kod düzenleme işlemiyle çözülemeyeceğini göstermektedir.

#### 5.2.2. Machine-Independent Refactoring Patterns

Makineden bağımsız ortak bileşenlerle ilişkili sorunların giderilmesi için dört refactoring kalıbı geliştirilmiştir.

**R1C — Exported Symbols From Common Component:** Bir sembol listesinin mimari hiyerarşide uygun seviyedeki başka bir ortak bileşene taşınmasını öngörmektedir. Bu işlem sırasında ortak işlevlerin yeniden kullanılabilirliğinin korunması amaçlanmaktadır.

**R2C — Ortak Sembol Listesinin Taşınması:** Ortak bileşendeki sembol listesinin gerekli alt kümesinin uygun başka bir ortak bileşene taşınmasına odaklanmaktadır. Kodun yerleştirileceği bileşenin belirlenmesi, yazılımın mimari yapısına ilişkin alan bilgisi gerektirmektedir.

**R3C — Makineye Özgü Sembollerin Ayrılması:** Ortak bir bileşende bulunan ancak yalnızca belirli bir makineye özgü bileşenin kullandığı sembollerin ilgili makineye özgü bileşene taşınmasını ve kapsüllenmesini amaçlamaktadır.

**R4C — Sembol Alt Kümesinin Kapsüllenmesi:** Ortak bileşendeki dışa aktarılmış sembollerin yalnızca belirli bir makineye özgü bileşen tarafından kullanılan alt kümesinin bu bileşene taşınmasını ele almaktadır. Böylece gereksiz dışa açık sembollerin ve uygunsuz bağımlılıkların azaltılması hedeflenmektedir.

Ortak bileşenlere yönelik refactoring işlemleri, farklı makine türlerinin aynı bileşenleri kullanabilmesi nedeniyle daha kapsamlı değerlendirme gerektirmektedir. Araştırmacılar, bu işlemlerde alan bilgisinin ve yazılım mimarları arasındaki koordinasyonun önemli olduğunu vurgulamaktadır.

### 5.3. Refactoring Kalıplarının OOP ile İlişkisi

Makaledeki refactoring kalıpları, nesneye dayalı programlamanın soyutlama, kapsülleme ve modülerlik kavramlarıyla ilişkilidir.

Sembollerin mantıksal olarak uygun bileşenlere taşınması, yazılım bileşenlerinin sorumluluklarının daha belirgin hâle getirilmesine yardımcı olmaktadır. Gereksiz dış bağımlılıkların kaldırılması ve sembollerin kapsüllenmesi ise bileşenler arasındaki sıkı bağlılığın azaltılmasını desteklemektedir.

Bununla birlikte, makalede tanımlanan kalıpların tamamı doğrudan sınıf veya nesne seviyesinde uygulanmamaktadır. Bazı kalıplar bileşenler arasındaki mimari ilişkileri, bazıları ise derleme bağımlılıklarını düzenlemektedir.

Dolayısıyla çalışma, OOP tasarım prensiplerinin daha geniş kapsamlı yazılım mimarisi iyileştirmelerine nasıl temel oluşturabileceğini göstermektedir.

### 5.4. RQ2 Açısından Değerlendirme

Makalenin ikinci araştırma sorusu, SOLID tasarım prensiplerinin mevcut yazılım sisteminde somut refactoring kalıplarına nasıl dönüştürülebileceğini incelemektedir.

Araştırmacılar, DIP prensibinden hareketle farklı mimari bağımlılık problemleri için yedi tekrarlanabilir kalıp tanımlamıştır. Bu kalıplar, sorunların türüne göre uygulanabilecek düzenleme işlemlerini sistematik biçimde açıklamaktadır.

Bu bağlamda araştırmanın önemli katkısı, DIP gibi soyut bir tasarım prensibinin mevcut C++ yazılım sistemindeki gerçek mimari sorunlara uyarlanabilecek somut işlemlere dönüştürülmesidir.

Bununla birlikte, kalıpların uygulanabilirliği yazılımın mevcut mimarisine, bileşenlerin sorumluluklarına ve kullanılan geliştirme ortamına bağlıdır. Bu nedenle söz konusu kalıpların farklı projelere doğrudan ve değişiklik yapılmadan aktarılabileceği varsayılmamalıdır.

Araştırmanın sonraki bölümünde, bu kalıpların uygulanması sonucunda elde edilen sayısal bulgular ve mimari bağımlılıklardaki değişimler değerlendirilecektir.

## 6. Bulgular ve Sonuçlar

Yanakiev, Lazar ve Capiluppi (2025) tarafından gerçekleştirilen araştırmada, ASML'nin uzun yıllardır geliştirilen C/C++ yazılım sisteminde birikmiş mimari teknik borcun azaltılması amacıyla uygulanan refactoring işlemlerinin sonuçları değerlendirilmiştir. Çalışma kapsamında üç bileşen (A, B ve C) arasındaki uygunsuz bağımlılıklar incelenmiş ve Dependency Inversion Principle (DIP) temelinde geliştirilen refactoring kalıplarından yararlanılmıştır.

Araştırmanın bulguları, bileşenler arasındaki mimari bağımlılıkların azaltılması, dışa aktarılan sembollerin uygun şekilde yeniden düzenlenmesi ve kullanılan refactoring kalıplarının dağılımı üzerinden değerlendirilmektedir.

### 6.1. A ve B Bileşenleri Arasındaki Refactoring Sonuçları

Makalenin altıncı bölümünde, A ve B bileşenleri arasındaki uygunsuz bağımlılıkların giderilmesine yönelik işlemler açıklanmaktadır. Araştırmacılar, altı arayüz üzerinde gerçekleştirilen refactoring çalışmaları sonucunda bir giden ve bir gelen uygunsuz bağımlılığın kaldırıldığını bildirmiştir.

Makalenin Table 4 tablosunda A–B kapsamındaki bağımlılık işlemlerinin refactoring kalıplarına göre dağılımı verilmiştir.

| Refactoring kalıbı | Bağımlılık sayısı | Oran |
|---|---:|---:|
| R1M | 194 | %66,0 |
| R2M | 99 | %33,7 |
| R3M | 1 | %0,3 |
| **Toplam** | **294** | **%100** |

Bu verilere göre R1M, A–B bileşenleri arasındaki düzenlemelerde en sık kullanılan refactoring kalıbıdır. R1M kalıbı, mimari kurallara aykırı biçimde dışa aktarılan sembollerin mantıksal olarak uygun alt seviye bileşene taşınmasını esas almaktadır.

R2M kalıbı 99 bağımlılık işlemiyle ikinci sırada yer alırken R3M yalnızca bir işlemde kullanılmıştır.

Araştırmacılar, R2M kapsamında ele alınan bağımlılıkların %85'inden fazlasının tek bir arayüzde bulunduğunu belirterek bu dağılımın belirli bir arayüzden önemli ölçüde etkilendiğini ifade etmiştir.

Bu nedenle kalıpların kullanım sıklığı, bütün yazılım projelerinde geçerli bir etkinlik sıralaması olarak yorumlanmamalıdır. Ayrıca tabloda yer alan 294 işlem, 294 ayrı bileşenler arası mimari bağımlılığın tamamen kaldırıldığı anlamına gelmemektedir.

### 6.2. A ve C Bileşenleri Arasındaki Refactoring Sonuçları

Çalışmada A ve C bileşenleri arasındaki bağımlılıklar da incelenmiştir. C bileşeni, farklı makine türlerinin ortak olarak kullanabildiği işlevleri içeren bir bileşendir. Dolayısıyla bu bileşenle ilişkili değişiklikler, birden fazla yazılım bileşenini ve geliştirme ekibini etkileyebilmektedir.

Makalenin Table 4 tablosunda A–C kapsamındaki işlemler aşağıdaki şekilde sınıflandırılmıştır.

| Refactoring kalıbı | Bağımlılık sayısı | Oran |
|---|---:|---:|
| R1C | 0 | %0 |
| R2C | 35 | %79,5 |
| R3C | 9 | %20,5 |
| R4C | 0 | %0 |
| **Toplam** | **44** | **%100** |

Bu dağılımda R2C kalıbı yaklaşık %80 ile en büyük paya sahiptir. R2C, ortak bileşenlerde bulunan sembollerin uygun başka bir ortak bileşene taşınmasıyla ilişkilidir.

Bununla birlikte, araştırmacılar ortak bileşenler arasındaki değişikliklerin daha geniş kapsamlı koordinasyon gerektirdiğini açıklamıştır. Çalışmanın zaman ve organizasyonel kapsamı nedeniyle belirlenen bütün bağımlılıkların giderilmesi mümkün olmamıştır.

Makalenin 6.2. bölümünde, çalışma kapsamında makineye özgü bileşene taşınabilen dokuz bağımlılığın düzenlendiği belirtilmektedir. Bu nedenle tabloda sınıflandırılan 44 bağımlılık işleminin tamamı fiilen gerçekleştirilmiş refactoring işlemleri olarak değerlendirilmemelidir.

Bu bulgu, büyük ölçekli yazılım sistemlerinde teknik olarak uygun bir refactoring çözümünün uygulanmasının organizasyonel koşullara da bağlı olduğunu göstermektedir.

### 6.3. Mimari Bağımlılıklar ve Dışa Aktarılan Sembollerdeki Değişim

Makalenin 6.1. bölümünde A–B bileşenleri arasındaki refactoring işlemleri sonucunda bir giden ve bir gelen uygunsuz bağımlılığın kaldırıldığı ve araştırma kapsamında %33'lük bir azalma sağlandığı belirtilmektedir.

Buna karşılık makalenin sonuç bölümünde başlangıçta belirlenen dört uygunsuz bağımlılıktan ikisinin ortadan kaldırıldığı ve genel olarak %50 azalma elde edildiği raporlanmıştır.

Genel sonuç bölümündeki oran şu şekilde hesaplanabilmektedir:

(2 / 4) × 100 = %50

Ancak makalenin 6.1. bölümünde bildirilen %33 oranının hesaplama tabanı aynı açıklıkta verilmemektedir. Bu nedenle söz konusu iki oranın hangi kapsamlar üzerinden hesaplandığı dikkatle değerlendirilmelidir.

Araştırmacılar ayrıca uygunsuz biçimde kullanılan dışa aktarılmış sembollerin sayısında %85'in üzerinde azalma elde edildiğini bildirmiştir.

Burada mimari bağımlılıkların azaltılması ile dışa aktarılmış sembollerin yeniden düzenlenmesi arasında ayrım yapılması gerekmektedir. Bileşenler arasındaki uygunsuz mimari ilişkilerin sayısı ve bu ilişkiler kapsamında kullanılan sembollerin sayısı farklı ölçütlerdir.

Dolayısıyla araştırmada bildirilen %85'in üzerindeki iyileşme, yazılım sistemindeki toplam teknik borcun aynı oranda ortadan kaldırıldığı anlamına gelmemektedir.

### 6.4. Araştırma Sorularının Bulgular Açısından Değerlendirilmesi

#### 6.4.1. RQ1 — Veri Odaklı Önceliklendirme

Makalenin birinci araştırma sorusu, veri odaklı bir yaklaşımın endüstriyel yazılım sistemlerinde mimari teknik borcun önceliklendirilmesine ve azaltılmasına nasıl katkıda bulunabileceğini incelemektedir.

Araştırmacılar, mevcut yazılım metriklerini ve ASML yazılım mimarlarının alan bilgisini birlikte değerlendirerek bakım faaliyetleri için öncelikli bileşenleri belirlemiştir.

Özellikle uygunsuz mimari bağımlılıkların giderilmesi yüksek öncelikli bir hedef olarak seçilmiş; yazılım sisteminin tamamını aynı anda yeniden düzenlemek yerine belirli bileşenlere odaklanılmıştır.

Elde edilen sonuçlar, mevcut veriler ve etki analizi kullanılarak sınırlı kapsamda da olsa mimari teknik borcun azaltılabileceğine ilişkin endüstriyel bir örnek sunmaktadır.

Bununla birlikte araştırma tek bir şirketin belirli yazılım sistemi üzerinde gerçekleştirildiğinden, aynı yaklaşımın farklı sistemlerde aynı düzeyde başarı sağlayacağı doğrudan ileri sürülemez.

#### 6.4.2. RQ2 — SOLID Prensiplerinin Refactoring Kalıplarına Dönüştürülmesi

İkinci araştırma sorusu, SOLID tasarım prensiplerinin somut ve tekrarlanabilir refactoring kalıplarına nasıl dönüştürülebileceğini incelemektedir.

Araştırmacılar, özellikle Dependency Inversion Principle prensibini temel alarak yedi refactoring kalıbı geliştirmiştir.

Bu kalıplar; uygunsuz biçimde dışa aktarılan sembollerin doğru bileşenlere taşınması, kapsüllenmesi, ortak bileşenlerdeki sorumlulukların yeniden düzenlenmesi ve gereksiz derleme bağımlılıklarının düzeltilmesi gibi işlemleri kapsamaktadır.

Table 4'teki dağılımlar, bu kalıpların farklı mimari bağımlılık problemleri için kullanıldığını veya uygulanmak üzere sınıflandırıldığını göstermektedir.

Çalışmanın bu açıdan temel katkısı, soyut bir yazılım tasarım prensibinin büyük ölçekli bir endüstriyel sistemde uygulanabilir bakım işlemlerine dönüştürülmesidir.

### 6.5. Bulguların OOP ve Yazılım Mimarisi Açısından Değerlendirilmesi

Araştırmanın bulguları, nesneye dayalı programlamada önemli olan soyutlama, kapsülleme ve modülerlik kavramlarının yazılım mimarisinin iyileştirilmesinde de rol oynayabileceğini göstermektedir.

Sembollerin uygun bileşenlere taşınması, bileşenlerin sorumluluklarının daha açık biçimde ayrılmasını desteklemektedir. Gereksiz dış bağımlılıkların kaldırılması ise bileşenler arasındaki istenmeyen bağlılığı azaltmaya yöneliktir.

Öte yandan çalışmadaki bütün düzenlemeler sınıf veya nesne düzeyinde gerçekleştirilmemiştir. Bazı işlemler bileşenler arası mimari ilişkileri, bazıları ise derleme yapılandırmalarını hedeflemektedir.

Bu nedenle makalenin sonuçları, SOLID prensiplerinin yalnızca sınıf tasarımıyla sınırlı olmadığını; mevcut yazılımın daha geniş mimari yapısının iyileştirilmesine de rehberlik edebileceğini ortaya koymaktadır.

### 6.6. Bulguların Genel Değerlendirmesi

Araştırmacılar, büyük ölçekli legacy yazılım sistemlerinde bütün teknik borcu tek seferde gidermeye çalışmak yerine, etki analizine dayalı ve aşamalı bir refactoring yaklaşımını benimsemiştir.

Çalışmada bildirilen sonuçlar, belirlenen uygunsuz mimari bağımlılıkların bir kısmının giderildiğini ve dışa aktarılan sembollerin uygun biçimde düzenlenmesi açısından önemli ilerleme kaydedildiğini göstermektedir.

Bununla birlikte ortak bileşenlerdeki bazı bağımlılıkların giderilememiş olması, refactoring faaliyetlerinin yalnızca teknik bilgiye değil; zaman, kapsam, alan bilgisi ve ekipler arası koordinasyona da bağlı olduğunu ortaya koymaktadır.

Bu incelemeye göre makalenin önemli katkısı, veri odaklı önceliklendirme yaklaşımını SOLID prensiplerinden türetilen tekrarlanabilir refactoring kalıplarıyla birleştirmesidir.

Sonuçların farklı yazılım sistemlerine genellenebilirliği, raporlanan oranların açıklığı ve uygulama kapsamındaki sınırlılıklar ise eleştirel değerlendirme bölümünde ayrıca ele alınacaktır.

## 7. Literatür ve Temel Akademik Çalışmalar

Yanakiev, Lazar ve Capiluppi (2025) tarafından gerçekleştirilen araştırma, nesneye dayalı yazılım tasarımı, yazılım yaşlanması, teknik borç yönetimi ve refactoring alanlarında daha önce ortaya konulmuş bilimsel çalışmalardan yararlanmaktadır. İncelenen makalenin literatürdeki konumunu değerlendirmek amacıyla, araştırmacıların doğrudan atıfta bulunduğu dört temel kaynak ele alınmıştır.

Bu kaynaklar Robert C. Martin'in (2003) nesneye dayalı tasarım prensiplerine ilişkin eseri, Lenarduzzi ve arkadaşlarının (2021) teknik borç önceliklendirmesi konulu sistematik literatür taraması, Parnas'ın (1994) yazılım yaşlanması çalışması ve Abid ve arkadaşlarının (2020) refactoring araştırmalarını sınıflandıran literatür incelemesidir.

### 7.1. Martin (2003): Nesneye Dayalı Tasarım Prensipleri

Robert C. Martin'in *Agile Software Development: Principles, Patterns, and Practices* adlı eseri, nesneye dayalı yazılım geliştirmede tasarım prensiplerinin ve tasarım kalıplarının kullanımını ele almaktadır.

Martin (2003), yazılım sistemlerinin değişen gereksinimlere uyum sağlayabilmesi için modüller arasındaki bağımlılıkların ve sorumlulukların uygun biçimde düzenlenmesini vurgulamaktadır. Bu kapsamda Dependency Inversion Principle (DIP), yüksek seviyeli modüllerin düşük seviyeli somut uygulamalara doğrudan bağımlı olmak yerine uygun soyutlamalara dayanmasını öneren temel tasarım prensiplerinden biridir.

Yanakiev ve arkadaşları (2025), makalelerinin giriş bölümünde SOLID prensiplerini açıklarken Martin'in çalışmasına atıfta bulunmaktadır. ASML'nin legacy C++ sistemindeki mimari bağımlılık ihlallerini gidermek amacıyla geliştirilen refactoring kalıpları da özellikle DIP prensibi temelinde oluşturulmuştur.

Bu yönüyle Martin'in eseri, incelenen araştırmanın teorik tasarım temelini oluşturmaktadır. Yanakiev ve arkadaşlarının katkısı ise bu teorik prensibi mevcut bir endüstriyel yazılım mimarisindeki somut sorunlara uyarlamasıdır.

### 7.2. Lenarduzzi ve Arkadaşları (2021): Teknik Borcun Önceliklendirilmesi

Lenarduzzi ve arkadaşları (2021), *A systematic literature review on Technical Debt prioritization: Strategies, processes, factors, and tools* başlıklı çalışmalarında teknik borcun önceliklendirilmesinde kullanılan stratejileri, süreçleri, faktörleri ve araçları sistematik biçimde incelemiştir.

Araştırmacılar, literatür taraması kapsamında 557 benzersiz yayını değerlendirmiş ve seçim süreci sonunda 44 birincil çalışmayı analiz etmiştir. Çalışmada teknik borcun önceliklendirilmesi açısından yazılım kalitesi, bakım maliyeti, geliştirici verimliliği ve maliyet-fayda değerlendirmeleri gibi farklı faktörler ele alınmıştır.

Araştırmanın önemli sonuçlarından biri, teknik borcun önceliklendirilmesi için tüm yazılım projelerine uygulanabilecek, genel kabul görmüş tek bir yaklaşımın bulunmamasıdır. Kullanılacak yöntemin yazılım sisteminin özelliklerine ve organizasyonun hedeflerine göre değişebileceği anlaşılmaktadır.

Yanakiev ve arkadaşları (2025), kendi araştırmalarında teknik borcun önceliklendirilmesi bağlamında Lenarduzzi ve arkadaşlarının çalışmasına atıfta bulunmaktadır. ASML sisteminde mevcut yazılım metrikleri, mimari bağımlılık sorunları ve yazılım mimarlarının değerlendirmeleri birlikte kullanılarak refactoring faaliyetleri önceliklendirilmiştir.

Bu ilişki, incelenen makalenin birinci araştırma sorusu (RQ1) açısından önem taşımaktadır. Lenarduzzi ve arkadaşları teknik borcun önceliklendirilmesini literatür düzeyinde ele alırken Yanakiev ve arkadaşları bu yaklaşımı belirli bir endüstriyel ortamda uygulamıştır.

### 7.3. Parnas (1994): Yazılım Yaşlanması

David Lorge Parnas'ın (1994) *Software Aging* başlıklı çalışması, yazılım sistemlerinin zaman içerisinde neden bakım ve sürdürülebilirlik sorunları yaşayabildiğini açıklayan temel araştırmalardan biridir.

Parnas'a göre yazılım yaşlanması yalnızca yazılımın eski bir tarihte geliştirilmiş olmasından kaynaklanmamaktadır. Değişen gereksinimlere uyum sağlanamaması ve yazılım üzerinde gerçekleştirilen değişikliklerin mevcut yapıyı olumsuz etkilemesi de yaşlanma sürecini hızlandırabilmektedir.

Bu yaklaşım, yazılım sistemlerinin uzun vadeli sürdürülebilirliği açısından bakım faaliyetlerinin ve mimari bütünlüğün korunmasının önemini ortaya koymaktadır.

Yanakiev ve arkadaşları (2025), makalelerinin ilgili çalışmalar bölümünde yazılım yaşlanması kavramını tartışırken Parnas'ın araştırmasına atıfta bulunmaktadır.

ASML'nin incelenen C++ sistemi yaklaşık yirmi yıllık geliştirme geçmişine sahiptir. Bu süreçte birikmiş mimari bağımlılık ihlalleri ve teknik borç, bakım faaliyetlerini zorlaştıran önemli sorunlar arasında yer almaktadır.

Dolayısıyla Parnas'ın çalışması, incelenen makalenin ele aldığı legacy sistem probleminin kavramsal arka planını oluşturmaktadır. Yanakiev ve arkadaşlarının araştırması ise bu tür mimari sorunların belirli bir bölümünün refactoring yoluyla nasıl azaltılabileceğine ilişkin uygulamalı bir örnek sunmaktadır.

### 7.4. Abid ve Arkadaşları (2020): Refactoring Araştırmalarının Sınıflandırılması

Abid ve arkadaşları (2020), *30 Years of Software Refactoring Research: A Systematic Literature Review* başlıklı çalışmalarında yazılım refactoring alanındaki araştırmaları sistematik biçimde incelemiş ve farklı araştırma yaklaşımlarını sınıflandırmaya yönelik bir taksonomi geliştirmiştir.

Çalışmada refactoring faaliyetleri; yaşam döngüsü, otomasyon düzeyi, incelenen yazılım öğeleri, programlama paradigmaları ve değerlendirme yöntemleri gibi farklı boyutlarda ele alınmaktadır.

Yanakiev ve arkadaşları (2025), makalelerinin 2.1. bölümünde Abid ve arkadaşlarının taksonomisinden yararlanarak kendi araştırmalarını refactoring literatürü içerisinde konumlandırmaktadır.

İncelenen çalışma; refactoring fırsatlarının tespit edilmesi ve önceliklendirilmesi, otomatik tespit araçları ve yarı otomatik önceliklendirme desteğiyle manuel refactoring gerçekleştirilmesi, mimari tasarım prensiplerinin kullanılması ve gerçek bir endüstriyel C++ sisteminde değerlendirme yapılması gibi özelliklere sahiptir.

Bu bağlamda Abid ve arkadaşlarının araştırması, Yanakiev ve arkadaşlarının çalışmasının yalnızca bir kod düzenleme uygulaması olmadığını, refactoring literatüründeki belirli araştırma kategorileriyle ilişkili olduğunu göstermektedir.

Bu kaynak özellikle ikinci araştırma sorusunun (RQ2) bilimsel bağlamda değerlendirilmesine katkıda bulunmaktadır.

### 7.5. Literatürün Karşılaştırmalı Değerlendirilmesi

İncelenen dört akademik kaynak, Yanakiev ve arkadaşlarının (2025) araştırmasını farklı açılardan desteklemektedir.

| Akademik çalışma | Temel odak | İncelenen makaleyle ilişkisi |
|---|---|---|
| Martin (2003) | SOLID ve OOP tasarım prensipleri | DIP'nin teorik temeli |
| Lenarduzzi ve ark. (2021) | Teknik borcun önceliklendirilmesi | RQ1'in bilimsel altyapısı |
| Parnas (1994) | Yazılım yaşlanması | Legacy sistemlerde bakım probleminin açıklanması |
| Abid ve ark. (2020) | Refactoring araştırmalarının sınıflandırılması | Refactoring yaklaşımının literatürde konumlandırılması |

Martin'in çalışması yazılımın nasıl tasarlanması gerektiğine, Parnas'ın çalışması yazılım sistemlerinin zaman içerisinde neden bakım sorunları yaşayabildiğine, Lenarduzzi ve arkadaşlarının araştırması hangi teknik borç sorunlarının öncelikle ele alınması gerektiğine ve Abid ve arkadaşlarının incelemesi refactoring faaliyetlerinin bilimsel literatürde nasıl sınıflandırıldığına odaklanmaktadır.

Bu çalışmalar birlikte değerlendirildiğinde Yanakiev ve arkadaşlarının araştırmasının tasarım prensipleri, teknik borç yönetimi ve yazılım bakımına ilişkin önceki bilimsel yaklaşımları endüstriyel bir problem etrafında birleştirdiği görülmektedir.

İncelenen makalenin temel katkısı, SOLID prensiplerini ilk kez ortaya koymak veya teknik borç kavramını yeniden tanımlamak değildir. Araştırmacılar, mevcut bilimsel bilgi birikiminden yararlanarak ASML'nin legacy C++ sistemindeki belirli mimari bağımlılık sorunlarına yönelik tekrarlanabilir refactoring kalıpları geliştirmiş ve bu kalıpların uygulanmasını değerlendirmiştir.

Bununla birlikte, seçilen kaynakların yayın türleri ve araştırma yaklaşımları farklıdır. Martin'in eseri tasarım prensiplerini açıklayan bir kitap, Parnas'ın çalışması bir konferans bildirisi, Lenarduzzi ve arkadaşlarının araştırması hakemli bir dergide yayımlanmış sistematik literatür taraması, Abid ve arkadaşlarının incelenen sürümü ise arXiv üzerinde erişilebilen sistematik literatür incelemesidir.

Bu nedenle söz konusu kaynaklar değerlendirilirken her birinin sunduğu kanıt türü ve araştırma kapsamı dikkate alınmalıdır.

Sonuç olarak literatür incelemesi, Yanakiev ve arkadaşlarının (2025) çalışmasının hem nesneye dayalı programlama prensipleriyle hem de yazılım mühendisliğindeki bakım, teknik borç ve refactoring araştırmalarıyla güçlü bir kavramsal ilişki içerisinde olduğunu göstermektedir.

## 8. Eleştirel Değerlendirme ve Geliştirme Önerileri

Yanakiev, Lazar ve Capiluppi (2025) tarafından gerçekleştirilen araştırma, nesneye dayalı tasarım prensiplerinin büyük ölçekli legacy yazılım sistemlerinde uygulanmasına ilişkin önemli bir endüstriyel deneyim sunmaktadır. Çalışmanın temel katkısı, Dependency Inversion Principle (DIP) prensibinin mevcut bir C/C++ sistemindeki mimari bağımlılık sorunlarına yönelik somut refactoring kalıplarına dönüştürülmesidir.

Bununla birlikte, araştırmanın güçlü yönleri kadar yöntemsel sınırlılıklarının da değerlendirilmesi gerekmektedir. Bu bölümde makalenin bilimsel ve teknik katkıları, geçerliliğini etkileyebilecek unsurlar ve gelecekteki çalışmalar için geliştirilebilecek öneriler ele alınmaktadır.

### 8.1. Araştırmanın Güçlü Yönleri

Çalışmanın önemli güçlü yönlerinden biri, önerilen yaklaşımın gerçek bir endüstriyel sistem üzerinde uygulanmış olmasıdır. Araştırmacılar, ASML'nin uzun yıllardır geliştirilen legacy C/C++ kod tabanındaki mimari bağımlılık sorunlarını incelemiş ve belirli refactoring işlemlerini gerçekleştirmiştir. Bu durum, SOLID prensiplerinin yalnızca teorik tasarım kuralları olarak değil, gerçek yazılım bakım problemlerine yönelik uygulama rehberleri olarak da kullanılabileceğini göstermektedir.

Araştırmanın ikinci güçlü yönü, refactoring öncesinde veri odaklı önceliklendirme yapılmasıdır. Yazılım metrikleri, etki analizi ve ASML mimarlarının alan bilgisi bir arada değerlendirilerek bakım açısından öncelikli sorunlar belirlenmiştir. Büyük ve karmaşık sistemlerde bütün teknik borcun tek seferde giderilmesinin güç olduğu düşünüldüğünde, bu yaklaşımın kaynakların daha etkili kullanılmasına katkı sağlayabileceği değerlendirilmektedir.

Üçüncü önemli katkı, DIP prensibinden hareketle yedi refactoring kalıbının geliştirilmesidir. Araştırmacılar, mimari bağımlılık sorunlarını sınıflandırmış ve mevcut durum ile hedeflenen yapı arasındaki dönüşümü açıklayan uygulama örnekleri sunmuştur. Bu kalıplar, benzer bağımlılık sorunlarının daha tutarlı biçimde ele alınmasını desteklemektedir.

Çalışmada artımlı refactoring yaklaşımının benimsenmesi de olumlu bir özelliktir. Mevcut sistemin tamamen yeniden yazılması yerine belirli mimari sorunlara odaklanılması, endüstriyel yazılım geliştirme süreçlerinin operasyonel kısıtlarıyla uyumlu bir yöntem sunmaktadır.

### 8.2. Yöntemsel Sınırlılıklar ve Geçerlilik Tehditleri

Makalenin önemli sınırlılıklarından biri, araştırmanın tek bir endüstriyel bağlamda yürütülmüş olmasıdır. Yanakiev ve arkadaşları (2025), çalışmanın *Threats to Validity* bölümünde ASML'nin kendine özgü teknolojilerinin, mimari yapısının ve geliştirme uygulamalarının sonuçların genellenebilirliğini sınırlandırabileceğini belirtmektedir.

Bu durum, araştırmanın dış geçerliliği açısından önem taşımaktadır. ASML sisteminde başarılı biçimde uygulanan refactoring kalıplarının farklı şirketlerde veya farklı yazılım mimarilerinde aynı sonuçları sağlayacağı doğrudan varsayılamaz. Kalıpların başka sistemlere uyarlanabilir olduğu yönündeki değerlendirmelerin daha güçlü biçimde desteklenmesi için farklı endüstriyel ortamlarda ek uygulamalara ihtiyaç bulunmaktadır.

İç geçerlilik açısından araştırmacılar, refactoring kalıplarının oluşturulmasında mevcut bağımlılıkların analizinden ve ASML yazılım mimarlarının görüşlerinden yararlandıklarını açıklamaktadır. Alan uzmanlarının araştırmaya katkısı, mimari problemlerin doğru yorumlanması açısından önemli bir avantajdır. Bununla birlikte, önceliklendirme kararlarının ve uygulama sonuçlarının bağımsız ölçümlerle daha ayrıntılı doğrulanması, yöntemin güvenilirliğini güçlendirebilir.

Araştırma verilerinin gizli olması da bağımsız yeniden üretilebilirlik açısından bir sınırlılıktır. Endüstriyel kaynak kodun paylaşılmaması anlaşılabilir bir durum olmakla birlikte, farklı araştırmacıların aynı işlemleri aynı veri üzerinde tekrar etmesini güçleştirmektedir. Bu durum tek başına bulguların geçersiz olduğu anlamına gelmemekte; ancak araştırmanın bağımsız olarak doğrulanabilmesini sınırlandırmaktadır.

### 8.3. Bulguların Eleştirel Değerlendirilmesi

Araştırmacılar, refactoring faaliyetleri sonucunda incelenen dört uygunsuz mimari bağımlılıktan ikisinin giderildiğini ve böylece genel kapsamda %50 azalma elde edildiğini bildirmektedir. Ayrıca uygunsuz kullanılan dışa aktarılmış sembollerin sayısında %85'in üzerinde azalma sağlandığı belirtilmektedir.

Bu sonuçlar, gerçekleştirilen refactoring işlemlerinin mimari bağımlılıkların azaltılması açısından ölçülebilir katkılar sunduğunu göstermektedir. Bununla birlikte, sonuçların yorumlanmasında kullanılan ölçütlerin kapsamı dikkate alınmalıdır.

Örneğin makalenin 6.1. bölümünde uygunsuz bağımlılıkların %33 oranında azaltıldığı belirtilirken sonuç bölümünde %50 oranı raporlanmaktadır. Bu oranların farklı kapsamlara karşılık gelmesi mümkündür. Ancak hesaplamalarda kullanılan başlangıç değerlerinin ve kapsamların daha açık biçimde sunulması, sonuçların anlaşılmasını ve karşılaştırılmasını kolaylaştıracaktır. Dolayısıyla bu durum kesin bir hesaplama hatası olarak değil, sonuçların raporlanmasında geliştirilebilecek bir açıklık sorunu olarak değerlendirilmelidir.

Çalışmanın bir diğer sınırlılığı, planlanan refactoring faaliyetlerinin tamamının gerçekleştirilememiş olmasıdır. Özellikle ortak bileşenlerle ilişkili bazı düzenlemeler, birden fazla ekibin koordinasyonunu gerektirdiğinden araştırma kapsamı dışında kalmıştır. Bu nedenle bildirilen iyileşmelerin bütün mimari teknik borcun ortadan kaldırıldığı şeklinde yorumlanmaması gerekir.

Ayrıca makale, mimari bağımlılıkların azaltılmasına ilişkin önemli nicel sonuçlar sunmasına rağmen bu değişikliklerin yazılımın uzun vadeli bakım maliyeti, hata düzeltme süresi veya geliştirici verimliliği üzerindeki etkilerini aynı ayrıntıda ölçmemektedir. Bu tür göstergeler, gerçekleştirilen mimari iyileştirmelerin operasyonel faydalarını değerlendirmek açısından tamamlayıcı nitelikte olacaktır.

### 8.4. Geliştirme Önerileri

Araştırmanın dış geçerliliğini güçlendirmek amacıyla geliştirilen refactoring kalıpları farklı şirketlerde ve yazılım mimarilerinde değerlendirilebilir. Özellikle katmanlı mimariye sahip farklı C++ sistemlerinde ve benzer bağımlılık problemleri bulunan diğer nesneye dayalı yazılım projelerinde yapılacak karşılaştırmalı çalışmalar, kalıpların uygulanabilirlik sınırlarının belirlenmesini sağlayabilir.

Bağımsız yeniden üretilebilirliği artırmak amacıyla araştırmacıların karşılaştığı mimari bağımlılık sorunlarını temsil eden anonimleştirilmiş örnek projeler hazırlanabilir. Bu projelerde refactoring öncesi ve sonrası bağımlılık yapıları, uygulanan dönüşümler ve doğrulama adımları gösterilebilir. Böylece kurumsal gizlilik korunurken araştırmanın yöntemsel şeffaflığı artırılabilir.

Sonuçların raporlanması açısından her refactoring işlemi için başlangıçtaki bağımlılık sayısını, işlem sonrasındaki bağımlılık sayısını ve elde edilen iyileşme oranını gösteren standart tablolar oluşturulması önerilmektedir. Ayrıca mimari bağımlılık sayısı ile sembol düzeyindeki bağımlılık sayısının ayrı ölçütler olarak sunulması, farklı başarı göstergelerinin karıştırılmasını önleyebilir.

Gelecekteki araştırmalarda refactoring faaliyetlerinin uzun vadeli bakım performansına etkisi de incelenebilir. Bakım süresi, değişiklik maliyeti, hata düzeltme süresi ve geliştirici iş yükü gibi ölçütlerin refactoring öncesinde ve sonrasında karşılaştırılması, mimari iyileştirmelerin pratik faydalarının daha kapsamlı değerlendirilmesine yardımcı olabilir. Bununla birlikte, böyle bir karşılaştırmada ekip deneyimi ve geliştirme süreçlerindeki değişiklikler gibi diğer faktörlerin etkileri de dikkate alınmalıdır.

Son olarak, araştırma kapsamında tamamlanamayan mimari düzenlemeler için uzun vadeli bir takip süreci oluşturulabilir. Böylece artımlı refactoring yaklaşımının yalnızca ilk aşamadaki sonuçları değil, sonraki bakım dönemlerindeki sürdürülebilirliği de incelenebilir.

### 8.5. Genel Akademik Değerlendirme

Yanakiev ve arkadaşlarının (2025) araştırması, SOLID tasarım prensiplerinin legacy yazılım sistemlerindeki mimari problemlere uygulanmasına yönelik değerli bir endüstriyel örnek sunmaktadır. Çalışmanın en önemli katkısı, DIP prensibini uygulanabilir refactoring kalıplarına dönüştürmesi ve bu kalıpları veri odaklı önceliklendirme yaklaşımıyla birlikte kullanmasıdır.

Bununla birlikte, çalışmanın tek bir endüstriyel ortamla sınırlı olması, verilerin gizliliği, refactoring işlemlerinin tamamının gerçekleştirilememesi ve uzun vadeli bakım performansının sınırlı ölçüde değerlendirilmesi, bulguların yorumlanmasında dikkat edilmesi gereken unsurlardır.

Bu değerlendirme sonucunda, makalenin temel araştırma sorularına uygulamalı ve ölçülebilir yanıtlar sunduğu; ancak önerilen yaklaşımın farklı sistemlerde doğrulanması ve bakım performansına uzun vadeli etkilerinin ölçülmesiyle bilimsel katkısının daha da güçlendirilebileceği sonucuna ulaşılmıştır.

Genel olarak çalışma, nesneye dayalı programlama prensipleri ile yazılım bakım süreçleri arasındaki ilişkiyi gerçek bir endüstriyel problem üzerinden göstermesi bakımından başarılı bir uygulama örneği olarak değerlendirilmektedir.

## 9. Genel Sonuç

*İncelemeden elde edilen temel çıkarımlar ve çalışmanın nesneye dayalı programlama açısından önemi özetlenecektir.*

## Kaynakça

*İncelenen makale ve araştırma sürecinde yararlanılan akademik kaynaklar burada listelenecektir.*