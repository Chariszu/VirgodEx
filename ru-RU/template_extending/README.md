# Расширение шаблона

Еще одной удобной вещью в Django является **расширение шаблонов**. Что это значит? Ты можешь использовать различные блоки HTML-кода для разных частей своего веб-сайта.

Шаблоны помогают, когда вы хотите использовать одну и ту же информацию или один и тот же макет в более чем одном месте. Вам не придется повторяться в каждом файле. И если вы хотите что-то изменить, то вы не должны делать это в каждом шаблоне, так как он всего один!

## Создаем базовый шаблон

Базовый шаблон - это наиболее общая типовая форма страницы, которую ты расширяешь для отдельных случев.

Давай создадим файл `base.html` в директории `blog/templates/blog/`:

    blog
    └───templates
        └───blog
                base.html
                post_list.html
    

Теперь открой его в редакторе кода и скопируй все из `post_list.html` файла в `base.html` файл примерно так:

{% filename %}blog/templates/blog/base.html{% endfilename %}

```html
{% load static %}
<!DOCTYPE html>
<html>
    <head>
        <title>Django Girls blog</title>
        <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/css/bootstrap.min.css" integrity="sha384-TX8t27EcRE3e/ihU7zmQxVncDAy5uIKz4rEkgIXeMed4M0jlfIDPvg6uqKI2xXr2" crossorigin="anonymous">
        <link href='//fonts.googleapis.com/css?family=Lobster&subset=latin,latin-ext' rel='stylesheet' type='text/css'>
        <link rel="stylesheet" href="{% static 'css/blog.css' %}">
    </head>
    <body>
        <header class="page-header">
          <div class="container">
              <h1><a href="/">Django Girls Blog</a></h1>
          </div>
        </header>

        <main class="container">
            <div class="row">
                <div class="col">
                {% for post in posts %}
                    <article class="post">
                        <time class="date">
                            {{ post.published_date }}
                        </time>
                        <h2><a href="">{{ post.title }}</a></h2>
                        <p>{{ post.text|linebreaksbr }}</p>
                    </article>
                {% endfor %}
                </div>
            </div>
        </main>
    </body>
</html>
```

Затем в файле `base.html` замени все между тегами `<body>` и `</body>` следующим кодом:

{% filename %}blog/templates/blog/base.html{% endfilename %}

```html
<body>
    <header class="page-header">
      <div class="container">
          <h1><a href="/">Django Girls Blog</a></h1>
      </div>
    </header>
    <main class="container">
        <div class="row">
            <div class="col">
            {% block content %}
            {% endblock %}
            </div>
        </div>
    </main>
</body>
```

{% raw %}Как ты заметила, мы заменили все из `{% for post in posts %}` на `{% endfor %}` с: {% endraw %}

{% filename %}blog/templates/blog/base.html{% endfilename %}

```html
{% block content %}
{% endblock %}
```

Но почему? Ты только что создала `блок`! Ты использовала тег шаблона `{% block %}`, чтобы создать область, в которую будет вставляться HTML. Что HTML будет поступать из другого шаблона, который расширяет этот шаблон (`base.html`). Мы покажем как это сделать через секунду.

Теперь сохрани `base.html` и снова открой ваш `blog/templates/blog/post_list.html` файл в редакторе кода. {% raw %}Тебе предстоит удалить все, что выше `{% for post in posts %}` и ниже `{% endfor %}`. Когда ты закончишь, файл будет выглядеть следующим образом:{% endraw %}

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
{% for post in posts %}
    <article class="post">
        <time class="date">
            {{ post.published_date }}
        </time>
        <h2><a href="">{{ post.title }}</a></h2>
        <p>{{ post.text|linebreaksbr }}</p>
    </article>
{% endfor %}
```

Мы хотим использовать это как часть нашего шаблона для всех блоков контента. Пришло время добавить теги блока в этот файл!

{% raw %}Вы хотите, чтобы ваш тег блока соответствовал тегу в файле `base.html`. Вы также хотите включить весь код, который принадлежит к блокам контента. Для этого поместите все между `{% block content %}` и `{% endblock %}`. Таким образом:{% endraw %}

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
{% block content %}
    {% for post in posts %}
        <article class="post">
            <time class="date">
                {{ post.published_date }}
            </time>
            <h2><a href="">{{ post.title }}</a></h2>
            <p>{{ post.text|linebreaksbr }}</p>
        </article>
    {% endfor %}
{% endblock %}
```

Осталось только одно. Нам нужно соединить эти два шаблона друг с другом. Это то, что называется "расширить шаблон"! Мы сделаем это, добавив тег расширения к началу файла. Вот так:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
{% extends 'blog/base.html' %}

{% block content %}
    {% for post in posts %}
        <article class="post">
            <time class="date">
                {{ post.published_date }}
            </time>
            <h2><a href="">{{ post.title }}</a></h2>
            <p>{{ post.text|linebreaksbr }}</p>
        </article>
    {% endfor %}
{% endblock %}
```

Готово! Сохрани файл и проверь, работает ли твой веб-сайт нормально. :)

> Если у тебя появилась ошибка `TemplateDoesNotExist`, это означает, что отсутствует файл `blog/base.html` и в консоли работает `runserver`. Попробуй остановить его (одновременным нажатием Ctrl+C - клавиш Control и C одновременно) и перезапусти сервер с помощью команды `Python manage.py runserver`.