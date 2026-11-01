# Temel Akademik Kaynakların İncelenmesi

## 1. İncelemenin Amacı

Bu dosyada Yanakiev, Lazar ve Capiluppi (2025) tarafından yayımlanan *Applying SOLID principles for the refactoring of legacy code: An experience report* başlıklı makalenin bilimsel altyapısını oluşturan dört temel çalışma incelenmektedir.

Seçilen çalışmaların tamamı, incelenen makalenin kaynakçasında bulunmakta ve makale metninde atıf almaktadır.

Literatür incelemesinin amacı, yalnızca önceki araştırmaları özetlemek değil; bu kaynakların seçilen makalenin problem tanımına, araştırma yöntemine ve uygulama yaklaşımına nasıl katkıda bulunduğunu açıklamaktır.

İncelenen çalışmalar şunlardır:

1. Martin (2003) — Nesneye dayalı tasarım prensipleri.
2. Lenarduzzi ve arkadaşları (2021) — Teknik borcun önceliklendirilmesi.
3. Parnas (1994) — Yazılım yaşlanması.
4. Abid ve arkadaşları (2020) — Refactoring araştırmalarının sistematik literatür incelemesi.

## 2. KAYNAK 1 — Martin (2003)

### 2.1. Bibliyografik Bilgiler

**Yazar:** Robert C. Martin

**Yıl:** 2003

**Başlık:** Agile Software Development: Principles, Patterns, and Practices

**Yayınevi:** Prentice Hall

**Yayın türü:** Kitap

**Kaynak bağlantısı:** https://books.google.com/books?id=Ak8OtwAACAAJ

### 2.2. Çalışmanın Amacı ve Kapsamı

Martin'in çalışması, nesneye dayalı yazılım geliştirmede tasarım prensiplerinin, tasarım kalıplarının ve geliştirme pratiklerinin kullanımını açıklamaktadır.

Kitap, yazılımın karmaşıklığı arttıkça ortaya çıkabilecek tasarım ve bakım sorunlarına karşı uygulanabilecek prensipleri ele almaktadır.

Çalışmada yazılımın yalnızca mevcut gereksinimleri karşılaması değil, gelecekteki değişikliklere de uyum sağlayabilmesi üzerinde durulmaktadır.

### 2.3. Yaklaşım ve Temel Katkı

Bu eser bir endüstriyel deney raporu veya sistematik literatür taraması değildir. Yazılım tasarım prensiplerini ve bunların uygulamalarını açıklayan temel bir yazılım mühendisliği kitabıdır.

Nesneye dayalı tasarımda sorumlulukların ayrılması, soyutlamaların kullanılması ve bağımlılıkların yönetilmesi gibi konulara teorik ve uygulamalı bir çerçeve sunmaktadır.

Dependency Inversion Principle (DIP) yaklaşımı, yüksek seviyeli modüllerin düşük seviyeli somut uygulamalara doğrudan bağımlı olmaması ve uygun soyutlamalar üzerinden ilişki kurması gerektiğini vurgulamaktadır.

### 2.4. Yanakiev ve Arkadaşlarının Makalesiyle İlişkisi

Yanakiev ve arkadaşları (2025), giriş bölümünde SOLID tasarım prensiplerini açıklarken Martin'in 2003 tarihli çalışmasına atıfta bulunmaktadır.

ASML'nin legacy C++ sisteminde gerçekleştirilen refactoring işlemleri özellikle DIP prensibinden hareketle tasarlanmıştır.

Dolayısıyla Martin (2003), incelenen makalenin yazılım tasarımı açısından teorik temelini oluşturan kaynaklardan biridir.

### 2.5. Bizim Değerlendirmemiz

Martin'in çalışması, OOP prensiplerinin yazılım bakımındaki önemini anlamak için yararlıdır.

Yanakiev ve arkadaşlarının katkısı ise bu prensipleri yalnızca açıklamak değil, belirli bir endüstriyel yazılım mimarisinde uygulanabilir refactoring kalıplarına dönüştürmektir.

Bu nedenle iki çalışma arasında teorik temel ile endüstriyel uygulama ilişkisi bulunmaktadır.

## 3. KAYNAK 2 — Lenarduzzi ve Arkadaşları (2021)

### 3.1. Bibliyografik Bilgiler

**Yazarlar:** Valentina Lenarduzzi, Terese Besker, Davide Taibi, Antonio Martini ve Francesca Arcelli Fontana

**Yıl:** 2021

**Başlık:** A systematic literature review on Technical Debt prioritization: Strategies, processes, factors, and tools

**Dergi:** Journal of Systems and Software

**Cilt:** 171

**Makale numarası:** 110827

**DOI:** https://doi.org/10.1016/j.jss.2020.110827

**Yayın türü:** Hakemli dergi makalesi — sistematik literatür taraması

### 3.2. Araştırmanın Amacı

Bu çalışmanın amacı, teknik borcun önceliklendirilmesinde kullanılan stratejileri, süreçleri, faktörleri ve araçları sistematik biçimde incelemektir.

Araştırma, yazılım geliştirme ekiplerinin hangi teknik borç sorunlarını öncelikle gidermesi gerektiğine ilişkin bilimsel bilgi birikimini değerlendirmektedir.

### 3.3. Araştırma Yöntemi

Araştırmacılar sistematik literatür taraması (Systematic Literature Review — SLR) yöntemini kullanmıştır.

Çalışma kapsamında 557 benzersiz yayın değerlendirilmiş ve belirlenen seçim ile kalite ölçütlerinden geçen 44 birincil çalışma analize dâhil edilmiştir.

Böylece teknik borç önceliklendirmesine ilişkin önceki araştırmalar ortak bir çerçevede karşılaştırılmıştır.

### 3.4. Temel Bulgular

Araştırmada teknik borcun önceliklendirilmesi için farklı yaklaşımların önerildiği görülmüştür.

Bu yaklaşımlar arasında yazılım kalitesinin iyileştirilmesi, geliştirici verimliliğinin artırılması, yazılım doğruluğunun korunması ve maliyet-fayda değerlendirmeleri bulunmaktadır.

Çalışmanın önemli sonuçlarından biri, teknik borcun hangi faktörlere göre önceliklendirilmesi gerektiği konusunda genel kabul görmüş tek bir yaklaşımın bulunmamasıdır.

Ayrıca teknik borç önceliklendirme araçlarının ve ölçütlerinin ampirik doğrulanmasına ilişkin eksiklikler vurgulanmaktadır.

### 3.5. Yanakiev ve Arkadaşlarının Makalesiyle İlişkisi

Yanakiev ve arkadaşları (2025), araştırmalarında teknik borcun önceliklendirilmesini ele alırken Lenarduzzi ve arkadaşlarının bakım kategorisine atıfta bulunmaktadır.

ASML örneğinde mevcut yazılım metrikleri, mimari bağımlılık problemleri ve yazılım mimarlarının değerlendirmeleri birlikte kullanılmıştır.

Önceliklendirme sonucunda uygunsuz mimari bağımlılıkların giderilmesi en yüksek öncelikli hedef olarak belirlenmiştir.

Bu yönüyle Lenarduzzi ve arkadaşlarının çalışması, seçilen makalenin birinci araştırma sorusunun (RQ1) bilimsel arka planına katkıda bulunmaktadır.

### 3.6. Bizim Değerlendirmemiz

Lenarduzzi ve arkadaşları, teknik borcun önceliklendirilmesini literatür düzeyinde araştırırken Yanakiev ve arkadaşları belirli bir endüstriyel sistemde önceliklendirme gerçekleştirmiştir.

ASML'deki öncelik sıralamasının bütün yazılım projeleri için geçerli evrensel bir sıralama olmadığı dikkate alınmalıdır.

Bu iki çalışma birlikte değerlendirildiğinde, teknik borç yönetiminde mevcut metriklerin yanında sistemin mimarisi ve kurumsal hedeflerinin de önem taşıdığı görülmektedir.

## 4. KAYNAK 3 — Parnas (1994)

### 4.1. Bibliyografik Bilgiler

**Yazar:** David Lorge Parnas

**Yıl:** 1994

**Başlık:** Software Aging

**Yayın:** Proceedings of the 16th International Conference on Software Engineering

**Sayfalar:** 279–287

**DOI:** https://doi.org/10.1109/ICSE.1994.296790

**Yayın türü:** Konferans bildirisi

### 4.2. Çalışmanın Amacı

Parnas'ın çalışması, yazılım sistemlerinin zamanla neden bakım ve sürdürülebilirlik sorunları yaşayabileceğini incelemektedir.

Yazılımın yaşlanması, yalnızca yazılımın eski bir tarihte geliştirilmiş olması anlamına gelmemektedir.

Zaman içerisinde yazılımın değişen ihtiyaçlara uyum sağlayamaması veya yapılan değişikliklerin mevcut yapıyı olumsuz etkilemesi de yaşlanmaya neden olabilmektedir.

### 4.3. Yaklaşım ve Temel Katkı

Parnas, yazılım yaşlanmasını iki temel neden üzerinden ele almaktadır:

1. Yazılımın değişen gereksinimlere uyarlanamaması.
2. Yazılımda gerçekleştirilen değişikliklerin mevcut yapıyı ve bakım kolaylığını olumsuz etkilemesi.

Çalışma, yazılım mühendisliğinde yalnızca ilk sürümün geliştirilmesine değil, yazılımın uzun vadeli sağlığına da odaklanılması gerektiğini vurgulamaktadır.

Bu nedenle yazılım yaşlanmasının etkilerini azaltmak için bakım, yeniden düzenleme ve uzun vadeli tasarım kararları önem kazanmaktadır.

### 4.4. Yanakiev ve Arkadaşlarının Makalesiyle İlişkisi

Yanakiev ve arkadaşları (2025), ilgili çalışmalar bölümünde yazılım yaşlanması kavramına değinirken Parnas'ın 1994 tarihli çalışmasına atıfta bulunmaktadır.

ASML'nin incelenen C++ sistemi, yaklaşık yirmi yıllık geliştirme geçmişine sahip bir legacy yazılımdır.

Bu süre boyunca biriken uygunsuz mimari bağımlılıklar ve teknik borç, yazılımın bakım faaliyetlerini zorlaştırmaktadır.

Parnas'ın çalışması, bu tür problemlerin neden uzun ömürlü yazılım sistemlerinde ortaya çıkabileceğini anlamak açısından teorik temel sunmaktadır.

### 4.5. Bizim Değerlendirmemiz

Parnas, yazılım yaşlanmasının nedenlerini ve uzun vadeli bakım ihtiyacını açıklamaktadır.

Yanakiev ve arkadaşları ise uzun süredir geliştirilen bir sistemde birikmiş mimari sorunların belirli bir kısmını azaltmaya yönelik somut refactoring faaliyetlerini raporlamaktadır.

Bu nedenle Parnas (1994), seçtiğimiz makalenin problem bağlamını anlamak açısından önemli bir kaynaktır.

## 5. KAYNAK 4 — Abid ve Arkadaşları (2020)

### 5.1. Bibliyografik Bilgiler

**Yazarlar:** Chaima Abid, Vahid Alizadeh, Marouane Kessentini, Thiago do Nascimento Ferreira ve Danny Dig

**Yıl:** 2020

**Başlık:** 30 Years of Software Refactoring Research: A Systematic Literature Review

**Kaynak:** arXiv:2007.02194

**Bağlantı:** https://arxiv.org/abs/2007.02194

**DOI:** https://doi.org/10.48550/arXiv.2007.02194

**Yayın türü:** arXiv üzerinde erişilebilen sistematik literatür taraması sürümü

**Not:** Seçilen Yanakiev ve arkadaşları (2025) makalesi bu çalışmayı arXiv kaydıyla kaynaklandırmaktadır. ArXiv kaydı tek başına hakemli dergi yayını olduğunu göstermez.

### 5.2. Araştırmanın Amacı

Abid ve arkadaşları, yazılım refactoring alanında yaklaşık otuz yıllık dönemde gerçekleştirilen araştırmaları kapsamlı biçimde incelemeyi amaçlamıştır.

Bu doğrultuda farklı refactoring yaklaşımlarını, kullanılan araçları, çalışma alanlarını ve araştırma eğilimlerini değerlendirmiştir.

### 5.3. Araştırma Yöntemi

Çalışmada sistematik literatür taraması yöntemi kullanılmıştır.

Araştırmacılar 3.183 refactoring araştırmasını kapsayan bir inceleme gerçekleştirmiş ve çalışmaları farklı boyutlarda sınıflandırmaya yönelik bir taksonomi oluşturmuştur.

Sınıflandırma; refactoring yaşam döngüsü, otomasyon düzeyi, incelenen yazılım öğeleri, programlama paradigmaları ve değerlendirme yaklaşımları gibi konuları kapsamaktadır.

### 5.4. Temel Katkılar

Araştırmanın temel katkısı, yazılım refactoring alanındaki dağınık araştırmaları ortak bir sınıflandırma yaklaşımıyla incelemesidir.

Çalışma, refactoring faaliyetlerinin yalnızca kaynak kod düzeyinde değil; yazılım mimarisi, modeller ve farklı geliştirme ortamları kapsamında da ele alınabildiğini göstermektedir.

Ayrıca araştırma eğilimlerinin ve literatürdeki eksikliklerin belirlenmesine yönelik bir çerçeve sunmaktadır.

### 5.5. Yanakiev ve Arkadaşlarının Makalesiyle İlişkisi

Yanakiev ve arkadaşları (2025), makalelerinin 2.1. bölümünde Abid ve arkadaşlarının refactoring taksonomisinden yararlanmaktadır.

Bu taksonomi aracılığıyla kendi araştırmalarını şu özellikler çerçevesinde konumlandırmaktadır:

- Refactoring fırsatlarının tespiti ve önceliklendirilmesi.
- Otomatik tespit araçları ve yarı otomatik önceliklendirme desteğiyle gerçekleştirilen manuel refactoring.
- Mimari tasarım prensipleriyle yönlendirilen kaynak kod düzenlemeleri.
- Nesneye dayalı tasarım yaklaşımı.
- Legacy C++ kodunun iç kalitesinin iyileştirilmesi.
- Gerçek endüstriyel ortamda değerlendirme yapılması.

Böylece seçilen makalenin refactoring literatüründeki kapsamı ve yaklaşımı açıklığa kavuşturulmaktadır.

### 5.6. Bizim Değerlendirmemiz

Abid ve arkadaşlarının çalışması refactoring araştırmalarının geniş kapsamlı bilimsel haritasını ortaya koyarken Yanakiev ve arkadaşları bu alandaki belirli bir endüstriyel uygulamayı incelemektedir.

Bu ilişki sayesinde seçtiğimiz makalenin yalnızca kod düzenleme işlemlerinden değil, refactoring faaliyetlerinin önceliklendirilmesinden ve uygulanmasından da oluştuğu daha açık anlaşılmaktadır.

## 6. Dört Akademik Kaynağın Karşılaştırılması

| Çalışma | Yayın türü | Temel odak | Seçilen makaleye katkısı |
|---|---|---|---|
| Martin (2003) | Kitap | SOLID ve OOP tasarım prensipleri | DIP'nin teorik temeli |
| Lenarduzzi ve ark. (2021) | Sistematik literatür taraması | Teknik borcun önceliklendirilmesi | RQ1'in bilimsel altyapısı |
| Parnas (1994) | Konferans bildirisi | Yazılım yaşlanması | Legacy sistemlerde bakım probleminin temeli |
| Abid ve ark. (2020) | Sistematik literatür taraması, arXiv sürümü | Refactoring araştırmalarının sınıflandırılması | Refactoring yaklaşımının literatürde konumlandırılması |

Bu kaynaklar farklı araştırma sorularına odaklanmakla birlikte, Yanakiev ve arkadaşlarının (2025) çalışmasının temelini farklı açılardan desteklemektedir.

Martin yazılımın nasıl tasarlanması gerektiğine, Parnas yazılımların zaman içerisinde neden bakım sorunları yaşayabildiğine, Lenarduzzi ve arkadaşları hangi teknik borç sorunlarının öncelikle ele alınması gerektiğine, Abid ve arkadaşları ise refactoring çalışmalarının bilimsel literatürde nasıl sınıflandırıldığına odaklanmaktadır.

Yanakiev ve arkadaşlarının çalışması bu bilgi birikiminden yararlanarak mevcut bir endüstriyel yazılım sisteminde belirli mimari bağımlılıkların giderilmesine yönelik uygulamaları incelemektedir.

## 7. RQ1 ve RQ2 ile Bağlantı

### 7.1. RQ1 — Veri Odaklı Önceliklendirme

Lenarduzzi ve arkadaşlarının çalışması, teknik borcun önceliklendirilmesinde kullanılabilecek stratejilere ve ölçütlere ilişkin bilimsel arka plan sağlamaktadır.

Parnas'ın çalışması ise uzun ömürlü yazılım sistemlerinde bakım ihtiyacının neden ortaya çıktığını anlamaya yardımcı olmaktadır.

Bu çalışmalar, ASML'nin mimari teknik borcunu azaltmak amacıyla önceliklendirme yapılmasının gerekçesini güçlendirmektedir.

### 7.2. RQ2 — SOLID Prensiplerinin Refactoring Kalıplarına Dönüştürülmesi

Martin'in çalışması, DIP gibi nesneye dayalı tasarım prensiplerinin teorik temelini oluşturmaktadır.

Abid ve arkadaşlarının çalışması, refactoring faaliyetlerinin farklı türlerde gerçekleştirilebildiğini ve sistematik biçimde sınıflandırılabildiğini göstermektedir.

Bu iki kaynak, Yanakiev ve arkadaşlarının DIP prensibinden hareketle yedi refactoring kalıbı oluşturmasını bilimsel bağlamda anlamaya yardımcı olmaktadır.

## 8. Genel Akademik Değerlendirmemiz

Literatür incelemesi sonucunda seçtiğimiz makalenin farklı araştırma alanlarını bir araya getirdiği görülmektedir.

Çalışma, nesneye dayalı tasarım prensiplerini, teknik borç yönetimini, yazılım yaşlanmasını ve refactoring literatürünü ortak bir endüstriyel problem etrafında ilişkilendirmektedir.

Bu açıdan makalenin katkısı, SOLID prensiplerini yeniden tanımlamak veya teknik borç kavramını ilk kez ortaya koymak değildir.

Asıl katkısı, mevcut bilimsel yaklaşımları belirli bir endüstriyel C++ sistemine uyarlayarak mimari bağımlılık sorunlarına yönelik uygulanabilir ve tekrarlanabilir refactoring kalıpları geliştirmesidir.

Bununla birlikte seçilen kaynakların yöntemleri farklıdır. Bir tasarım kitabından, bir konferans bildirisinden ve sistematik literatür taramalarından elde edilen kanıt türleri aynı değildir.

Bu nedenle akademik raporda her kaynağın katkısını kendi yayın türü ve araştırma kapsamı içerisinde değerlendirmek gerekmektedir.

## 9. Kaynakça

Abid, C., Alizadeh, V., Kessentini, M., do Nascimento Ferreira, T., & Dig, D. (2020). *30 Years of Software Refactoring Research: A Systematic Literature Review*. arXiv:2007.02194. https://doi.org/10.48550/arXiv.2007.02194

Lenarduzzi, V., Besker, T., Taibi, D., Martini, A., & Fontana, F. A. (2021). A systematic literature review on Technical Debt prioritization: Strategies, processes, factors, and tools. *Journal of Systems and Software, 171*, 110827. https://doi.org/10.1016/j.jss.2020.110827

Martin, R. C. (2003). *Agile Software Development: Principles, Patterns, and Practices*. Prentice Hall.

Parnas, D. L. (1994). Software aging. In *Proceedings of the 16th International Conference on Software Engineering* (pp. 279–287). IEEE. https://doi.org/10.1109/ICSE.1994.296790

Yanakiev, I., Lazar, B.-M., & Capiluppi, A. (2025). Applying SOLID principles for the refactoring of legacy code: An experience report. *Journal of Systems and Software, 220*, 112254. https://doi.org/10.1016/j.jss.2024.112254