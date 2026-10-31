# Araştırma Bulguları ve Sonuçların Değerlendirilmesi

## 1. İncelenen Makale

**Yazarlar:** Ivan Yanakiev, Bogdan-Mihai Lazar, Andrea Capiluppi

**Yıl:** 2025

**Başlık:** Applying SOLID principles for the refactoring of legacy code: An experience report

**Dergi:** Journal of Systems and Software, 220, 112254

**DOI:** https://doi.org/10.1016/j.jss.2024.112254

**İncelenen bölümler:** Bölüm 6 (Applying the Refactoring Patterns to Reduce Illegal Dependencies), Bölüm 7 (Discussion), Bölüm 8 (Threats to Validity) ve Bölüm 9 (Conclusion).

## 2. Araştırma Bulgularının Genel Çerçevesi

Yanakiev ve arkadaşları (2025), ASML'nin uzun yıllar boyunca geliştirilmiş C/C++ yazılım sistemindeki mimari bağımlılık ihlallerini azaltmak amacıyla veri odaklı önceliklendirme ve SOLID prensiplerine dayalı refactoring işlemleri gerçekleştirmiştir.

Araştırmada A, B ve C olarak anonimleştirilen üç bileşene odaklanılmıştır. Önceliklendirme sürecinde mevcut yazılım metriklerinden, mimari bağımlılık analizlerinden ve ASML yazılım mimarlarının alan bilgisinden yararlanılmıştır.

Uygulama aşamasında Dependency Inversion Principle (DIP) temel alınarak geliştirilen yedi refactoring kalıbı değerlendirilmiştir.

Çalışmanın bulguları, özellikle mimari bağımlılıkların azaltılması ve dışa aktarılmış sembollerin daha uygun bileşenlere yerleştirilmesi açısından incelenmektedir.

## 3. A ve B Bileşenleri Arasındaki Refactoring Sonuçları

Makalenin Table 4 tablosuna göre A ve B bileşenleriyle ilişkili bağımlılıklar için aşağıdaki dağılım raporlanmıştır:

| Refactoring kalıbı | Bağımlılık sayısı | Oran |
|---|---:|---:|
| R1M | 194 | %66,0 |
| R2M | 99 | %33,7 |
| R3M | 1 | %0,3 |
| **Toplam** | **294** | **%100** |

Bu sonuçlara göre R1M, A–B kapsamındaki işlemlerde en sık kullanılan refactoring kalıbıdır.

R1M kalıbı, uygunsuz biçimde dışa aktarılan sembollerin mantıksal olarak uygun alt seviye bileşene taşınmasına odaklanmaktadır.

R2M kalıbı, kullanılan sembollerin belirli alt kümelerinin uygun bileşene taşınmasıyla ilgilidir.

R3M ise gereksiz derleme bağımlılıklarının giderilmesini amaçlamaktadır.

Araştırmacılar, R2M kapsamında ele alınan bağımlılıkların %85'inden fazlasının tek bir arayüzde bulunduğunu belirterek dağılımın belirli bir arayüzden güçlü biçimde etkilendiğini vurgulamıştır.

Bu nedenle kalıpların kullanım sıklığını, farklı yazılım projelerindeki genel etkinlik sıralaması olarak değerlendirmek doğru değildir.

Ayrıca Table 4'teki 294 sayısı, tamamen ortadan kaldırılmış 294 ayrı bileşenler arası mimari ilişki anlamına gelmemektedir. Tablo, daha ayrıntılı bağımlılık işlemlerinin refactoring kalıplarına göre dağılımını göstermektedir.

## 4. A ve C Bileşenleri Arasındaki Refactoring Sonuçları

Makalenin Table 4 tablosunda ortak bileşenlerle ilişkili işlemler için aşağıdaki değerler verilmiştir:

| Refactoring kalıbı | Bağımlılık sayısı | Oran |
|---|---:|---:|
| R1C | 0 | %0 |
| R2C | 35 | %79,5 |
| R3C | 9 | %20,5 |
| R4C | 0 | %0 |
| **Toplam** | **44** | **%100** |

Bu dağılımda R2C kalıbı yaklaşık %80 ile en büyük paya sahiptir.

Ancak makalenin 6.2. bölümünde ortak bileşenler arasındaki bazı düzenlemelerin araştırma kapsamı dışında kaldığı belirtilmektedir.

Araştırmacılar, çalışma kapsamında makineye özgü bileşene taşınabilen dokuz bağımlılığın yeniden düzenlendiğini bildirmiştir.

Bu nedenle Table 4'te bulunan bütün işlemlerin fiilen tamamlandığını söylemek doğru değildir.

Ortak bileşenlerin birden fazla makine türü tarafından kullanılması, bu bileşenlerdeki değişikliklerin farklı geliştirme ekiplerini etkilemesine neden olmaktadır.

Araştırmacılar bu durumu, ortak bileşenlerin refactoring sürecinde alan bilgisi, mimari değerlendirme ve ekipler arası koordinasyon gerektiren önemli bir güçlük olarak ele almıştır.

## 5. Mimari Bağımlılıkların Azaltılması

Makalenin 6.1. bölümünde A–B kapsamındaki refactoring işlemleri sonucunda bir giden ve bir gelen uygunsuz bağımlılığın giderildiği ve araştırma kapsamında %33'lük bir azalma sağlandığı belirtilmektedir.

Buna karşılık makalenin 9. bölümündeki genel sonuç değerlendirmesinde, başlangıçta belirlenen dört uygunsuz bağımlılıktan ikisinin giderildiği ve toplam %50 azalma elde edildiği bildirilmektedir.

Genel sonuç bölümündeki oran aşağıdaki gibi hesaplanabilmektedir:

(2 / 4) × 100 = %50

Ancak makalenin 6.1. bölümündeki %33 oranının hesaplama tabanı aynı açıklıkla ortaya konulmamıştır.

Bu nedenle %33 ve %50 ifadelerinin aynı ölçüm kapsamına ait olduğu varsayılmamalıdır. Akademik raporda iki sonucun geçtiği bölümler ayrı ayrı belirtilmeli ve aralarındaki farkın yorumlanmasında dikkatli olunmalıdır.

## 6. Dışa Aktarılmış Sembollerdeki Azalma

Makalenin sonuç bölümünde, uygunsuz biçimde kullanılan dışa aktarılmış sembollerin sayısının %85'in üzerinde azaltıldığı raporlanmıştır.

Bu bulgu, mimari bağımlılıkların giderilmesinden farklı bir ölçüte karşılık gelmektedir.

Mimari bağımlılıkların azaltılması, bileşenler arasındaki kurallara aykırı ilişkilerin düzenlenmesiyle ilgilidir.

Dışa aktarılmış sembollerin azaltılması ise bu ilişkilerde uygunsuz biçimde kullanılan programlama öğelerinin yeniden konumlandırılması ve kapsüllenmesiyle ilişkilidir.

Dolayısıyla %85'in üzerindeki azalma, sistemdeki toplam teknik borcun aynı oranda giderildiği şeklinde yorumlanmamalıdır.

## 7. Birinci Araştırma Sorusu (RQ1) Açısından Değerlendirme

**RQ1:** Veri odaklı bir yaklaşım, endüstriyel ortamda mimari teknik borcun önceliklendirilmesine ve azaltılmasına nasıl katkıda bulunmaktadır?

Araştırmacılar, ASML'nin mevcut izleme süreçlerinden elde edilen metrikleri ve yazılım mimarlarının değerlendirmelerini kullanarak refactoring çalışmalarını önceliklendirmiştir.

Bu süreçte özellikle uygunsuz mimari bağımlılıkların azaltılması yüksek öncelikli hedef olarak belirlenmiştir.

Yazılımın tamamını aynı anda yeniden düzenlemek yerine, etki analizi sonucunda seçilen bileşenlere odaklanılmıştır.

Elde edilen sonuçlar, sınırlı kaynaklarla yürütülen bakım çalışmalarında mevcut metriklerin ve alan bilgisinin birlikte kullanılmasının faydalı olabileceğini göstermektedir.

Bununla birlikte, çalışma sonuçları tek bir endüstriyel uygulamaya dayanmaktadır. Dolayısıyla veri odaklı önceliklendirme yaklaşımının bütün yazılım sistemlerinde aynı düzeyde başarı sağlayacağı sonucuna doğrudan ulaşılamaz.

## 8. İkinci Araştırma Sorusu (RQ2) Açısından Değerlendirme

**RQ2:** SOLID tasarım prensipleri, incelenen yazılım sistemi için somut refactoring kalıplarına nasıl dönüştürülmektedir?

Araştırmacılar, Dependency Inversion Principle prensibini temel alarak yedi refactoring kalıbı tanımlamıştır.

Bu kalıplar; sembollerin uygun bileşenlere taşınması, kapsüllenmesi ve gereksiz derleme bağımlılıklarının düzeltilmesi gibi farklı işlemleri içermektedir.

Table 4 verileri, tanımlanan kalıpların incelenen mimari bağımlılık sorunlarına göre sınıflandırıldığını göstermektedir.

Çalışmanın önemli katkılarından biri, soyut bir tasarım prensibinin büyük ölçekli endüstriyel yazılımda kullanılabilecek tekrarlanabilir bakım işlemlerine dönüştürülmesidir.

Ancak kalıpların uygulanması, mevcut sistemin mimarisine ve bileşenler arasındaki ilişkilerin doğru analiz edilmesine bağlıdır.

## 9. Araştırmacıların Tartışmada Vurguladığı Çıkarımlar

Makalenin tartışma bölümünde aşağıdaki noktalar öne çıkmaktadır:

1. **Mevcut metriklerden yararlanma:** Özel bir analiz aracına bağımlı olmadan, kurum içinde mevcut olan veriler bakım faaliyetlerinin önceliklendirilmesinde kullanılabilir.

2. **Artımlı refactoring:** Büyük bir legacy sistemin tüm teknik borcunu tek seferde gidermek yerine, belirlenen sorunları aşamalı olarak ele almak daha yönetilebilir olabilir.

3. **SOLID prensiplerinin uygulanabilirliği:** Tasarım prensiplerinin somut refactoring kalıplarına dönüştürülmesi, bu prensiplerin endüstriyel kullanımına ilişkin pratik bir örnek sunmaktadır.

4. **Tekrarlanabilir kalıpların kullanımı:** Benzer mimari sorunların ortak kalıplarla ele alınması, büyük kod tabanlarında daha tutarlı bir bakım yaklaşımı sağlayabilir.

5. **Ekipler arası koordinasyon:** Özellikle ortak bileşenlerde gerçekleştirilen değişiklikler, birden fazla geliştirme ekibinin katılımını gerektirebilir.

## 10. Çalışmanın Sınırlılıklarına İlişkin İlk Notlar

Araştırma, ASML'nin belirli bir yazılım sistemi üzerinde gerçekleştirilmiş endüstriyel bir deneyim raporudur.

Bu nedenle elde edilen bulguların farklı organizasyonlara ve mimarilere aktarılabilirliği dikkatle değerlendirilmelidir.

Ayrıca araştırmanın kapsamı ve organizasyonel koşullar, belirlenen bütün bağımlılıkların giderilmesini engellemiştir.

Kullanılan verilerin gizli olması da sonuçların bağımsız olarak yeniden üretilmesini güçleştirebilir.

Makalenin farklı bölümlerinde raporlanan %33 ve %50 oranlarının hesaplama kapsamları da akademik raporda ayrıca tartışılabilecek bir açıklık sorunudur.

Bu konuların ayrıntılı eleştirisi, projenin eleştirel değerlendirme aşamasında yapılacaktır.

## 11. Kendi Ara Değerlendirmem

Bu çalışmadan çıkardığım temel sonuç, büyük ölçekli yazılım sistemlerinde teknik borcun giderilmesinin yalnızca kodun yeniden yazılmasıyla çözülebilecek bir problem olmadığıdır.

Öncelikle hangi bağımlılıkların daha yüksek etkiye sahip olduğu belirlenmeli, ardından uygun refactoring işlemleri seçilmelidir.

Makalede geliştirilen yedi kalıp, bu işlemleri sistematik hâle getirmek açısından önemlidir.

Buna karşılık ortak bileşenlerdeki sorunların tümünün giderilememiş olması, teknik açıdan uygun bir çözümün organizasyonel koşullar nedeniyle her zaman uygulanamayabileceğini göstermektedir.

Ayrıca sonuçların değerlendirilmesinde sembol düzeyindeki değişikliklerle bileşenler arası mimari bağımlılıkların birbirinden ayrılması gerekmektedir.

Bu ayrımın korunması, çalışmanın başarı düzeyinin doğru yorumlanması açısından önem taşımaktadır.

## Kaynakça

Yanakiev, I., Lazar, B.-M., & Capiluppi, A. (2025). Applying SOLID principles for the refactoring of legacy code: An experience report. *Journal of Systems and Software, 220*, 112254. https://doi.org/10.1016/j.jss.2024.112254