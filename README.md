# Yazilim-Mimarisi-ve-Tasarimi
## Kurucu (Builder) Tasarım Deseni  
Kurucu (builder) tasarım deseni creational grubununa ait, birden fazla parçadan oluşan nesnelerin üretilmesinden sorumlu bir tasarım desenidir.Bazı nesneler birden fazla nesnenin birleşmesinden(bazı işlemleri yapması sonucu) oluşabilir. Zamanla bu ana nesneyi oluşturan nesnelerin yapısı değişebilir, bu nesnelerin oluşturulması karışık bir hal alabilir veya bu nesnelere başka nesneler de eklenebilir. Builder tasarım deseni bu gibi durumlarda genişletilebilirliği sağlamak ve kod karmaşıklığını engellemek için kullanılır. Builder tasarım deseninde bu nesnelerin oluşturulması Builder denilen sınıfların sorumluluğundadır.  Abstract factory tasarım kalıbı ile benzer bir yapısı vardır. Aralarındaki fark builder tasarım deseni birden fazla nesnenin birleşmesinden oluşan nesnelerin üretilmesinden sorumludur.
Ana avantajları şunlardır:
o	Bir nesnenin yapımı ve temsili arasında net bir ayrım sağlar.
o	Kurucu süreci üzerinde daha iyi kontrol sağlar.
o	Bu nesnelerin iç temsilini değiştirmeyi için destekler.  
