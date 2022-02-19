## Creational Tasarım Kalıpları



Projemizde duruma uygun şekilde nesne yaratmaya yarayan tasarım kalıplarıdır. Bu tasarım kalıplarının asıl amacı nesnenin nasıl yaratıldığını, düzenlendiğini ve gösterildiğini ayırmaya yarar. Bu amaçla 5 iyi bilinen temel tasarım kalıbı vardır. Bunlar; Abstact Factory, Builder, Factory, Prototype ve Singeleton Tasarım Kalıplarıdır.



1. ### Abstract Factory Pattern



Birden fazla ürün ailesi ile çalışmamız gerektiği zaman ortaya çıkan bir tasarım kalıbıdır. İlişkisel olan birden fazla nesnenin üretimini ortak bir interface ile tek bir sınıftan oluşturmak için kullanılır. Nesne üretim anında istemcinin üretilen nesneye olan bağımlılığını en aza indirmeye çalışır.



Daha iyi anlamak adına örnek vermek gerekirse bir tane super sınıfımız olsun Shape diye ve iki tane alt sınıfı olsun bu sınıftan extend edilen; Circle ve Rectangle. Bu zaten şimdiye kadar inheritance'da en çok duyduğumuz örnek. Peki Abstract Factory nerde devreye giriyor derseniz hemen oraya geliyorum. Şimdi başka bir sınıfımız olsun ve türü interface ve ismi AbstractShapeFactory olsun ve altında da CircleFactory ve RectangleFactory isminde iki sınıfımız var. Bu iki sınıfın altında birer metodu olsun ve bu metodun amacı da kendi türülerin de yani Circle veya Rectangle türünde nesneleri oluşturmak olarak düşünelim, bu metotları da CircleFactory ve RectangleFactory olarak isimlendirelim. Böylece iki hiyerarşi ağacımız oldu, son olarak nesnelerimizi oluşturmaya yarayan statik metoda sahip son bir sınıfımız olsun, nesne oluştururken bu sınıfın metodunu çağıracağız. Bu sınıfta ShapeFactory olarak isimlendirelim. Herhangi bir sınıfın içinden Circle nesnesi oluşturmak istediğimde Shape circleObject = ShapeFactory.getShape(new CircleFactory()); diye yazarak Circle nesnemizi oluşturabilceğiz. Peki bu kadar niye uzattık direk nesne çağıramaz mıydık? Hem evet hem hayır. Evet nesne zaten böyle çağırabiliyoruz ama ilerde değişikler yapmak, farklı alanlara geçmek istediğimizde klasik nesne yaratma bize bu esnekliği veremeyecekti. Yazının sonunda kod örneği göstereceğim.



![abstractFactoryUML](https://github.com/Hepsiemlak-Java-Spring-Bootcamp/hepsiemlak-java-spring-bootcamp-hw2-TacettinUtkuSuer/blob/main/odev02/odev02soru03/sekiller/abstractFactoryUML.png)

[1] Web Sitesi: https://www.codesenior.com/



2. ### Builder Pattern



Çok fazla parametre alan obje varsa, farklı kombinasyonlarda çok fazla consructor oluşturmanız gerekiyorsa ve yine oluşum sırasında bir sürü null ataması yapmak zorunda kalıyorsanız builder pattern bu sorunlara çözüm getirerek kodunuz temiz ve kullanışlı bir hale getiriyor. 



```java
public class Hamburger {

	private final int kofteGramaji;
	private final String isim;
	private boolean peynir;
	private boolean sogan;
	private boolean domates;

	private Hamburger(HamburgerBuilder hamburgerBuilder) {
		this.kofteGramaji = pizzaBuilder.kofteGramaji;
		this.isim = pizzaBuilder.isim;
		this.peynir = pizzaBuilder.peynir;
		this.sogan = pizzaBuilder.sogan;
		this.domates = pizzaBuilder.domates;
	}
public static class HamburgerBuilder {

		private final int kofteGramaji;
		private final String isim;
		private boolean peynir;
		private boolean sogan;
		private boolean domates;

		public HamburgerBuilder(int kofteGramaji, String isim) {
			this.kofteGramaji = kofteGramaji;
			this.isim = isim;
		}

		public HamburgerBuilder ekPeynir(boolean peynir) {
			this.peynir = peynir;
			return this;
		}

		public HamburgerBuilder ekSogan(boolean sogan) {
			this.sogan = sogan;
			return this;
		}

		public HamburgerBuilder ekDomates(boolean domates) {
			this.domates = domates;
			return this;
		}

		public Hamburger buildHamburger() {
			return new Hamburger(this);
		}
	}


}
```



Yukarıda görüldüğü gibi constructor karmaşıklığından ve kodun okunabilirliğini etkileyen sorunlardan kurtulmuş olduk. Son olarak bu sınıftan nesne üretmeye bakalım.



```java
		HamburgerBuilder hamburgerBuilder = new Hamburger.HamburgerBuilder(175, "Texas");
		hamburgerBuilder.ekSogan(true);
		hamburgerBuilder.ekPeynir(true);
```



3. ### Factory Method Pattern



Aslında yukarıda bahsettiğimiz Abstract Factory Pattern'ının temel taşı denilebilir. Nesne yaratma görevini klasik yöntemden ziyade soyutlama yaparak başka bir soyut sınıftan yaparak oluşturmaya yarar. Peki bu bize ne avantaj sağlar, niye bunu yapıyoruz diye sorarsanız? Projemize yeni bir özellik eklerken en az dokunuş ile istemci kodumuzu hiç değiştirmeden bu eklemeyi yapmak amacı ile gerçekleştiriyoruz. Yukarıda da belirttiğim gibi yazının sonunda kod örneği vereceğim.



4. ### Prototype Pattern



Her yeniden üretilen yeni nesne ile çok fazla kaynak kullanımının önüne geçebilmemizi sağlamaktadır. Nesne bir kez oluşturulduğunda bu nesne klonlanarak yeni nesneler yaratma tasarım kalıbıdır. Böylece her seferinde new kullanmamış olacağız. Daha açıklayıcı olması adına aşağıda kod örneği yer almaktadır.



```java
public class manavAlisverisSepeti implements Cloneable {
    // Cloneable, kodumuzun klonlanibilmesi için implement ediliyor.
    
    private List<String> alisverisListesi;
    
    public manavAlisverisSepeti(){
        manavListesi = new ArrayList<String>();
    }
    
    public manavAlisverisSepeti(List<String> manavListesi) {
        this.manavListesi = manavListesi;
    }

    public void meyveSebzeEkle() {
        manavListesi.add("Elme");
        manavListesi.add("Armut");
        manavListesi.add("Marul");
        manavListesi.add("Domates");
    }

    public List<String> getManavListesi() {
        return manavListesi;
    }

    // Cloneable interface'i içerisindeki clone metodu override ediliyor.
    @Override
    public Object clone() throws CloneNotSupportedException {
        List<String> manavListesi = new ArrayList<String>();
        for (String s : this.getManavListesi()) {
            manavListesi.add(s);
        }
        return new manavAlisverisSepeti(manavListesi);
    }
    
}
```



Şimdi de nesnemizi oluşturalım ve klonlayalım.



```java
        manavAlisverisSepeti manavListesiNesnesi = new manavAlisverisSepeti();
        uyeler.meyveSebzeEkle();

        manavAlisverisSepeti manavListesiNesnesi2 = (manavAlisverisSepeti) manavListesiNesnesi.clone();

        List<String> yeniManavListesi = manavListesiNesnesi2.getManavListesi();
        yeniManavListesi.add("Karpuz");

```



Klonlama ile az kaynak tüketerek yeni nesnelerimizi oluşturmuş olduk.



5. ### Singleton Pattern



Singleton Tasarım Kalıbı projemizin çalışması sırasında benzersiz sadece bir tane nesne oluşturulmasını sağlar. Aynı nesneden tekrar üretmeye çalışsak da program bize yine aynı nesneyi döndürecektir. Bunu kullanmamızın nedeni uygulamada sadece bu nesneden bir tane olması gerektiği durumlar, farkında olmadan yeniden nesne üretmeye çalışsak da bu nesneden sadece bir tane olduğuna emin olmamız gerektiği ve/veya bir çok sınıfın bu aynı instance'ı kullanması gerektiği durumlardır. Örnek olması adına instancelarımız databasedeki fiziksel bilgilerin ram belleğe taşınmış yani ram bellek içerisinde yer alan verilerimiz olabilir, bu durumda program içerisinde bu nesneye her ulaşmak ve yaratmak isteyen için aynı verinin döndüğünden emin olmak gerekmektedir. Singleton'da bu tür problemlere çözüm yaratmaktadır. 



```java
public class Singleton {

    private static Singleton singleton = null;

    public static Singleton olustur(){
        if (singleton==null){
            singleton =  new Singleton();
        }
        return singleton;
    }

}
```



Yukarıda görüldüğü gibi bir sınıf oluşturalım. Görüldüğü üzere nesne oluşturmayı oluştur metoduna aktardık ve bu metot bu nesnene yoksa oluşturup döndürüyor varsa da var olan nesneyi döndürüyor böylece hep aynı nesneyi kullanmış oluyoruz. 



```java
public class Main {

    public static void main(String[] args) {

        Singleton sing  = Singleton.olustur();
        System.out.println(sing );

        Singleton sing2 = Singleton.olustur();
        System.out.println(sing2);

        Singleton sing3 = Singleton.olustur();
        System.out.println(sing3);

        
    }
}
```



Yukarıdaki kod bloğunu çalıştırdığımız da ise aşağıdaki gibi bir çıktı alıyoruz. Görüldüğü üzere bütün nesnelerin idleri aynı yani nesneler aynı.



![singleton](https://github.com/Hepsiemlak-Java-Spring-Bootcamp/hepsiemlak-java-spring-bootcamp-hw2-TacettinUtkuSuer/blob/main/odev02/odev02soru03/sekiller/singleton.png)





- ### Factory ve Abstract Factory Örneği



Daha önce yazmış olduğumuz HepsiEmlak uygulamasına Factory ve Abstract Factory tasarım kalıplarını ekleyerek, örnek gösterilecektir. Üst sınıf bir interface sınıfıdır ve böylece soyutlama yapılmıştır.



```java
public interface IKullaniciAbstractFactory {
    
	public IKullanici createKullanici;
    
}
```



Bireysel ve kurumsal kullanıcıların nesnelerinin oluşturulabilmesi için aşağıdaki sınıflar oluşturulmuştur ve IKullaniciAbstractFactory interface sınıfından implement edilmiştir.



```java
public class BireyselKullaniciFactory implements ShapeAbstractFactory {
    @Override
    public IKullanici createKullanici() {
        return new BireyselKullanici();
    }
}
```



```java
public class KurumsalKullaniciFactory implements ShapeAbstractFactory {
    @Override
    public IKullanici createKullanici() {
        return new KurumsalKullanici();
    }
}
```



Farklı kullanıcı tipleri için nesnelerin oluşturulmasında tek bir sınıftan işlem yapılmaktadır. İstemci tarafı kod sadece KullaniciFactory üzerinden nesne oluşturmaktadır. Böylece ileride farklı tipler sisteme dahil olması gerektiğinde sadece yukarıdaki gibi bir kod eklenmesi yeterli olacaktır.



```java
public class KullaniciFactory {
    public static IKullanici getKullanici(IKullaniciAbstractFactory factory){
        return factory.createKullanici();
    }
}
```



Aşağıdaki nesnelerin main sınıfı içerisindeki oluşturulmaları görülmektedir.



```java
public class Main {
    public static void main(String[] args) {
        
        IKullanici bireyselKullanicilar = KullaniciFactory.getKullanici(new BireyselKullaniciFactory());
     
        IKullanici kurumsalKullanicilar = KullaniciFactory.getKullanici(new KurumsalKullaniciFactory());

    }
}
```

## [Geri](https://github.com/Hepsiemlak-Java-Spring-Bootcamp/hepsiemlak-java-spring-bootcamp-hw2-TacettinUtkuSuer/tree/main/odev02)

