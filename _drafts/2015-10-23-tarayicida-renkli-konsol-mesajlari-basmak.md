---
title : Tarayıcıda Renkli Konsol Mesajları Basmak
tags  : ['devtools', 'console']
---
{% capture image_path %}{{site.url}}/assets/images/content/2015-10-23-tarayicida-renkli-konsol-mesajlari-basmak/{% endcapture %}

<p class="lead">Alert popülerliğini yitirdikten sonra hepimiz console.log'a sardık. Artık o yokken nasıl kod yazıyorduk hatırlamıyoruz bile. Ancak siyah beyaz loglardan ötesi de mümkün.</p>
<!--more-->

> Hikaye dinlemek istemeyenler doğrudan uygulama kısmına atlayabilirler.

# Hikaye
Şu an çalıştığım projede geliştirdiğimiz yapıyı birçok backend developer kullanıyor. Bu nedenle pek çok hata geri dönüşü alıyoruz. Herkes de doğal olarak kendi bilgisayarıyla geliyor 'abi bu çalışmıyor' diye. Her geri dönüşte açıp debugging yapmak artık zor gelmeye başlayınca; sistemin her adımı loglayacağı bir yapı geliştireyim dedim.

Fikir basit. Her adımda loglama olacaktı. Sunucuya request mi atıldı logla, cevap mı geldi logla, plugin mi çalıştırılacak logla, sayfa içeriği mi değişiyor logla, ne oluyorsa önce logla! Sonra 'biri bu çalışmıyor' deyince de ilk iş aç loglara bak hangi adıma kadar gelmiş, nerede patlamış diye.

Ancak art arda onlarca log basınca konsol mide bulandırıcı bir hal aldı. Ne bir bakışta loglar birbirinden ayırtedilebiliyordu ne de insanın konsola bakası geliyordu. Şu konsola bir renk katmak gerekliydi.

# Uygulama

İlk söylenmesi gereken konsol mesajlarının `console.log`'dan ibaret olmadığı.

### console.error
{% highlight js lineno %} console.error('Çok pis bir olay oldu!'); {% endhighlight %}
!["console.error çıktısı"]({{image_path}}console.error.output.png "console.error çıktısı"){: .border-wrapper }

Kritik bir hata oluşan durumlarda eğer hata fırlatmak istemiyorsanız, kullanılabilecek konsol mesajıdır. Aynı zamanda mesajın solundaki ok simgesine dikkat edin, simgeye tıklayarak callstack'i görüntüleyebilirsiniz.

### console.info
{% highlight js lineno %} console.info('Sana bir haberim var!'); {% endhighlight %}
!["console.info çıktısı"]({{image_path}}console.info.output.png "console.info çıktısı"){: .border-wrapper }

Beklenen bir şey olduğunda veya olmasaydı da olurdu ama olması çok güzel dedirten şeylerde kullanılabilecek, coşku ifade eden mesaj tipi.

### console.log
{% highlight js lineno %} console.log('Şu durum gerçekleşti.'); {% endhighlight %}
!["console.log çıktısı"]({{image_path}}console.log.output.png "console.log çıktısı"){: .border-wrapper }

Bildiğiniz console.log. Sıradan işlemleri, anlık durumu loglamak için kullanılmalıdır.

### console.warn
{% highlight js lineno %} console.warn('Bu sadece bir uyarıydı!'); {% endhighlight %}
!["console.warn çıktısı"]({{image_path}}console.warn.output.png "console.warn çıktısı"){: .border-wrapper }

Sistemi patlatmaz ama olmasaydı daha iyiydi, bak buna dikkat et, yapma böyle şeyler demek istediğiniz anlarda kızlarımızın 'neyse' sözünü söylerken kullandıklarını tonlama ile beliren mesaj. Bi uyarı gençler. 

Buraya kadar tamam.

# Tarayıcı Desteği
Burada anlatılanlar Google Chrome ve Firefox üzerinde çalışır. Konsolların CSS'i destekleyip desteklemediğini şu an için öğrenmenin bir yolu olmadığından tarayıcı tespit edilerek kullanılması tavsiye edilir.

Bu anlatılanlarla ilgili daha detaylı bilgiye <a href="https://developers.google.com/web/tools/chrome-devtools/debug/console/console-write#string-substitution-and-formatting" target='_blank'>Chrome Devtools / String Substitution and Formatting</a> sayfası altından erişebilirsiniz. Aynı sayfadan konsolun farklı yeteneklerine de göz gezdirebilirsiniz. Tek olayı mesaj basmak değil.