# Dependency Inversion Principle ve Refactoring Patterns İncelemesi

## 1. Araştırmanın Uygulama Aşaması

Yanakiev, Lazar ve Capiluppi (2025), ASML'nin mevcut C++ yazılım sistemindeki mimari bağımlılık sorunlarını azaltmak amacıyla SOLID tasarım prensiplerinden yararlanmıştır.

Çalışmanın uygulama aşaması özellikle Dependency Inversion Principle (DIP) prensibi üzerine kurulmuştur.

Araştırmacılar, mimari kurallara aykırı bağımlılıkları gidermek için gereken işlemleri belirlemiş ve benzer sorunların sistematik biçimde çözülebilmesi amacıyla bu işlemleri tekrarlanabilir refactoring kalıplarına dönüştürmüştür.

Bu yaklaşım makalenin ikinci araştırma sorusu (RQ2) ile doğrudan ilişkilidir.

## 2. Dependency Inversion Principle (DIP)

Dependency Inversion Principle, yüksek seviyeli yazılım modüllerinin düşük seviyeli modüllerin somut uygulamalarına doğrudan bağımlı olmaması, bunun yerine uygun soyutlamalara dayanması gerektiğini ifade etmektedir.

Bu prensip aynı zamanda soyutlamaların uygulama ayrıntılarına bağımlı olmamasını ve uygulama ayrıntılarının soyutlamalara uygun biçimde geliştirilmesini öngörmektedir.

İncelenen makalede DIP, ASML'nin katmanlı mimarisindeki uygunsuz bağımlılıkların giderilmesi için temel tasarım prensibi olarak benimsenmiştir.

Makaledeki uygulamalar yalnızca yeni arayüzler oluşturmakla sınırlı değildir. Mevcut sembollerin uygun bileşenlere taşınması, kapsüllenmesi ve bazı durumlarda gereksiz derleme bağımlılıklarının kaldırılması da bu kapsamda ele alınmaktadır.

## 3. Refactoring Patterns Kavramı

Refactoring Patterns, belirli yazılım tasarım sorunlarını gidermek amacıyla uygulanabilecek tekrarlanabilir yeniden düzenleme yaklaşımlarıdır.

Araştırmacılar, refactoring işlemlerini her bağımlılık için bağımsız olarak tasarlamak yerine, benzer mimari sorunları ortak kalıplar altında toplamıştır.

Makalenin 5. bölümünde kalıplar mevcut durum (AS-IS) ile hedeflenen durum (TO-BE) arasındaki mimari değişiklikler üzerinden açıklanmaktadır.

Kalıplar iki ana gruba ayrılmıştır:

- Machine-Dependent Refactoring Patterns: Belirli makine türlerine özgü bileşenlerde uygulanan üç kalıp.
- Machine-Independent Refactoring Patterns: Farklı makine türleri tarafından kullanılabilen ortak bileşenlerle ilişkili dört kalıp.

Toplam yedi refactoring kalıbı açıklanmıştır.

## 4. Machine-Dependent Refactoring Patterns

### 4.1. R1M — Exported Symbols

Bu kalıp, alt seviyedeki bir bileşenin üst seviyedeki bir bileşenden dışa aktarılan sembolleri mimari kurallara aykırı biçimde kullanması durumunda uygulanmaktadır.

Çözüm olarak ilgili sembollerin mantıksal açıdan uygun alt seviye bileşene taşınması ve kapsüllenmesi önerilmektedir.

Böylece uygunsuz bağımlılığın kaldırılması ve bileşen sınırlarının güçlendirilmesi amaçlanmaktadır.

### 4.2. R2M — Exported Symbols

Bu kalıp, alt seviyedeki bir bileşenin üst seviyede dışa aktarılan sembol listesinin yalnızca belirli bir kısmını kullanması durumuyla ilgilidir.

Örneğin üst bileşendeki hata kodları listesinden yalnızca iki kodun alt bileşende kullanılması söz konusu olabilir.

Bu durumda gerekli semboller alt seviyedeki bileşene taşınarak kapsülleme güçlendirilebilir ve gereksiz bağımlılıklar azaltılabilir.

### 4.3. R3M — Derleme Bağımlılığının Düzeltilmesi

Bu kalıp, bileşenlerin derleme yapılandırmasındaki gereksiz bağımlılıklardan kaynaklanan mimari ihlalleri ele almaktadır.

Bazı durumlarda bir bileşen, başka bir bileşenin sembollerini gerçekte kullanmadığı hâlde derleme bağımlılıkları nedeniyle ona bağımlı görünebilir.

R3M kapsamında bu gereksiz bağımlılık tanımı kaldırılarak yanlış pozitif mimari ihlallerin giderilmesi hedeflenmektedir.

Bu kalıbın önemli özelliği, kaynak kodun temel mimari yapısının değiştirilmesinden çok derleme kapsamının doğru tanımlanmasına odaklanmasıdır.

## 5. Machine-Independent Refactoring Patterns

### 5.1. R1C — Exported Symbols From Common Component

Bu kalıp, farklı makine türlerinde ortak kullanılabilen bileşenlerde ortaya çıkan uygunsuz sembol bağımlılıklarının giderilmesine yöneliktir.

İlgili sembol listesinin bağımlılık hiyerarşisinde uygun konumdaki başka bir ortak bileşene taşınması önerilmektedir.

Amaç, ortak işlevlerin yeniden kullanılabilirliğini koruyarak mimari bağımlılıkları düzenlemektir.

### 5.2. R2C — Ortak Sembol Listesinin Bir Bölümünün Taşınması

Bu kalıp, ortak bir bileşenden dışa aktarılan sembollerin belirli bir alt kümesinin uygun başka bir ortak bileşene taşınmasına odaklanmaktadır.

Sembollerin hangi bileşene yerleştirileceği, sistemin mimari yapısı ve kullanım alanına ilişkin bilgi gerektirmektedir.

### 5.3. R3C — Makineye Özgü Sembollerin Ayrılması

Bu kalıp, ortak bir bileşende bulunan belirli sembollerin yalnızca makineye özgü bir bileşen tarafından kullanılması durumunu ele almaktadır.

Bu sembollerin makineye özgü bileşene taşınması ve kapsüllenmesiyle ortak bileşenin yalnızca yeniden kullanılabilir işlevleri barındırması amaçlanmaktadır.

### 5.4. R4C — Ortak Bileşendeki Sembol Alt Kümesinin Kapsüllenmesi

Bu kalıp, ortak bileşenden dışa aktarılan bir sembol listesinin belirli bir alt kümesinin yalnızca tek bir makineye özgü bileşen tarafından kullanılması durumuyla ilgilidir.

İlgili sembol alt kümesi, onu kullanan bileşene taşınarak kapsüllenir.

Bu sayede hem mimari bağımlılık ihlalinin giderilmesi hem de gereksiz dışa açık sembollerin azaltılması hedeflenmektedir.

## 6. Refactoring Kalıplarının OOP ile İlişkisi

Makaledeki refactoring işlemleri, nesneye dayalı tasarımın özellikle soyutlama, kapsülleme, modülerlik ve bağımlılık yönetimi kavramlarıyla ilişkilidir.

Sembollerin doğru bileşenlere yerleştirilmesi, bileşen sorumluluklarının daha açık biçimde ayrılmasına yardımcı olabilir.

Dışa açık sembollerin gereksiz kullanımının azaltılması ise kapsüllemeyi güçlendirebilir.

Bununla birlikte, makaledeki bütün kalıplar sınıf seviyesinde değildir. Bazıları bileşenler arası mimari ilişkileri, bazıları ise derleme bağımlılıklarını düzenlemektedir.

Bu nedenle çalışmanın katkısı yalnızca OOP sınıflarının yeniden tasarlanması olarak değil, daha geniş kapsamlı bir mimari refactoring yaklaşımı olarak değerlendirilmelidir.

## 7. Araştırma Sorusu RQ2 ile İlişkisi

Makalenin ikinci araştırma sorusu, SOLID prensiplerinin mevcut yazılım sisteminde somut refactoring kalıplarına nasıl dönüştürülebileceğini incelemektedir.

Araştırmacılar, DIP prensibinden hareketle farklı bağımlılık sorunlarına uygulanabilecek yedi kalıp tanımlamıştır.

Bu kalıpların ortak amacı, mevcut mimari bağımlılıkların uygun biçimde yeniden düzenlenmesi ve benzer sorunların tekrarlanabilir adımlarla ele alınmasıdır.

Dolayısıyla RQ2 açısından çalışmanın temel yaklaşımı, soyut bir tasarım prensibini mevcut sistemin mimari ihtiyaçlarına uygun operasyonel işlemlere dönüştürmektir.

## 8. Ara Değerlendirme

Bu aşamadaki değerlendirmeme göre makalenin önemli yönlerinden biri, tasarım prensiplerini yalnızca kavramsal olarak açıklamak yerine gerçek bir endüstriyel yazılım sistemindeki bakım faaliyetlerine uyarlamasıdır.

Özellikle R3M kalıbı, mimari refactoring işlemlerinin her zaman sınıfların veya fonksiyonların taşınmasını gerektirmediğini göstermektedir.

Ortak bileşenlere yönelik kalıplar ise yazılım mimarisinin düzeltilmesinde yeniden kullanılabilirlik ve alan bilgisinin önemini ortaya koymaktadır.

Araştırmanın sonraki aşamasında bu kalıpların uygulanması sonucunda elde edilen sayısal bulgular ve çalışmanın sınırlılıkları incelenecektir.

## Kaynakça

Yanakiev, I., Lazar, B.-M., & Capiluppi, A. (2025). Applying SOLID principles for the refactoring of legacy code: An experience report. *Journal of Systems and Software, 220*, 112254. https://doi.org/10.1016/j.jss.2024.112254

İncelenen bölümler: Bölüm 5, Appendix A ve Appendix B.