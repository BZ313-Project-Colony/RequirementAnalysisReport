# Gereksinim Analizi Raporu
## Proje adı: QR Pass

## Amaç
QR Pass, davet ve etkinlik düzenlemelerinde QR teknolojisini kullanarak, davet oluşturup katılımcılarla organizasyon arasındaki iletişimi sağlayabilmeyi, böylece elle veri girişinin azaltılarak hata olasılığının azaltmayı amaçlıyor.

## Hedefler
- Etkinliklerin daha düzenli ve hızlı bir şekilde yönetilmesi.
- Davet katılım takibini sağlamak
- Etkinliğe kayıt olma işlemini kolaylaştırmak
- QR teknolojisi ile etkinlik girişlerini kolaylaştırmak.
- Etkinlik bilgilerini düzenli bir şekilde yönetmek

## Projeye Genel Bakış
QR Pass üniversite kulüp etkinlik yönetimini iyileştirmek için geliştirilen bir uygulamadır.
Ürün, iki tip kullanıcıya hitap etmektedir. Yönetici etkinlik ve etkinlik daveti oluşturma, davetlileri düzenleyebilme, davetli sayısının ve girişinin takibini sağlayabilme eylemlerini yapabilirken; kullanıcı oluşturulan etkinliğe kayıt gerçekleştirilmelidir.

## Tanımlar ve Kısaltmalar
QR: Quick Response
PaaS: Platform as a Service

## Kullanılacak Teknolojiler ve Hedefler
- PaaS - Heroku: Java Spring Boot ile oluşturduğumuz QR Pass web servisi popüler, kullanışlı ve ucuz bir PaaS platformu olan Heroku üzerinde çalıştıracağız.
- Veritabanı: Postgres: Etkinlik ve bilet bilgilerini depolamak için açık kaynak ve Java ile uyumlu olan Postgres veritabanını kullanacağız.
- Mail Sender Library : Spring Boot Starter Email : Kullanıcıların maillerine kayıt oldukları etkinliklere dair etkinlik bilgilerini ve QR kodlarını içeren bilet içeriğini güvenli bir şekilde mail yoluyla gönderebilmek için bu kütüphaneyi kullanacağız.
- Hosting : Firebase Hosting: QR Pass admin paneli ve etkinlik kayıt formu olarak geliştireceğimiz iki ayrı frontend web projesini Firebase Hosting aracılığıyla host edeceğiz.
- Flutter QR Scanner Library: Katılımcıların maillerine gelen QR kodlarını okuyup bilet durumlarını değiştirebilmek amacıyla oluşturacağımız mobil uygulamamızda development süresini kısaltmak adına hazır QR Scanner kütüphanesi kullanacağız.

# Gereksinimler

## Fonksiyonel Gereksinimler
Fonksiyonel gereksinimler, bir yazılım sisteminin gerçekleştirmesi gereken işlevleri tanımlayan özelliklerdir. Bu gereksinimler, sistemin ne yapması gerektiğini ve nasıl davranması gerektiğini belirler. Fonksiyonel gereksinimleri yazılım sisteminin geliştirilmesine başlamadan önce dikkatle tanımlamak önemlidir, çünkü bunlar sistemin tasarımını ve uygulamasının temelini oluşturur. Bu projenin fonksiyonel gereksinimleri aşağıdaki kategorilerde belirlenmiş ve açıklanmıştır.

### Web Arayüzü-Yönetici Tarafı:
#### Etkinlik Oluşturma :
- Kullanıcı adı ve şifre ile giriş yapılarak etkinlik oluşturulabilmelidir.
- Etkinlik bilgileri arasında etkinlik adı, tarih, saat, mekan ve maksimum katılımcı sayısı bulunmalıdır.
#### Etkinlik Listeleme
- Yönetici, oluşturduğu etkinlikleri listeleyebilmelidir.
- Her etkinlik için katılımcı sayısı ve kayıt linki görüntülenebilmelidir.
#### Etkinlik Katılımcı Listesi
- Yönetici, her etkinliğe kaydolan katılımcıları ve bilgilerini listeleyebilmelidir.
- QR okutma durumlarını (okuttu, onaylandı / okutmadı / okuttu, onaylanmadı) görebilmelidir.
#### Etkinlik Kayıt Linki Oluşturma :
- Yönetici, her etkinliğe özel bir kayıt linki oluşturarak katılımcılara paylaşabilmelidir.
- Dilerse etkinlik dolmadan kayıtları kapatabilmelidir.
#### Etkinlik Silme
- Yönetici, oluşturduğu etkinlikleri silebilmelidir.
#### Etkinlik Detayları Güncelleme
- Yönetici, oluşturduğu etkinliklerin detaylarını daha sonra güncelleyebilmelidir.

### Web Arayüzü-Katılımcı Tarafı:
#### Etkinlik Bilgilerini Görüntüleme
- Katılımcı, etkinliğe özel URL üzerinden etkinlik bilgilerini görüntüleyebilmelidir.
- Katılımcı, ad, soyad, e-posta bilgilerini girerek etkinliğe kayıt olabilmelidir.

### Mobil Arayüzü-QR Okuyucu Kişisi Tarafı
#### Etkinlik Kaydı ve QR Okutma :
- Kullanıcı adı ve şifre ile giriş yaparak etkinlik listesini görüntüleyebilmelidir.
- Her etkinliğin içindeki katılımcıları ve QR okutma durumlarını (onaylandı / onaylanmadı) görebilmelidir.
- QR kodu tarayarak etkinlik kaydını oluşturabilmelidir.

### Donanım ve Yazılım Gereksinimleri
#### Donanım Gereksinimleri:
- Sunucu: Heroku Eco Dynos - Minimum 256 mb RAM - Paylaşımlı CPU.
- Veritabanı: Heroku Mini Postgres - 64 MB Storage
- Mobil Cihazlar: Android ve iOS platformlarını desteklemelidir.
#### Yazılım Gereksinimleri:
- Web: Intellij Idea - Visual Studio Code - Herhangi bir modern tarayıcı.
- Mobil: Android Studio - Visual Studio Code.

## Fonksiyonel Olmayan Gereksinimler
Fonksiyonel olmayan gereksinimler, bir yazılım sisteminin performansını, kullanılabilirliğini, güvenilirliğini, güvenliğini ve diğer özelliklerini tanımlayan gereksinimlerdir.

### Performans Gereksinimleri
#### Sunucu Performansı:
- Sunucu, belirlenen saatlerde ve etkinlik anlarında yoğunluğa dayanıklı olmalıdır.
- Aynı anda birden fazla etkinlik ve kullanıcıyı destekleyebilmelidir.
#### Yük Testleri:
- Sistem, belirlenen maksimum kullanıcı sayısını ve etkinlik sayısını karşılayabilmek için yük testlerine tabi tutulmalıdır.

### Güvenlik Gereksinimleri
#### Veri Güvenliği
- Kullanıcı bilgileri, etkinlik detayları ve kayıtlar güvenli bir şekilde depolanmalı ve iletilmelidir.
- Şifreleme algoritmaları ve güvenlik standartları kullanılmalıdır. Kimlik Doğrulama ve Yetkilendirme:
- Kullanıcı kimlik doğrulama ve yetkilendirme süreçleri güvenli ve doğru bir şekilde işlemelidir.
- Yetkilendirme kontrolleri düzgün bir şekilde uygulanmalıdır.

### Kullanılabilirlik Gereksinimleri
#### Kolay Kullanım:
- Web ve mobil arayüzler, kullanıcılar için kolay ve anlaşılır olmalıdır.
- Her kullanıcı tipinin (yönetici, katılımcı, QR okuyucu) işlemleri kolaylıkla gerçekleştirebilmesi sağlanmalıdır.
#### Mobil Uyumluluk:
- Mobil cihazlarda kullanıcılar için uygun bir deneyim sağlanmalıdır.
- Mobil arayüz, farklı ekran boyutlarına ve çözünürlüklerine uygun olmalıdır.

### Güvenlik Gereksinimleri
#### Veri Güvenliği:
- Kullanıcı bilgileri ve etkinlik verileri güvenli bir şekilde saklanmalı ve
iletilmelidir.
- Şifreleme yöntemleri, güncel güvenlik standartlarına uygun olmalıdır.
#### Yetkilendirme ve Erişim Kontrolü:
- Yönetici ve kullanıcı yetkileri doğru bir şekilde yönetilmeli ve uygulanmalıdır.

### Sistem Erişebilirliği
#### Uptime ve Bakım Süreleri:
- Sistem, belirlenen çalışma saatlerinde kesintisiz olarak kullanılabilir olmalıdır.
- Bakım süreleri önceden duyurulmalı ve minimum düzeyde tutulmalıdır.

### Hata Yönetimi ve Geri Dönüş
#### Hata Mesajları:
- Kullanıcılar, sistemdeki hataları anlayabilecek açıklayıcı hata mesajları almalıdır.

### Entegrasyon Gereksinimleri:
#### Mobil Cihazlar ile Uyum:
- Mobil uygulamalar, Android ve iOS platformlarına uyumlu olmalıdır.
- Uygulamalar, platform güncellemelerine ve değişikliklerine uyumlu olmalıdır.
#### Web Tarayıcı Uyumluluğu:
- Web arayüzü, farklı tarayıcılar ve sürümleri ile uyumlu olmalıdır.

### Sonuç
QR Pass projesi, etkinliklerin düzenli ve hızlı bir şekilde yönetilmesini sağlamak, davet katılımını takip etmek, kayıt olma sürecini kolaylaştırmak ve QR teknolojisi ile etkinlik girişlerini optimize etmektir.

Fonksiyonel gereksinimler, Web Arayüzü-Yönetici Tarafı, Web Arayüzü-Katılımcı Tarafı ve Mobil Arayüzü-QR Okuyucu Kişisi Tarafı olmak üzere üç ana kategoride açıklanmıştır. Bu gereksinimler, uygulamanın temel işlevselliğini ve kullanıcı deneyimini belirlemektedir.

Fonksiyonel olmayan gereksinimler ise Performans, Güvenlik, Kullanılabilirlik, Sistem Erişebilirliği, Hata Yönetimi ve Geri Dönüş, Entegrasyon kategorilerinde açıklanmıştır. Bu gereksinimler, projenin performansını, güvenliğini, kullanılabilirliğini, erişilebilirliğini ve entegrasyon yeteneklerini sağlamaya yöneliktir.
