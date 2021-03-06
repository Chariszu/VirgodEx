# Django šablony

Je čas zobrazit nějaká data! Django nám k tomuto účelu poskytuje užitečné, vestavěné **šablonové tagy**.

## Co jsou šablonové tagy?

You see, in HTML, you can't really write Python code, because browsers don't understand it. They know only HTML. We know that HTML is rather static, while Python is much more dynamic.

**Django template tags** allow us to transfer Python-like things into HTML, so you can build dynamic websites faster. Cool!

## Zobraz šablonu se seznamem příspěvků

V předchozí kapitole jsme dali naší šabloně seznam příspěvků v proměnné `posts`. Teď to zobrazíme v HTML.

V Django šabloně se proměnná vypíše pomocí dvojitých složených závorek s názvem proměnné uvnitř. Takhle:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
{{ posts }}
```

Zkus to ve své šabloně `blog/templates/blog/post_list.html`. Nahraď vše od druhého `<div>` do třetího `</div>` řádkou `{{ posts }}`. Ulož soubor a obnov stránku, abys viděla výsledek:

![Figure 13.1](images/step1.png)

Jak vidíš, dostali jsme toto:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<QuerySet [<Post: My second post>, <Post: My first post>]>
```

To znamená, že to Django chápe jako seznam objektů. Vzpomínáš si z kapitoly **Úvod do pythonu**, jak můžeme zobrazit seznam? Ano, pomocí for smyček! V Django šabloně je použiješ takto:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
{% for post in posts %}
    {{ post }}
{% endfor %}
```

Zkus udělat tohle ve své šabloně.

![Figure 13.2](images/step2.png)

Funguje to! But we want the posts to be displayed like the static posts we created earlier in the **Introduction to HTML** chapter. Můžeš smíchat HTML tagy se šablonovými. Naše `body` bude vypadat takhle:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<div>
    <h1><a href="/">Django Girls Blog</a></h1>
</div>

{% for post in posts %}
    <div>
        <p>published: {{ post.published_date }}</p>
        <h1><a href="">{{ post.title }}</a></h1>
        <p>{{ post.text|linebreaksbr }}</p>
    </div>
{% endfor %}
```

{% raw %}Všechno co dáš mezi `{% for %}` a `{% endfor %}` se zopakuje pro každý objekt v seznamu. Obnov svou stránku:{% endraw %}

![Figure 13.3](images/step3.png)

Have you noticed that we used a slightly different notation this time (`{{ post.title }}` or `{{ post.text }})`? Přistupujeme k datům v každém poli defnovaném v našem `Post` modelu. Also, the `|linebreaksbr` is piping the posts' text through a filter to convert line-breaks into paragraphs.

## Ještě jedna věc

It'd be good to see if your website will still be working on the public Internet, right? Let's try deploying to PythonAnywhere again. Here's a recap of the steps…

* Nejdřív hoď svůj kód na Github

{% filename %}command-line{% endfilename %}

    $ git status
    [...]
    $ git add --all .
    $ git status
    [...]
    $ git commit -m "Modified templates to display posts from database."
    [...]
    $ git push
    

* Pak se přihlaš do [PythonAnywhere](https://www.pythonanywhere.com/consoles/) s jdi do **Bash konzole** (nebo vytvoř novou) a zadej:

{% filename %}PythonAnywhere command-line{% endfilename %}

    $ cd my-first-blog
    $ git pull
    [...]
    

* Konečně, jdi na záložku [Web](https://www.pythonanywhere.com/web_app_setup/) a klikni na **Reload**. Tvá stránka by měla být aktuální! If the blog posts on your PythonAnywhere site don't match the posts appearing on the blog hosted on your local server, that's OK. Databáze v místním počítači a Python Anywhere není synchronizována.

Gratulujeme! Now go ahead and try adding a new post in your Django admin (remember to add published_date!) Make sure you are in the Django admin for your pythonanywhere site, https://yourname.pythonanywhere.com/admin. Then refresh your page to see if the post appears there.

Works like a charm? We're proud! Step away from your computer for a bit – you have earned a break. :)

![Figure 13.4](images/donut.png)