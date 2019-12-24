# Yazilim-Mimarisi-ve-Tasarimi
## Kurucu (Builder) Tasarım Deseni  
Kurucu (builder) tasarım deseni creational grubununa ait, birden fazla parçadan oluşan nesnelerin üretilmesinden sorumlu bir tasarım desenidir.Bazı nesneler birden fazla nesnenin birleşmesinden(bazı işlemleri yapması sonucu) oluşabilir. Zamanla bu ana nesneyi oluşturan nesnelerin yapısı değişebilir, bu nesnelerin oluşturulması karışık bir hal alabilir veya bu nesnelere başka nesneler de eklenebilir. Builder tasarım deseni bu gibi durumlarda genişletilebilirliği sağlamak ve kod karmaşıklığını engellemek için kullanılır. Builder tasarım deseninde bu nesnelerin oluşturulması Builder denilen sınıfların sorumluluğundadır.  Abstract factory tasarım kalıbı ile benzer bir yapısı vardır. Aralarındaki fark builder tasarım deseni birden fazla nesnenin birleşmesinden oluşan nesnelerin üretilmesinden sorumludur.
Ana avantajları şunlardır:
o	Bir nesnenin yapımı ve temsili arasında net bir ayrım sağlar.
o	Kurucu süreci üzerinde daha iyi kontrol sağlar.
o	Bu nesnelerin iç temsilini değiştirmeyi için destekler.  


![Image of Class](https://github.com/FRTekneci/Yazilim-Mimarisi-ve-Tasarimi/blob/master/builderuml1.jpg)
Ambalaj.java
```java

genel  arayüz Paketleme {
            genel dize paketi();
            kamu  int fiyat();
}  



```
cd.java
```java
genel  soyut  sınıf CD paketleme uygular{
genel  soyut dize paketi();
}  	
```

Şirket.java
```java
    genel  soyut  sınıf şirket CD uzanır{
    genel  Özet  int fiyatı();
}  
````
Ambalaj adında bir arayüz  ve cd ile şirket olmak üzere 2 adet  soyut sınıf oluşturuldu.
Sony.java
```java
public class Sony extends Company{  
    @Override  
        public int price(){   
                        return 20;  
      }  
    @Override  
    public String pack(){  
             return "Sony CD";  
        }         
}//End of the Sony class.  
```



Samsung.java
```java
     public class Samsung extends Company {  
    @Override  
        public int price(){   
                        return 15;  
    }  
    @Override  
    public String pack(){  
             return "Samsung CD";  
        }         
}//End of the Samsung class.  

```
Sony ve Samsung olmak üzere iki adet uygulama sınıfı oluşturuldu.  

CDType.java
```java
import java.util.ArrayList;  
import java.util.List;  
public class CDType {  
             private List<Packing> items=new ArrayList<Packing>();  
             public void addItem(Packing packs) {    
                    items.add(packs);  
             }  
             public void getCost(){  
              for (Packing packs : items) {  
                        packs.price();  
              }   
             }  
             public void showItems(){  
              for (Packing packing : items){  
             System.out.print("CD name : "+packing.pack());  
             System.out.println(", Price : "+packing.price());  
          }       
            }     
}//End of the CDType class.

```
CDBuilder.java
```java
public class CDBuilder {  
                  public CDType buildSonyCD(){   
                     CDType cds=new CDType();  
                     cds.addItem(new Sony());  
                     return cds;  
              }  
              public CDType buildSamsungCD(){  
             CDType cds=new CDType();  
             cds.addItem(new Samsung());  
             return cds;  
              }  
}// End of the CDBuilder class.  

```
CDType ve CDBuilder olarak iki adet sınıf oluşturuldu.  
BuilderDemo.java:
```java
  
public class BuilderDemo{  
 public static void main(String args[]){  
   CDBuilder cdBuilder=new CDBuilder();  
   CDType cdType1=cdBuilder.buildSonyCD();  
   cdType1.showItems();  
  
   CDType cdType2=cdBuilder.buildSamsungCD();  
   cdType2.showItems();  
 }  
}
...
BuilderDemo adında sınıf oluşturuldu.
##Komut (Command) Tasarım Deseni  

Davranışsal (Behavioral) tasarım kalıplarından biri olan komut tasarım kalıbı, nesneye dayalı programlama (Object Oriented Programing) çalışmalarında çoğu zaman farkında olmadan kullanılan bir yapıdır. Komut tasarım kalıbı, kullanıcı isteklerini gerçekleştiren kod yapısının sarmalanarak nesneler halinde saklanmasına dayanır. Öyle ki üzerinde çalışılacak nesnenin tanımının yapılamadığı durumlar olabilir. Bu şartlarda ne tür çözüm yolları ile nesneye müdahale edilmeye çalışılabileceği kestirilemez, ancak gerçekleştirilmek istenen işlemler bir nesne olarak sarmalanır. Nesne halinde tutulan bu sarmal kod yapısı, alıcı nesne için bir çözüm oluşturur. Çözümlerin nesneler halinde saklanmasının getirisi olarak da komut tasarım kalıbı aynı kod yapısının tekrar tekrar kullanılabilmesine olanak sağlar.  
![Image of Class](https://github.com/FRTekneci/Yazilim-Mimarisi-ve-Tasarimi/blob/master/commanduml.jpg)  


````java
public interface ActionListenerCommand {  
    public void execute();  
}  
```
Komut görevi görecek ActionListernerCommand arabirimi oluşturuldu.  
Document.java:
```java
public class Document {  
          public void open(){  
           System.out.println("Document Opened");  
       }  
       public void save(){  
           System.out.println("Document Saved");  
       }  
} 

```
Alıcı görevi görecek bir belge sınıfı oluşturuldu.

ActionOpen.java:
```java

public class ActionOpen implements ActionListenerCommand{  
    private Document doc;  
    public ActionOpen(Document doc) {  
        this.doc = doc;  
    }  
    @Override  
    public void execute() {  
        doc.open();  
    }  
} 

```
ConcreteCommand işlevi görecek bir ActionOpen sınıfı oluşturuldu.  
AdapterPatternDemo.java
```java
public class ActionSave implements ActionListenerCommand{  
   private Document doc;  
   public ActionSave(Document doc) {  
        this.doc = doc;  
    }  
    @Override  
    public void execute() {  
        doc.save();  
    }  
}

``` 
ConcreteCommand işlevi görecek bir ActionSave sınıfı oluşturun.
 ActionSave.java:
 ```java

public class ActionSave implements ActionListenerCommand{  
   private Document doc;  
    public ActionSave(Document doc) {  
        this.doc = doc;  
    }  
    @Override  
    public void execute() {  
        doc.save();  
    }  
}  

```
Invoker işlevi görecek bir MenuOptıons sınıfı oluşturuldu.
AdapterPatternDemo.java:
```java

public class CommandPatternClient {  
    public static void main(String[] args) {  
        Document doc = new Document();  
          
        ActionListenerCommand clickOpen = new ActionOpen(doc);  
        ActionListenerCommand clickSave = new ActionSave(doc);  
          
        MenuOptions menu = new MenuOptions(clickOpen, clickSave);  
          
        menu.clickOpen();  
        menu.clickSave();  
   }  
}
```
İstemci işlevi görecek bir CommanClient sınıfı oluşturuldu.


