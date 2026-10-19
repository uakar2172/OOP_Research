# Makalenin Amacı ve Araştırma Soruları

## 1. Araştırma Problemi

Yanakiev, Lazar ve Capiluppi (2025) tarafından gerçekleştirilen çalışma, uzun yıllar boyunca geliştirilen büyük ölçekli yazılım sistemlerinde biriken mimari teknik borcun azaltılmasını ele almaktadır.

Araştırmanın gerçekleştirildiği ASML şirketinde, yazılım geliştirme standartları ve çeşitli analiz araçları bulunmasına rağmen mimari düzeyde bağımlılık problemleri oluşmuştur. Özellikle bileşenler arasındaki sıkı bağlılıklar ve mimari kurallara aykırı bağımlılıklar, yazılımın bakımını ve geliştirilmesini zorlaştıran unsurlar olarak belirtilmektedir.

Bu durum, yalnızca kodlama standartlarının uygulanmasının yazılım mimarisindeki bütün sorunları önlemek için yeterli olmadığını göstermektedir.

## 2. Araştırmanın Amacı

Çalışmanın temel amacı, ASML'nin mevcut yazılım sisteminde mimari teknik borcun azaltılmasına yönelik uygulanabilir bir refactoring yaklaşımı geliştirmek ve değerlendirmektir.

Bu amaç doğrultusunda araştırmacılar, mevcut yazılım ölçümlerinden yararlanarak bakım açısından öncelikli üç bileşen belirlemeyi ve bu bileşenlerde SOLID tasarım prensiplerini uygulamayı hedeflemiştir.

Özellikle Dependency Inversion Principle (DIP) prensibinin somut kod düzenleme işlemlerine dönüştürülmesi üzerinde durulmaktadır.

## 3. Araştırma Soruları

### 3.1. RQ1 — Veriye Dayalı Önceliklendirme

**Araştırma sorusu:** Veriye dayalı bir yaklaşım, endüstriyel yazılım sistemlerinde mimari teknik borcun azaltılmasına yönelik çalışmaların önceliklendirilmesine nasıl katkı sağlar?

Bu soru, büyük ölçekli bir yazılım sisteminde bakım çalışmalarına hangi bileşenlerden başlanması gerektiğini belirleme problemiyle ilgilidir.

Araştırmacılar, mevcut yazılım ve süreç ölçümlerinin bakım faaliyetlerinin önceliklendirilmesinde nasıl kullanılabileceğini incelemektedir.

### 3.2. RQ2 — SOLID Prensiplerinin Uygulanması

**Araştırma sorusu:** SOLID tasarım prensipleri, mevcut yazılım sistemine uygulanabilecek somut refactoring kalıplarına nasıl dönüştürülebilir?

Bu soru, soyut yazılım tasarım prensiplerinin gerçek bir endüstriyel yazılım sisteminde nasıl uygulanabileceğine odaklanmaktadır.

Araştırmacılar özellikle Dependency Inversion Principle prensibini uygulamak için gerekli kod değişikliklerini incelemekte ve tekrarlanabilir refactoring kalıpları oluşturmayı amaçlamaktadır.

## 4. Araştırma Soruları Arasındaki İlişki

İki araştırma sorusu birbirini tamamlamaktadır.

RQ1, yazılım sisteminde hangi bileşenlerin öncelikli olarak yeniden düzenlenmesi gerektiğine odaklanırken RQ2, seçilen bileşenlerde hangi refactoring işlemlerinin uygulanacağını ele almaktadır.

Bu açıdan çalışma, mimari teknik borcun azaltılmasında hem doğru müdahale alanlarının belirlenmesini hem de uygun tasarım prensiplerinin uygulanmasını kapsamaktadır.

## Kaynak

Yanakiev, I., Lazar, B.-M., & Capiluppi, A. (2025). Applying SOLID principles for the refactoring of legacy code: An experience report. *Journal of Systems and Software, 220*, 112254. https://doi.org/10.1016/j.jss.2024.112254