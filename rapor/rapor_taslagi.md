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

### 3.4. Refactoring Kavramı

*Bu bölümde makalenin anlaşılması için gerekli temel kavramlar açıklanacaktır.*

## 4. Makalenin Araştırma Yöntemi

*Çalışmanın gerçekleştirildiği yazılım ortamı, kullanılan ölçütler, önceliklendirme yaklaşımı ve uygulama süreci incelenecektir.*

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