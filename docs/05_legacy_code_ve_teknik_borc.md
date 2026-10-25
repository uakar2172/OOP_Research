# Legacy Code, Teknik Borç ve Refactoring

## 1. Legacy Code Kavramı

Legacy Code, geçmişte geliştirilmiş ve günümüzde kullanılmaya devam edilen mevcut yazılım kodunu ifade etmektedir. Bu tür yazılımlar, uzun yıllar boyunca farklı geliştiriciler tarafından güncellenmiş ve genişletilmiş olabilir.

Bir yazılımın Legacy Code olarak değerlendirilmesi, mutlaka hatalı veya işlevsiz olduğu anlamına gelmemektedir. Mevcut sistem çalışmaya devam etse bile kodun anlaşılması, değiştirilmesi ve yeni gereksinimlere uyarlanması zorlaşabilir.

Özellikle karmaşık bağımlılıklar, yetersiz dokümantasyon ve sınırlı test kapsamı, mevcut yazılım sistemlerinin bakımını güçleştirebilen faktörler arasındadır.

## 2. Technical Debt (Teknik Borç)

Teknik borç, yazılım geliştirme sürecinde alınan tasarım ve uygulama kararlarının gelecekte ek bakım ve geliştirme maliyetleri oluşturmasını ifade eden bir kavramdır.

Teknik borç, kısa vadeli ihtiyaçlar doğrultusunda bilinçli olarak alınan kararlardan kaynaklanabileceği gibi zaman içerisinde değişen gereksinimler ve yeterince iyileştirilmeyen yazılım yapıları nedeniyle de birikebilir.

Teknik borç kavramı, finansal borç benzetmesiyle açıklanabilmektedir. Mevcut tasarım sorunlarını gidermek için gereken yeniden düzenleme maliyeti borcun anaparasına, sorunlar devam ettiği sürece ortaya çıkan ek bakım maliyetleri ise borcun faizine benzetilebilir.

### 2.1. Code-Level Technical Debt

Kod seviyesindeki teknik borç, tek tek metotların, sınıfların veya uygulama ayrıntılarının yapısından kaynaklanan bakım sorunlarını kapsamaktadır.

Örneğin bir metodun gereğinden fazla sorumluluk taşıması, anlaşılması zor koşul yapıları veya tekrarlanan kod parçaları bu kapsamda değerlendirilebilir.

Bu tür sorunlar, uygun refactoring işlemleriyle azaltılabilir.

### 2.2. Architectural Technical Debt

Mimari teknik borç, yazılım sistemindeki bileşenlerin organizasyonu, birbirleriyle ilişkileri ve bağımlılık yapılarından kaynaklanan sorunları ifade etmektedir.

Bileşenler arasındaki sıkı bağlılıklar, çok sayıda bağımlılığın oluşması ve tanımlanan mimari kuralların ihlal edilmesi bu kapsamda ele alınabilir.

Kod seviyesindeki teknik borç daha yerel sorunlarla ilişkiliyken mimari teknik borç, birden fazla bileşeni etkileyebilen daha geniş kapsamlı sorunlar oluşturabilir.

## 3. Refactoring Kavramı

Refactoring, bir yazılım sisteminin dışarıdan gözlemlenen davranışını koruyarak iç yapısının yeniden düzenlenmesidir.

Bu işlem yazılımın okunabilirliğini, bakım yapılabilirliğini ve değiştirilebilirliğini iyileştirmeyi amaçlamaktadır.

Örneğin uzun bir metodun daha küçük metotlara ayrılması veya bir sınıfın somut uygulamalara olan bağımlılıklarının uygun soyutlamalar üzerinden yeniden düzenlenmesi refactoring kapsamında gerçekleştirilebilir.

Refactoring işlemleri, yeni özellik geliştirme veya hatalı davranışı düzeltme işlemleriyle aynı değildir. Temel amaç mevcut davranışı korurken yazılımın iç tasarımını iyileştirmektir.

Bununla birlikte refactoring sırasında istenmeyen davranış değişiklikleri oluşabileceğinden, otomatik testler ve uygun doğrulama yöntemleri önem taşımaktadır.

## 4. İncelenen Makale ile İlişkisi

Yanakiev, Lazar ve Capiluppi (2025) tarafından gerçekleştirilen araştırma, ASML şirketinde yaklaşık yirmi yıllık geliştirme sürecinde biriken mimari teknik borcun azaltılmasına odaklanmaktadır.

Araştırmanın gerçekleştirildiği C++ yazılım sisteminde çeşitli kodlama standartları ve analiz araçları bulunmasına rağmen mimari bağımlılık sorunlarının devam ettiği belirtilmektedir.

Makalenin giriş bölümünde özellikle şu problemler vurgulanmaktadır:

- **Tight Coupling:** Yazılım bileşenleri arasında sıkı bağlılıkların bulunması.
- **Large Fan-out:** Bileşenlerin çok sayıda başka bileşene bağımlı olması.
- **Illegal Dependencies:** Yazılım sisteminin tanımlanmış mimari bağımlılık kurallarının ihlal edilmesi.

Çalışmada bu sorunların giderilmesi amacıyla mevcut yazılım bileşenleri üzerinde refactoring işlemleri gerçekleştirilmektedir.

Araştırmacılar, özellikle Dependency Inversion Principle (DIP) prensibinden yararlanarak mimari bağımlılıkların yeniden düzenlenmesini ele almaktadır.

Bunun yanında, benzer mimari sorunlar için gerçekleştirilen kod değişiklikleri tekrarlanabilir refactoring kalıplarına dönüştürülmektedir.

## 5. Ara Değerlendirme

İncelenen makalede Legacy Code kavramı, yalnızca eski bir yazılımın varlığını değil, uzun yıllar boyunca biriken mimari bağımlılık sorunlarının yönetilmesi gerekliliğini ortaya koymaktadır.

Bu açıdan çalışmanın temel problemi, tek tek metotların okunabilirliğinden daha geniş kapsamlıdır. Araştırmacılar sistemin bileşenler arası ilişkilerini iyileştirmeye odaklanmaktadır.

SOLID prensiplerinin, özellikle DIP'nin, mimari teknik borcun azaltılmasında kullanılmasının gerekçesi de bu bağımlılık sorunlarıyla ilişkilidir.

Araştırmanın sonraki aşamasında hangi bileşenlerin öncelikli olarak seçildiği, kullanılan ölçümler ve refactoring yöntemleri daha ayrıntılı incelenecektir.

## Kaynakça

Yanakiev, I., Lazar, B.-M., & Capiluppi, A. (2025). Applying SOLID principles for the refactoring of legacy code: An experience report. *Journal of Systems and Software, 220*, 112254. https://doi.org/10.1016/j.jss.2024.112254