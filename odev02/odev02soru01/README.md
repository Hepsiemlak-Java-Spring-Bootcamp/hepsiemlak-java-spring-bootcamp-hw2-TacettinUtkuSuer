## JAVA Dünyasındaki Frameworkler



Bu yazımızda JAVA dünyasında kullanılan frameworklerden bahsedeceğiz. Herkesin bildiği ve çok yaygın olarak kullanılan Spring Framework'unden değil diğer frameworkler, yaptıkları işler ve hangi alanlarının güçlü olduğu üzerinde duracağımız. 



Peki öncelikle neden framework kullanıyoruz, Java bize neden yetmiyor da böyle bir arayış içine girilmiş. Frameworkler aslında projelerinizi oluştururken size yardımcı olan kodlardır. Daha önceden oluşturulmuş ve test edilmiş bir yapı sağlar ve bu yapı sayesinde bizler çok daha hızlı, temiz ve güvenli kodlar yazmaya yönlendirir. 



Bu yazımızda HIBERNATE, JSF ve STRUTS'dan bahsedeceğiz.



- ### HIBERNATE



Bir ORM kütüphanesidir, yani veritabanları ile modellerimiz arasındaki ilişkileri çok iyi sağlamaktadır. Nesne yönelimli programlama ve ilişkisel veritabanı kullanımı günümüzde olmazsa olmazdır. Hibernate sayesinde Java sınıflarından veritabanlarına tabloların dönüşümü  yada tam tersi kolaylıkla yapılabiliyor. Ek olarak veri sorgulama ve veri çekme işlemlerini de sağlar. Çok karmaşık SQL veritabanları ile uğraşmayı kolaylaştırdığı gibi nerdeyse tüm veritabanlarını da desteklemektedir. 



```java
private static SessionFactory factory = new Configuration().configure().buildSessionFactory();

Session session = factory.openSession;
```



Yukarıda görülen iki sınıf, HIBERNATE'in en önemli iki sınıfıdır. Bu iki sınıftan da nesne üretmek pahalı olduğu için olabildiğince az yani dikkatli kullanılmalıdır. 



- ### JSF "Java Server Faces"



Web sayfalarında dinamik web sayfaları oluşturmak için kullanılır. Bir farklı deyişle kullanıcı arayüzlerini sunucu tarafında sağlayan frameworktür. Spring gibi MVC yapısına uygun olarak geliştirilmiştir. Veriler üzerinde doğrulama gibi işlemler çok kolay yapılır. Farklı dil desteği mevcuttur.  Kendi içerisinde kullanışlı UI komponentları vardır. Kullanıcı sayısı az uygulamalarda çok fazla kolaylık sağlasa da kullanıcı sayısı arttıkça sunucuyu yormaya başlamaktadır.



```java
<%..............%>
```



Managed Bean ile oluşturulmuş sınıflar JSF özel tagları ile kullanılarak HTML dili içerisinde kullanılır. 



- ### STRUTS 



Web teknolojileri gerçekleştirmekte kullanılan bir frameworktür. MVS yapısında çalışmaktadır hatta bu tasarım örüntüsünün atasıdır. Java Server Pages (JSP) ile uyumlu bir şekilde çalışmaktadır, hatta buradaki kodları en aza indirmektedir. Form kontrolleri frameworkte tanımlı olarak gelmektedir. Bu kontroller sunucu ve istemci tarafında da tercihe bağlı olarak kullanılabilrmektedir. Bir XML dosyası üzerinden olay akışı sağlanabilmektedir.  Aşağıda örnek bir Struts-specific configuration files kodu yer almaktadır.



```
<servlet>
    <servlet-name>action</servlet-name>
    <servlet-class>org.apache.struts.action.ActionServlet</servlet-class>
    <init-param>
        <param-name>config</param-name>
        <param-value>/WEB-INF/struts-config.xml</param-value>
    </init-param>
    <init-param>
        <param-name>debug</param-name>
        <param-value>2</param-value>
    </init-param>
    <init-param>
       <param-name>detail</param-name>
       <param-value>2</param-value>
    </init-param>
    <load-on-startup>2</load-on-startup>
</servlet>
<servlet-mapping>
    <servlet-name>action</servlet-name>
    <url-pattern>*.do</url-pattern>
</servlet-mapping> 

[*] Alıntılanan Web Sitesi: netbeans.apache.org
```


## [Geri](https://github.com/Hepsiemlak-Java-Spring-Bootcamp/hepsiemlak-java-spring-bootcamp-hw2-TacettinUtkuSuer/tree/main/odev02)
