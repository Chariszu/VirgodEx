# Pag-extend ng template

Isa pang magandang bagay na mayroon ang Django para sa iyo ay **template extending**. Ano ang ibig sabihin nito? Ibig sabihin nito ay maaari mong gamitin ang parehong mga parte ng iyong HTML sa iba't ibang pahina ng iyong website.

Ang mga template ay nakatutulong kapag gusto mong gamitin ang parehong impormasyon o layout sa higit sa isang lugar. Hindi mo na kinakailangan na ulitin ang iyong sarili sa bawat file. At kung gusto mong baguhin ang isang bagay, hindi mo na kinakailangan na gawin ito sa bawat template, sa isa lang!

## Gumawa ng isang base template

Ang isang base template ay ang pinaka basic na template na ginagamit mo sa bawat pahina ng iyong website.

Gumawa tayo ng isang `base.html` na file sa `blog/templates/blog/`:

    blog
    └───templates
        └───blog
                base.html
                post_list.html
    

Pagkatapos ay buksan ito at kopyahin lahat mula sa `post_list.html` sa `base.html` na file, kagaya nito:

{% filename %}blog/templates/blog/base.html{% endfilename %}

```html
{% load staticfiles %}
<html>
    <head>
        <title>Django Girls blog</title>
        <link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css">
        <link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css">
        <link href='//fonts.googleapis.com/css?family=Lobster&subset=latin,latin-ext' rel='stylesheet' type='text/css'>
        <link rel="stylesheet" href="{% static 'css/blog.css' %}">
    </head>
    <body>
        <div class="page-header">
            <h1><a href="/">Django Girls Blog</a></h1>
        </div>

        <div class="content container">
            <div class="row">
                <div class="col-md-8">
                {% for post in posts %}
                    <div class="post">
                        <div class="date">
                            {{ post.published_date }}
                        </div>
                        <h1><a href="">{{ post.title }}</a></h1>
                        <p>{{ post.text|linebreaksbr }}</p>
                    </div>
                {% endfor %}
                </div>
            </div>
        </div>
    </body>
</html>
```

Pagkatapos, sa `base.html`, palitan ang iyong kabuuang `<body>` (everything between `<body>` and `</body>`) nito:

{% filename %}blog/templates/blog/base.html{% endfilename %}

```html
<body>
    <div class="page-header">
        <h1><a href="/">Django Girls Blog</a></h1>
    </div>
    <div class="content container">
        <div class="row">
            <div class="col-md-8">
            {% block content %}
            {% endblock %}
            </div>
        </div>
    </div>
</body>
```

{% raw %}Maaaring napansin mo na pinalitan nito ang lahat ng mula sa `{% for post in posts %}` sa `{% endfor %}` ng: {% endraw %}

{% filename %}blog/templates/blog/base.html{% endfilename %}

```html
{% block content %}
{% endblock %}
```

Pero bakit? Ikaw ay nakagawa ng isang `block`! Ginamit mo ang template tag na `{% block %}` upang gumawa ng lugar na magkakaroon ng HTML na nakalakip dito. Ang HTML na ito ay manggagaling sa ibang template na ini-extend ang template na ito (`base.html`). Ipapakita namin sa iyo kung paano ito gawin maya-maya.

Ngayon, i-save ang `base.html` at buksan ang `blog/templates/blog/post_list.html` ulit. {% raw %}Tatanggalin mo ang lahat ng nasa taas ng `{% for post in posts %}` at sa baba `{% endfor %}`. Kapag tapos ka na, ang file ay magiging kagaya nito: {% endraw %}

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
{% for post in posts %}
    <div class="post">
        <div class="date">
            {{ post.published_date }}
        </div>
        <h1><a href="">{{ post.title }}</a></h1>
        <p>{{ post.text|linebreaksbr }}</p>
    </div>
{% endfor %}
```

Gusto nating gagamitin ito isip parte ng ating template para sa lahat ng mga content block. Oras na para magdagdag ng block na tags sa file na ito!

{% raw %}Gusto mo na ang iyong block tag ay magtugma sa tag ng iyong `base.html` na file. Gusto mo ring itong maglakip ng lahat ng code na pag-aari ng iyong content blocks. Para gawin ito, ilagay lahat sa pagitan ng `{% block content %}` at `{% endblock %}`. Gaya nito:{% endraw %}

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
{% block content %}
    {% for post in posts %}
        <div class="post">
            <div class="date">
                {{ post.published_date }}
            </div>
            <h1><a href="">{{ post.title }}</a></h1>
            <p>{{ post.text|linebreaksbr }}</p>
        </div>
    {% endfor %}
{% endblock %}
```

Isang bagay na lang ang natira. Kailangan nating ikonekta ang dalawang templates. Ito ang ibig sabihin ng pag-extend na mga templates! Gagawin natin ito sa pamamagitan ng pagdagdag ng extend na tag sa simula ng file. Gaya nito:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
{% extends 'blog/base.html' %}

{% block content %}
    {% for post in posts %}
        <div class="post">
            <div class="date">
                {{ post.published_date }}
            </div>
            <h1><a href="">{{ post.title }}</a></h1>
            <p>{{ post.text|linebreaksbr }}</p>
        </div>
    {% endfor %}
{% endblock %}
```

Iyan na! Tingnan ang iyong website kung gumagana pa rin ito. :)

> Kung may nakuha kang error na `TemplateDoesNotExist`, ibig sabihin ay walang `blog/base.html` na file at ang `runserver` ay tumatakbo sa iyong console. Subukang ihinto ito (sa pamamagitan ng pag-pindut ng Ctrl+C - ang Control at ang C na mga key ng sabay) at i-start itong muli sa pamamagitan ng pagpapatakbo ng isang `python manage.py runserver` na pag-uutos.