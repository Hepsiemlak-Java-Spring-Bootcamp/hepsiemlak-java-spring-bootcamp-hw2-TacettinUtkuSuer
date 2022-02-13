## Spring Framework'ün de En Çok Kullanılan Tasarım Kalıpları



### 1. MVC 



Yazılım dünyasında çok önemli bir yere sahip olan ve çok kullanılan bir tasarım kalıbıdır. Model - View - Controller kelimlerinin baş harflerinden türetilmiştir. Oluşturulmuş olan isimlerden de anlaşılabileceği gibi katmanlı bir mimaridir. Her bir katman bağımsız olarak çalışabilmektedir.  Peki bu kelimeler ne demek? Gelin bunlara birlikte bakalım;




  - MODEL

Model MVC projesinin business logic'iğini oluşturmaktadır.  Kendi içerisinde alt katmanlara da ayrılabilmektedir. Veritabanı kullanımı yani veri erişimi, modifikasyonlar ve doğrulama gibi işlemler bu katmanda yürütülür. 

  - VIEW

Verilerin yorumlanması yani arayüzlerin oluşturulduğu katmanıdır. HTML, CSS, JS gibi kullanıcı arayüzleri bu bölümde yer almaktadır. View katmanı kullanıcı isteklerini Controller'a iletir, aynı şekilde Model'den alması gereken verileri yine Controller'dan talep eder. 

  - CONTROLLER

Controller, view ile model arasındaki köprüdür. View'un isteklerini değerlendirir ve hangi işlemlerin yapılacağını ve view'a hangi bilgilerin gönderileceğini yönetir.



### 2. Proxy Tasarım Kalıbı



Var olan bir nesne ile istemci arasında bir katman oluşturarak. Nesnenin kontrollü olarak kullanımını sağlar. Böylece istemci taraf doğrudan nesneye ulaşamamış olur. Bu hem güvenlik açısından hem de nesneye erişim öncesi kontrol imkanı sağlar. Nesne yaratılması uzun zaman alan durumlarda da kullanılır ve ilk oluşturma süresi uzun olsa da sonraki kullanımlarda erişim süresi kısalır.



### 3. Factory Tasarım Kalıbı



Factory Tasarım Kalıbı projelerimizde ki new bağımlılığını ortadan kaldırmaya yaramaktadır. Bu da hem nesnelerimizi yani Bean'lerimizi oluşturma kontrolünü Springe vermiş oluruz hem de ileride projemizin farklı bir amaçla kullanılması istediğinde böyle bir değişikliği yapmamıza olanak sağlamaktadır. 



### 4. Singleton Tasarım Kalıbı



Bu tasarım kalıbı projemizin çalıştığı anda bir sınıftan sadece bir tane nesne oluşturulmasını sağlar ve bunu garanti eder. Birden çok sınıf aynı instance'ı kullanmış olur. 



### 5. Template Method Tasarım Kalıbı 



Şablon ve soyut bir super sınıf tanımlanarak algoritma işlemlerinin iskeleti hazırlanır. Alt sınıflarda farklı ihtiyaçlar ve özelleşmeler varsa bu alt sınıflarda tanımlanır. Bu kalıp sayesinde kod tekrarlarından kaçınılmış olunur. 



### 6.  FrontController Tasarım Kalıbı



İstekleri yönetmek için kullanılır ve merkezi bir denetleyici modelidir. Her istemci isteği önce ön denetimlerden geçmelidir ve işlenmelidir. Spring'de bu işlemleri DispatcherServlet kullanılarak uygulanır.



### 7. Prototype Tasarım Kalıbı



Üretilen nesnenin çok fazla kaynak harcamasını engellemek amacı ile nesnemizi bir kez oluşturup onun klonlarını oluşturarak yeni nesneler yapmamızı sağlayan bir tasarım kalıbıdır.



### 8. DI / IoC Tasarım Kalıbı



DI, Dependency Injection'ın kısaltmasıdır ve IoC "Inversion of Control" yani uygulamanın yaşam döngüsü boyunca nesnelerin birbirlerine bağımlılığını azaltmayı amaçlayan bir tasarım kalıbıdır. Herhangi bir oluşturulacak nesnenin sınıfı bir interface inject edildiyse, bu interface içerisinde ki metotları kullanacağı için nesneyi oluşturan kişi sacece bu metot isimlerini bilerek erişir ve kullanır. Böylece sınıf içerisindeki kullanım algoritmaları değişse bile isim ve amacı aynı kalacağından, nesneyi kullanan sınıf bu bağımlılıktan kurtulmuş olur.





