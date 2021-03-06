# Django views - čas tvoriť!

Je čas zbaviť sa toho bugu, čo sme vytvorili v poslednej kapitole! :)

*View* je miesto, kam dávame "logiku" našej aplikácie. Bude požadovať informáciu z `modelu`, ktorý si už vytvorila a pošle to do `šablóny`. Šablónu (template) budeme vytvárať v nasledujúcej kapitole. Views sú vlastne len metódy Pythonu, ktoré sú trochu zložitejšie, ako tie, ktoré sme písali v kapitole **Úvod do Pythonu**.

Views sú umiestnené v súbore `views.py`. Naše *views* budeme pridávať do súboru `blog/views.py`.

## blog/views.py

OK, let's open up this file in our code editor and see what's in there:

{% filename %}blog/views.py{% endfilename %}

```python
from django.shortcuts import render

# Create your views here.
```

Je tu toho málo zatiaľ.

Ako si spomínaš riadky začínajúce s `#` sú komentáre - to znamená, že ich Python nespustí.

Vytvorme *view* ako nám komentár naznačuje. Pridaj nasledovný minimálny view pod komentárom:

{% filename %}blog/views.py{% endfilename %}

```python
def post_list(request):
    return render(request, 'blog/post_list.html', {})
```

As you can see, we created a function (`def`) called `post_list` that takes `request` and will `return` the value it gets from calling another function `render` that will render (put together) our template `blog/post_list.html`.

Ulož súbor a prejdi na http://127.0.0.1:8000 / a pozri sa, čo sa udeje.

Ďalšia chyba! Prečítaj si, o čo ide tentokrát:

![Chyba](images/error.png)

Ukazuje, že server aspoň znovu beží, ale stále to nie je ono, že? Neboj sa, je to len chybová stránka, nič čoho sa treba báť! Podobne ako chyby v konzole, sú vlastne velkom úťitočné. Dočítaš sa, že *TemplateDoesNotExist*. Poďme opraviť túto chybu a vytvoríme šablónu v nasledujúcej kapitole!

> Learn more about Django views by reading the official documentation: https://docs.djangoproject.com/en/2.2/topics/http/views/