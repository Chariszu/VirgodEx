# Django URL'leri

İlk web sayfamızı kurmak üzereyiz: bloğun için bir ana sayfa! Ama öncelike, Django URL'leri hakkında biraz bilgi edinelim.

## URL nedir?

URL basitçe bir web adresidir. Her defasında bir web sitesini ziyaret ettiğinde bir URL görürsün. Tarayıcının adres çubuğunda görünmektedir. (Evet! `127.0.0.1:8000` bir URL'dir! Ve`https://djangogirls.org`'da bir URL'dir)

![Url](images/url.png)

Internetteki her sayfanın kendi URL'si olması gerekir. Bu yolla uygulama URl'yi açan kullanıcaya ne göstemesi gerektiğini bilir. Django'da `URLconf` (URL konfigürasyonu) denilen bir şey kullanıyoruz. URLconf is a set of patterns that Django will try to match with the requested URL to find the correct view.

## URL'ler Django'da nasıl çalışır?

Kod editörümüzde `mysite/urls.py` dosyasını açalım ve neye benzediğine bakalım:

{% filename %}mysite/urls.py{% endfilename %}

```python
"""mysite URL Configuration

[...]
"""
from django.conf.urls import url
from django.contrib import admin

urlpatterns = [
    url(r'^admin/', admin.site.urls),
]
```

Gördüğünüz gibi, Django çoktan bizim için buraya bir şey yerleştirmiş.

Lines between triple quotes (`'''` or `"""`) are called docstrings – you can write them at the top of a file, class or method to describe what it does. Python bunları çalıştırmaz.

Önce ki bölümde ziyaret ettğiniz yönetici URL'si şimdiden burada:

{% filename %}mysite/urls.py{% endfilename %}

```python
    url(r'^admin/', admin.site.urls),
```

This line means that for every URL that starts with `admin/`, Django will find a corresponding *view*. In this case we're including a lot of admin URLs so it isn't all packed into this small file – it's more readable and cleaner.

## Regex (Kurallı İfade)

Django'nun URL'leri view'larla nasıl eşleştirdiğini merak ediyor musunuz? Bu kısım biraz karışık. Django bunun için `regex` kullanıyor. Regex, "regular expressions"ın kısaltılmış hali ve düzenli ifadeler anlamına geliyor. Regex'in bir arama kalıbı oluşturmak için birçok (birçok!) kuralı var. Regexler ileri bir konu olduğu için nasıl çalıştığının detayına girmeyeceğiz.

Gene de kalıpları nasıl oluşturduğumuzu anlamak isterseniz, aşağıdaki bir örnek var - aradığımız kalıbı oluşturmak için kuralların sadece bir kısmına ihtiyacımız olacak, şöyle:

* `^` metnin başlangıcı için
* metnin sonu için `$`
* `\d` for a digit
* `+` belirlemek için bi önceki öğenin en az bir kez tekrarlanması lazım
* `()` to capture part of the pattern

Anything else in the URL definition will be taken literally.

Now imagine you have a website with the address like `http://www.mysite.com/post/12345/`, where `12345` is the number of your post.

Her gönderi için ayrı bir view yazmak gerçekten can sıkıcı olurdu. With regular expressions, we can create a pattern that will match the URL and extract the number for us: `^post/(\d+)/$`. Şimdi bunu, burada ne yaptığımızı görebilmek için parçalarına ayıralım:

* **^post/** is telling Django to take anything that has `post/` at the beginning of the url (right after `^`)
* **(\d+)** ise bir sayı (birden fazla rakam) olduğunu ve bu sayıyı yakalamak ve çıkarmak istediğimizi belirtiyor
* **/** ise Django'ya arkasından bir `/` karakteri gelmesi gerektiğini söylüyor
* **$** ise URL'nin sonuna işaret ediyor, yani sadece sonu `/` ile biten string'ler bu kalıpla eşleşecek

## İlk Django URL'niz!

İlk URL'mizi oluşturma zamanı.'http://127.0.0.1:8000/' adresinin bloğumuzun anasayfası olmasını ve gönderilerin bir listesini görüntülemesini istiyoruz.

We also want to keep the `mysite/urls.py` file clean, so we will import URLs from our `blog` application to the main `mysite/urls.py` file.

Go ahead, add a line that will import `blog.urls`. Note that we are using the `include` function here so you will need to add that import.

`mysite/urls.py` dosyanız şöyle olmalıdır:

{% filename %}mysite/urls.py{% endfilename %}

```python
from django.conf.urls import include
from django.conf.urls import url
from django.contrib import admin

urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'', include('blog.urls')),
]
```

Django artık 'http://127.0.0.1:8000/'ye gelen her şeyi `blog.urls`'ya yönlendirecek ve ordaki yönergelere bakacak.

Writing regular expressions in Python is always done with `r` in front of the string. Bu Python için string'in özel karakterler içerdiğini, doğrudan Python için değil düzenli ifadeler için bir string olduğu konusunda ipucu verir.

## blog.urls

Create a new empty file named `urls.py` in the `blog` directory. All right! Add these first two lines:

{% filename %}blog/urls.py{% endfilename %}

```python
from django.conf.urls import url
from . import views
```

Here we're importing Django's function `url` and all of our `views` from the `blog` application. (We don't have any yet, but we will get to that in a minute!)

Bundan sonra ilk URL kalıbımızı ekleyebiliriz:

{% filename %}blog/urls.py{% endfilename %}

```python
urlpatterns = [
    url(r'^$', views.post_list, name='post_list'),
]
```

As you can see, we're now assigning a `view` called `post_list` to the `^$` URL. This regular expression will match `^` (a beginning) followed by `$` (an end) – so only an empty string will match. Bu doğru çünkü Django URL çözücülerinde 'http://127.0.0.1:8000/' URL'nin parçası değildir. Bu kalıp, Django'ya eğer siteye biri 'http://127.0.0.1:8000/' adresinden gelirse gitmesi gereken yerin `views.post_list` olduğunu söylüyor.

The last part, `name='post_list'`, is the name of the URL that will be used to identify the view. Bu view'un adı ile aynı olabilir ama tamamen farklı bir şey de olabilir. We will be using the named URLs later in the project, so it is important to name each URL in the app. We should also try to keep the names of URLs unique and easy to remember.

Eğer şimdi http://127.0.0.1:8000/'ine gitmeyi denerseniz, 'sayfanıza ulaşılamıyor' tarzında bir mesaj görürsünüz. Bunun nedeni sunucu (`runserver` yazdığınızı hatırlıyor musunuz?) artık çalışmıyor olacaktır. Sebebini bulmak için sunucunuzdaki komut penceresine bakın.

![Hata](images/error1.png)

Your console is showing an error, but don't worry – it's actually pretty useful: It's telling you that there is **no attribute 'post_list'**. Bu Django'nun bulup kullanmaya çalıştığı *view*'un adı. Ama onu henüz oluşturmedık. At this stage your `/admin/` will also not work. Endişeye gerek yok - o noktaya ulaşacağız.

> Django URLconfs ile ilgili daha fazla bilgi edinmek istiyorsanız resmi dokümantasyona bakabilirsiniz: https://docs.djangoproject.com/en/1.11/topics/http/urls/