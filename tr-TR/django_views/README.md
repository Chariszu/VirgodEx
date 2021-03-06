# Django views - yaratma zamanı geldi!

Bir önceki bölümde ortaya çıkan hatayı ortadan kaldırma vakti geldi! :)

*view*, uygulamamızın "mantığının" ifade edildiği yerdir. Daha önce oluşturduğumuz `model` den bilgi alarak `template`'e iletir. "template"i ise gelecek bölümde oluşturacağız. View'ler bildiğiniz Python fonksiyonlarıdır. Ancak, **Python'a Giriş** bölümünde yazdığımız fonksiyonlardan biraz daha karmaşıktır.

View'ler `views.py` dosyasında yer alır. Şimdi, *view*'larımızı `blog/views.py` dosyasına ekleyelim.

## blog/views.py

Tamam, şimdi bu dosyayı açalım ve içinde ne olduğuna bakalım:

{% filename %}blog/views.py{% endfilename %}

```python
from django.shortcuts import render

# Create your views here.
```

Henüz fazla bir şey yok.

`#` ile başlayan satırların yorumlar olduğunu unutmayın - bu # ile başlayan satırların Python tarafından çalıştırılmayacağı anlamına geliyor.

Hadi yorumun önerdiği gibi bir *view* oluşturalım. Bunun için alttaki viewı en alta ekleyin:

{% filename %}blog/views.py{% endfilename %}

```python
def post_list(request):
    return render(request, 'blog/post_list.html', {})
```

As you can see, we created a function (`def`) called `post_list` that takes `request` and will `return` the value it gets from calling another function `render` that will render (put together) our template `blog/post_list.html`.

Dosyamızı kaydedelim ve http://127.0.0.1:8000/ adresine gidip bakalım.

Bir başka hata! Okuyup neler olduğunu anlamaya çalışalım:

![Hata](images/error.png)

İyi tarafından bakarsak bu hata en azından sunucumuzun yeniden çalıştığını gösteriyor, ama hala bir şeyler yanlış, değil mi? Dert etmeyin, sadece bir hata sayfası, korkacak bir şey yok! Komut satırındaki hata mesajları gibi bunlar da aslında oldukça yararlılar. *TemplateDoesNotExist* hatası alıyoruz, yani Template bulunamadı. Gelecek bölümde bu hatayı template oluşturarak düzeltelim!

> Learn more about Django views by reading the official documentation: https://docs.djangoproject.com/en/2.2/topics/http/views/