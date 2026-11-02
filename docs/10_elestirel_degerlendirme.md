# Makalenin Eleştirel Değerlendirilmesi ve Geliştirme Önerileri

## 1. İncelenen Makale

**Yazarlar:** Ivan Yanakiev, Bogdan-Mihai Lazar ve Andrea Capiluppi

**Yıl:** 2025

**Başlık:** Applying SOLID principles for the refactoring of legacy code: An experience report

**Dergi:** Journal of Systems and Software, 220, 112254

**DOI:** https://doi.org/10.1016/j.jss.2024.112254

**İncelenen bölümler:** Bölüm 6 — Applying the Refactoring Patterns to Reduce Illegal Dependencies; Bölüm 7 — Discussion; Bölüm 8 — Threats to Validity; Bölüm 9 — Conclusion.

## 2. Eleştirel Değerlendirmenin Amacı

Bu incelemenin amacı, Yanakiev ve arkadaşlarının (2025) gerçekleştirdiği araştırmanın bilimsel ve teknik açıdan güçlü yönlerini, yöntemsel sınırlılıklarını ve geliştirilebilecek noktalarını değerlendirmektir.

Çalışma, ASML'nin yaklaşık yirmi yıllık geliştirme geçmişine sahip legacy C/C++ yazılım sisteminde birikmiş mimari teknik borcun azaltılmasına odaklanmaktadır.

Araştırmacılar, veri odaklı önceliklendirme yaklaşımını SOLID tasarım prensiplerinden özellikle Dependency Inversion Principle (DIP) ile birleştirerek tekrarlanabilir refactoring kalıpları geliştirmiştir.

Bu dosyada araştırmacıların doğrudan bildirdiği bulgular ve sınırlılıklar ile tarafımızdan geliştirilen eleştiri ve öneriler ayrı başlıklarda değerlendirilmektedir.

## 3. Araştırmanın Güçlü Yönleri

### 3.1. Gerçek Bir Endüstriyel Sistemde Uygulanması

Araştırmanın önemli güçlü yönlerinden biri, önerilen yaklaşımın yalnızca kuramsal düzeyde tartışılmaması ve gerçek bir endüstriyel yazılım sistemi üzerinde uygulanmasıdır.

ASML'nin büyük ölçekli yazılım sistemi, uzun geliştirme geçmişi ve mimari bağımlılık sorunları nedeniyle legacy yazılım bakımına ilişkin gerçekçi bir araştırma ortamı sunmaktadır.

Araştırmacılar, sistemdeki mevcut mimari kısıtları ve organizasyonel koşulları dikkate alarak refactoring faaliyetleri gerçekleştirmiştir.

**Kendi değerlendirmemiz:** Gerçek bir endüstriyel sistemde yapılan çalışma, yazılım mühendisliği prensiplerinin uygulamadaki güçlüklerini göstermesi açısından değerlidir. Özellikle mimari kararların yalnızca kod kalitesine değil, ekiplerin sorumluluklarına ve geliştirme süreçlerine de bağlı olduğunu ortaya koymaktadır.

### 3.2. Veri Odaklı Önceliklendirme Kullanılması

Araştırmacılar, yazılım sistemindeki bütün sorunları aynı anda gidermeye çalışmak yerine mevcut metrikleri, etki analizini ve yazılım mimarlarının değerlendirmelerini kullanarak refactoring önceliklerini belirlemiştir.

Uygunsuz mimari bağımlılıkların azaltılması, araştırma kapsamında en yüksek öncelikli hedef olarak seçilmiştir.

Bu yaklaşım, bakım çalışmalarının sınırlı zaman ve kaynaklarla gerçekleştirilmesi gerektiği durumlarda uygulanabilir bir karar verme çerçevesi sunmaktadır.

**Kendi değerlendirmemiz:** Önceliklendirme yapılması, yazılım bakımında kaynakların daha etkili kullanılmasına yardımcı olabilir. Bununla birlikte, önceliklendirme kararlarının ne ölçüde nesnel ve tekrarlanabilir olduğu ayrıca değerlendirilmelidir.

### 3.3. SOLID Prensiplerinin Somut Refactoring Kalıplarına Dönüştürülmesi

Çalışmanın önemli katkılarından biri, DIP prensibini yedi refactoring kalıbına dönüştürmesidir.

Kalıplar, makineye özgü ve ortak bileşenlerde karşılaşılan mimari bağımlılık sorunlarına göre sınıflandırılmıştır.

Araştırmacılar, mevcut durum (AS-IS) ile hedeflenen durum (TO-BE) arasındaki değişiklikleri açıklayarak benzer sorunlara uygulanabilecek düzenleme yaklaşımları sunmuştur.

**Kendi değerlendirmemiz:** Bu yaklaşım, soyut yazılım tasarım prensiplerinin büyük ölçekli projelerde nasıl somut bakım işlemlerine dönüştürülebileceğini göstermektedir.

### 3.4. Artımlı Refactoring Yaklaşımı

Araştırmacılar, birikmiş teknik borcun tamamını tek seferde gidermeye çalışmak yerine belirli bileşenlere odaklanmıştır.

Makalenin tartışma bölümünde artımlı refactoring yaklaşımının büyük ölçekli legacy sistemler açısından yönetilebilir bir strateji olduğu vurgulanmaktadır.

**Kendi değerlendirmemiz:** Bu yaklaşım, büyük bir yazılım sistemini tamamen yeniden yazmanın neden olabileceği maliyetleri ve operasyonel riskleri dikkate alması açısından olumludur.

Ancak artımlı yaklaşımın uzun vadeli etkilerini değerlendirmek için sonraki bakım dönemlerine ilişkin verilere de ihtiyaç duyulabilir.

## 4. Araştırmacıların Belirttiği Geçerlilik Sınırlılıkları

### 4.1. Dış Geçerlilik (External Validity)

Araştırmacılar, çalışmanın ASML'nin kendine özgü yazılım mimarisi, teknolojileri ve geliştirme süreçleri içerisinde yürütüldüğünü belirtmektedir.

Bu durum, sonuçların farklı şirketlere ve yazılım sistemlerine genellenebilirliğini sınırlandırabilir.

Bununla birlikte araştırmacılar, geliştirilen kalıpların katmanlı mimarilere sahip farklı sistemlere uyarlanabileceğini savunmaktadır.

**Kendi değerlendirmemiz:** Kalıpların farklı projelere uyarlanabilir olması mantıklı bir beklentidir. Ancak aynı düzeyde iyileşme sağlayacaklarının gösterilmesi için başka projelerde de değerlendirme yapılması gerekir.

### 4.2. İç Geçerlilik (Internal Validity)

Makalenin iç geçerlilik tartışmasında, refactoring kalıplarının mevcut bağımlılıkların analizi ve ASML yazılım mimarlarıyla gerçekleştirilen görüşmeler temelinde geliştirildiği açıklanmaktadır.

Yazılım mimarlarının alan bilgisi, sistemin mimari kurallarının doğru yorumlanmasına katkı sağlamıştır.

**Kendi değerlendirmemiz:** Alan uzmanlarının sürece katılması güçlü bir yön olmakla birlikte, refactoring sonuçlarının bağımsız ölçümlerle doğrulanması değerlendirmeyi daha da güçlendirebilir.

Özellikle gözlemlenen iyileşmelerin hangi kısmının refactoring işlemleriyle doğrudan ilişkilendirilebildiğinin açık biçimde gösterilmesi yararlı olacaktır.

## 5. Kendi Belirlediğimiz Yöntemsel Sınırlılıklar

Bu bölümdeki değerlendirmeler, makalede açıkça belirtilen bulguların tarafımızdan eleştirel açıdan yorumlanmasına dayanmaktadır.

### 5.1. Araştırmanın Tek Bir Endüstriyel Bağlamla Sınırlı Olması

Çalışmanın yalnızca ASML'nin belirli bir yazılım sistemi üzerinde gerçekleştirilmesi, geliştirilen refactoring kalıplarının başka sistemlerdeki etkisinin doğrudan gözlemlenememesi anlamına gelmektedir.

Farklı sektörlerde kullanılan yazılım sistemleri, ASML'den farklı mimari yapılara, geliştirme süreçlerine ve teknolojik kısıtlara sahip olabilir.

Bu nedenle elde edilen sonuçlar, öncelikle incelenen endüstriyel bağlam çerçevesinde değerlendirilmelidir.

### 5.2. Araştırma Verilerinin Gizli Olması

Makalenin Data Availability bölümünde kullanılan verilerin gizli olduğu belirtilmektedir.

Bu durum, bağımsız araştırmacıların aynı kaynak kodu ve verileri kullanarak refactoring işlemlerini tekrar gerçekleştirmesini güçleştirmektedir.

Ancak verilerin gizli olması tek başına araştırma sonuçlarının yanlış olduğu anlamına gelmemektedir.

**Eleştirel değerlendirmemiz:** Yöntemin bağımsız biçimde yeniden uygulanabilmesi için ayrıntılı deney prosedürlerinin ve gizlilik kurallarını ihlal etmeyen örneklerin paylaşılması yararlı olabilir.

### 5.3. Refactoring Kapsamının Sınırlı Kalması

Araştırmacılar, çalışmanın zaman ve organizasyonel koşullar nedeniyle kapsam açısından sınırlı kaldığını açıklamıştır.

Özellikle ortak bileşenlerdeki bazı bağımlılıkların giderilmesi, daha fazla ekip koordinasyonu gerektirdiği için tamamlanamamıştır.

Bu nedenle araştırmanın sonuçları, bütün mimari teknik borcun ortadan kaldırılması şeklinde yorumlanmamalıdır.

**Eleştirel değerlendirmemiz:** Tamamlanamayan refactoring işlemlerinin sonraki bakım dönemlerinde izlenmesi, önerilen yaklaşımın daha geniş ölçekte uygulanabilirliğinin değerlendirilmesine katkıda bulunabilir.

### 5.4. Yüzdesel Sonuçların Hesaplama Kapsamı

Makalenin 6.1. bölümünde bir giden ve bir gelen uygunsuz bağımlılığın giderilmesi sonucunda %33 azalma bildirilmektedir.

Buna karşılık sonuç bölümünde araştırma kapsamında belirlenen dört uygunsuz bağımlılıktan ikisinin giderilmesiyle %50 azalma elde edildiği açıklanmaktadır.

Sonuç bölümündeki hesaplama şu şekilde ifade edilebilir:

(2 / 4) × 100 = %50

Bununla birlikte 6.1. bölümünde belirtilen %33 oranının hesaplama tabanı aynı açıklıkta gösterilmemektedir.

**Eleştirel değerlendirmemiz:** İki oranın farklı olması tek başına hesaplama hatası bulunduğunu kanıtlamaz. Ancak hangi bağımlılık türlerinin ve hangi başlangıç değerlerinin kullanıldığının daha açık biçimde sunulması, sonuçların anlaşılmasını kolaylaştıracaktır.

### 5.5. Başarı Ölçütlerinin Kapsamı

Araştırmacılar, uygunsuz mimari bağımlılıkların azaltılması ve dışa aktarılmış sembollerin yeniden düzenlenmesi açısından sonuçlar raporlamıştır.

Sonuç bölümünde uygunsuz kullanılan dışa aktarılmış sembollerde %85'in üzerinde azalma bildirilmektedir.

Bununla birlikte, bu iyileşmenin yazılımın bakım maliyeti, geliştirici verimliliği veya sonraki hata oranları üzerindeki uzun vadeli etkileri aynı kapsamda nicel olarak gösterilmemektedir.

**Eleştirel değerlendirmemiz:** Mimari bağımlılıkların azaltılması anlamlı bir sonuçtur. Ancak bunun bakım süresini veya bakım maliyetini ne ölçüde iyileştirdiğini gösterecek ek ölçümler, çalışmanın pratik etkisini daha güçlü biçimde değerlendirmeyi sağlayabilir.

## 6. Geliştirme Önerilerimiz

Aşağıdaki öneriler araştırmacıların gerçekleştirdiği işlemler değildir. Çalışmanın sınırlılıklarını dikkate alarak tarafımızdan geliştirilen gelecekteki araştırma önerileridir.

### 6.1. Farklı Endüstriyel Sistemlerde Doğrulama

Geliştirilen yedi refactoring kalıbı, farklı şirketlere ve yazılım mimarilerine sahip projelerde uygulanarak karşılaştırılabilir.

Örneğin katmanlı mimariye sahip başka bir C++ projesinde veya benzer bileşen bağımlılıkları içeren Java ve C# sistemlerinde kalıpların uygulanabilirliği araştırılabilir.

Böyle bir karşılaştırma, kalıpların hangi koşullarda kullanılabildiğini ve hangi durumlarda uyarlama gerektirdiğini belirlemeye yardımcı olabilir.

### 6.2. Anonimleştirilmiş Örnek Proje Oluşturulması

ASML'nin ticari gizliliğini koruyacak biçimde, araştırmada incelenen sorunları temsil eden küçük bir örnek proje hazırlanabilir.

Bu projede refactoring öncesi ve sonrası bağımlılık yapıları, derleme yapılandırmaları ve test senaryoları sunulabilir.

Böylece farklı araştırmacılar, önerilen kalıpları gerçek şirket verilerine erişmeden uygulama ve değerlendirme olanağı bulabilir.

### 6.3. Öncesi-Sonrası Ölçümlerin Ayrıntılandırılması

Refactoring işlemleri öncesinde ve sonrasında aynı ölçütlerin kaydedildiği standart tablolar kullanılabilir.

Örneğin şu bilgiler ayrı ayrı sunulabilir:

- Başlangıçtaki uygunsuz mimari bağımlılık sayısı.
- Tamamen kaldırılan mimari bağımlılık sayısı.
- Sembol seviyesinde düzeltilen bağımlılık sayısı.
- Tamamlanan ve tamamlanamayan refactoring işlemleri.
- Her iyileşme oranının başlangıç ve sonuç değerleri.

Böylece farklı ölçüm düzeyleri birbirine karıştırılmadan raporlanabilir.

### 6.4. Yazılım Bakımına Etkinin Ölçülmesi

Refactoring işlemlerinin yazılımın uzun vadeli bakım süreçlerine etkisi ek ölçütlerle değerlendirilebilir.

Bu kapsamda refactoring öncesi ve sonrası bakım süreleri, değişiklik gerçekleştirme maliyetleri, hata düzeltme süreleri ve geliştirici iş yükü incelenebilir.

Ayrıca bu ölçümleri etkileyebilecek ekip deneyimi, geliştirme araçları ve süreç değişiklikleri gibi faktörler de kontrol edilmelidir.

Böylece mimari iyileştirmeler ile bakım performansı arasındaki ilişki daha güçlü kanıtlarla değerlendirilebilir.

### 6.5. Otomatik Bağımlılık Analizi ile Destekleme

Araştırmada geliştirilen refactoring kalıplarını desteklemek amacıyla uygun mimari bağımlılık analiz araçları kullanılabilir.

Bu araçlar, bileşenler arasındaki ilişkileri tespit etme ve refactoring öncesi-sonrası yapıları karşılaştırma süreçlerinde yardımcı olabilir.

Ancak böyle bir yaklaşımın uygulanması, ilgili şirketin güvenlik politikalarına ve mevcut geliştirme altyapısına uygun olmalıdır.

### 6.6. Tamamlanamayan Refactoring İşlemlerinin İzlenmesi

Araştırma kapsamında tamamlanamayan ortak bileşen düzenlemeleri için sonraki bakım dönemlerini kapsayan bir takip planı oluşturulabilir.

Bu planda işlemlerin öncelikleri, etkilenen ekipler, tahmini maliyetleri ve tamamlanma durumları kaydedilebilir.

Böylece artımlı refactoring yaklaşımının yalnızca kısa vadeli sonuçları değil, uzun vadeli sürdürülebilirliği de değerlendirilebilir.

## 7. Güçlü Yönler, Sınırlılıklar ve Önerilerin Özeti

| Değerlendirme alanı | Güçlü yön veya sınırlılık | Önerimiz |
|---|---|---|
| Endüstriyel uygulama | Gerçek C++ sisteminde değerlendirme | Farklı sistemlerde doğrulama |
| Önceliklendirme | Metrik ve etki analizi kullanılması | Karar ölçütlerinin ayrıntılandırılması |
| Refactoring kalıpları | Yedi tekrarlanabilir kalıp | Açık örneklerle yeniden uygulanabilirlik |
| Veri erişimi | Gizli endüstriyel veriler | Anonimleştirilmiş örnek proje |
| Sonuçların sunumu | Birden fazla iyileşme ölçütü | Öncesi-sonrası ölçüm tabloları |
| Çalışma kapsamı | Bazı bağımlılıkların giderilememesi | Uzun vadeli takip planı |
| Bakım etkisi | Mimari bağımlılıkların azaltılması | Bakım maliyeti ve sürelerinin ölçülmesi |

## 8. RQ1 ve RQ2 Açısından Eleştirel Değerlendirme

### 8.1. RQ1 — Veri Odaklı Önceliklendirme

Araştırmacılar, mevcut yazılım metrikleri ve alan uzmanlarının değerlendirmelerinden yararlanarak belirli bileşenlerin refactoring için öncelikli olduğunu belirlemiştir.

Bu yaklaşım, büyük ölçekli yazılım sistemlerinde bakım kaynaklarının sınırlı olduğu durumlar için anlamlı bir uygulama örneğidir.

Ancak önceliklendirme kararlarının daha ayrıntılı ölçütlerle belgelenmesi ve farklı sistemlerde karşılaştırılması, yöntemin uygulanabilirliğine ilişkin daha güçlü sonuçlar sağlayabilir.

### 8.2. RQ2 — SOLID Prensiplerinin Refactoring Kalıplarına Dönüştürülmesi

Araştırmacılar, DIP prensibini yedi somut refactoring kalıbına dönüştürerek teorik tasarım ilkelerini mevcut bir endüstriyel yazılım sisteminde uygulanabilir işlemler hâline getirmiştir.

Bu yönüyle araştırma, SOLID prensiplerinin pratik değerini göstermektedir.

Bununla birlikte kalıpların farklı programlama dilleri, yazılım mimarileri ve geliştirme süreçlerinde nasıl uyarlanması gerektiği gelecekte yapılabilecek çalışmalar için önemli bir araştırma konusudur.

## 9. Kişisel Akademik Değerlendirme

Bu makaleyi inceleme sürecinde vardığım temel sonuç, yazılım mimarisinin iyileştirilmesinin yalnızca kod seviyesinde gerçekleştirilen değişikliklerden ibaret olmadığıdır.

Büyük ölçekli ve uzun ömürlü yazılım sistemlerinde hangi sorunların öncelikle giderileceğini belirlemek, teknik çözümü uygulamak kadar önemlidir.

Yanakiev ve arkadaşlarının çalışmasının güçlü yönü, mevcut yazılım metriklerini, alan uzmanlarının bilgisini ve SOLID prensiplerini bir araya getirerek gerçek bir bakım problemi için sistematik yaklaşım sunmasıdır.

Çalışmanın en dikkat çekici yönlerinden biri, Dependency Inversion Principle prensibinin soyut bir tasarım kuralı olarak bırakılmaması ve uygulanabilir refactoring kalıplarına dönüştürülmesidir.

Bununla birlikte, tek bir endüstriyel ortamda elde edilen bulguların farklı sistemlere genellenmesinde dikkatli olunmalıdır. Ayrıca gizli veriler ve çalışma kapsamı, araştırmanın bağımsız doğrulanabilirliğini ve elde edilen iyileşmelerin uzun vadeli etkilerinin değerlendirilmesini sınırlandırmaktadır.

Bana göre çalışmanın geliştirilmesi gereken en önemli yönü, refactoring başarısının yalnızca mimari bağımlılık ölçütleriyle değil, bakım maliyetleri ve uzun vadeli sürdürülebilirlik göstergeleriyle de değerlendirilmesidir.

Bu tür ek ölçümler, SOLID prensiplerinin mevcut kod tabanına uygulanmasının teknik yararlarının yanında yazılım geliştirme süreçlerine katkısını da daha açık biçimde gösterebilir.

Sonuç olarak, araştırma hem nesneye dayalı tasarım prensiplerinin endüstriyel uygulamaları hem de mimari teknik borcun yönetimi açısından değerli bir örnek sunmaktadır. Belirlenen sınırlılıklar ise çalışmanın sonuçlarını bütünüyle geçersiz kılmaktan ziyade gelecekte yapılabilecek araştırmalar için geliştirme alanları oluşturmaktadır.

## 10. Kaynakça

Yanakiev, I., Lazar, B.-M., & Capiluppi, A. (2025). Applying SOLID principles for the refactoring of legacy code: An experience report. *Journal of Systems and Software, 220*, 112254. https://doi.org/10.1016/j.jss.2024.112254