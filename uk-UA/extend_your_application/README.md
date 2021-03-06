{% set warning_icon = '<span class="glyphicon glyphicon-exclamation-sign" style="color: red;" aria-hidden="true" data-toggle="tooltip" title="An error is expected when you run this code!" ></span>' %}

# Розширте свою програму

Ми вже завершили всі етапи необхідні для створення нашого сайту: ми знаємо як написати модель, адресу URL, вигляд та шаблон. Ми також знаємо як зробити сайт привабливим.

Час попрактикуватись!

Перша річ, яка має бути у нашому блозі - це, очевидно, сторінка, що відображує один пост, правильно?

Ми вже маємо модель </code>посту`, тому не потрібно нічого додавати до <code>models.py`.

## Створюємо в шаблоні посилання на сторінку посту

Ми розпочнемо із додавання посилання всередині `blog/templates/blog/post_list.html` файлу. Відкрийте його в редакторі коду і поки що воно має виглядати так: {% filename %}blog/templates/blog/post_list.html{% endfilename %}

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

{% raw %}Ми хочемо, щоб в списку постів в заголовку було посилання на сторінку детальної інформації про пост. Давайте змінимо `<h2><a href="">{{ post.title }}</a></h2>` так, щоб було посилання на сторінку з детальною інформацією про пост:{% endraw %}

{% filename %}{{ warning_icon }} blog/templates/blog/post_list.html{% endfilename %}

```html
<h2><a href="{% url 'post_detail' pk=post.pk %}">{{ post.title }}</a></h2>
```

{% raw %}Час пояснити дивний запис `{% url 'post_detail' pk=post.pk %}`. Як і очікувалось, `{% %}` означає, що ми використовуємо шаблонні теги Django. На цей раз ми використаємо один, який створить адресу URL для нас! 

`post_detail` частина означає, що Django буде очікувати адресу URL у `blog/urls.py` з назвою=post_detail

А як щодо `pk=post.pk`? `pk` - це скорочення від первинного ключа, що є унікальним ідентифікатором для кожного запису в базі даних. Кожна модель Django має поле, яке виступає як первинний ключ і будь-яку іншу назву воно маже мати, це також може називатися "pk". Тому що ми не вказали основного ключа в моделі `поста`, Django створює одне для нас (за замовчуванням, поле з назвою "id", що збільшується на усі записи, наприклад 1,2,3) і додає це поле в кожну з наших записів. Ми маємо доступ до первинного ключа, записуючи `post.pk`, так само як ми отримуємо доступ до інших полів (`назва`,`автор` і т.д.) у нашому об'єкті `пост`!

Тепер, коли ми переходимо до http://127.0.0.1:8000/, ми отримуємо помилку (як і оікувалось, оскільки у нас немає адреси URL або потрібного *вигляду* для `post_detail`. Це буде виглядати наступним чином:

![NoReverseMatch error](images/no_reverse_match2.png)

## Створюєм адресу URL для деталей запису

Давайте створимо адресу URL на `urls.py` для нашого *вигляду* `post_detail`!

Ми хочемо, щоб наш перший пост був доступний за такою адресою **URL**: http://127.0.0.1:8000/post/1/ 

Давайте створимо адресу URL в файлі `blog/urls.py` і вкажемо Django на *вигляд* з назвою `post_detail`, який буде відображати пост цілком. Відкрийте файл `blog/urls.py` в редакторі коду і додайте рядок `path('post/<int:pk>/', views.post_detail, name='post_detail'),` так щоб файл виглядав так:

{% filename %}{{ warning_icon }} blog/urls.py{% endfilename %}

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.post_list, name='post_list'),
    path('post/<int:pk>/', views.post_detail, name='post_detail'),
]
```

Ця частина `post<int:pk>/` визначає шаблон адреси URL - ми пояснимо це вам:

- `post` означає, що URL-адреса має починатися зі слова **post** з такою назвою ****. Все йде правильно.
- `<int:pk>` - ця частина складніша. Це означає, що Django очікує ціле значенння і передасть його до вигляду як змінну `pk`.
- `/` - тоді нам знадобиться **/** після завершення URL-адреси.

Це означає, що якщо ви введете `http://127.0.0.1:8000/post/5/`, Django зрозуміє, що ви шукаєте відображення із назвою `post_detail` і передає цьому відображенню інформацію, що `pk` дорівнює `5`.

Гаразд, ми додали новий шаблон URL-адрес до `blog/urls.py`! Let's refresh the page: http://127.0.0.1:8000/ Boom! The server has stopped running again. Have a look at the console – as expected, there's yet another error!

![AttributeError](images/attribute_error2.png)

Do you remember what the next step is? It's adding a view!

## Додамо деталі відображення запису

This time our *view* is given an extra parameter, `pk`. Our *view* needs to catch it, right? So we will define our function as `def post_detail(request, pk):`. Note that this parameter must have the exact same name as the one we specified in `urls` (`pk`). Also note that omitting this variable is incorrect and will result in an error!

Now, we want to get one and only one blog post. To do this, we can use querysets, like this:

{% filename %}{{ warning_icon }} blog/views.py{% endfilename %}

```python
Post.objects.get(pk=pk)
```

But this code has a problem. If there is no `Post` with the given `primary key` (`pk`) we will have a super ugly error!

![DoesNotExist error](images/does_not_exist2.png)

We don't want that! But luckily Django comes with something that will handle that for us: `get_object_or_404`. In case there is no `Post` with the given `pk`, it will display much nicer page, the `Page Not Found 404` page.

![Page not found](images/404_2.png)

The good news is that you can actually create your own `Page not found` page and make it as pretty as you want. But it's not super important right now, so we will skip it.

OK, time to add a *view* to our `views.py` file!

In `blog/urls.py` we created a URL rule named `post_detail` that refers to a view called `views.post_detail`. This means that Django will be expecting a view function called `post_detail` inside `blog/views.py`.

We should open `blog/views.py` in the code editor and add the following code near the other `from` lines:

{% filename %}blog/views.py{% endfilename %}

```python
from django.shortcuts import render, get_object_or_404
```

And at the end of the file we will add our *view*:

{% filename %}blog/views.py{% endfilename %}

```python
def post_detail(request, pk):
    post = get_object_or_404(Post, pk=pk)
    return render(request, 'blog/post_detail.html', {'post': post})
```

Yes. It is time to refresh the page: http://127.0.0.1:8000/

![Post list view](images/post_list2.png)

It worked! But what happens when you click a link in blog post title?

![TemplateDoesNotExist error](images/template_does_not_exist2.png)

Oh no! Another error! But we already know how to deal with it, right? We need to add a template!

## Create a template for the post details

We will create a file in `blog/templates/blog` called `post_detail.html`, and open it in the code editor.

Enter the following code:

{% filename %}blog/templates/blog/post_detail.html{% endfilename %}

```html
{% extends 'blog/base.html' %}

{% block content %}
    <article class="post">
        {% if post.published_date %}
            <time class="date">
                {{ post.published_date }}
            </time>
        {% endif %}
        <h2>{{ post.title }}</h2>
        <p>{{ post.text|linebreaksbr }}</p>
    </article>
{% endblock %}
```

Once again we are extending `base.html`. In the `content` block we want to display a post's published_date (if it exists), title and text. But we should discuss some important things, right?

{% raw %}`{% if ... %} ... {% endif %}` is a template tag we can use when we want to check something. (Remember `if ... else ...` from **Introduction to Python** chapter?) In this scenario we want to check if a post's `published_date` is not empty.{% endraw %}

OK, we can refresh our page and see if `TemplateDoesNotExist` is gone now.

![Post detail page](images/post_detail2.png)

Yay! It works!

# Deploy time!

It'd be good to see if your website still works on PythonAnywhere, right? Let's try deploying again.

{% filename %}command-line{% endfilename %}

    $ git status
    $ git add .
    $ git status
    $ git commit -m "Added view and template for detailed blog post as well as CSS for the site."
    $ git push
    

Then, in a [PythonAnywhere Bash console](https://www.pythonanywhere.com/consoles/):

{% filename %}PythonAnywhere command-line{% endfilename %}

    $ cd ~/<your-pythonanywhere-domain>.pythonanywhere.com
    $ git pull
    [...]
    

(Remember to substitute `<your-pythonanywhere-domain>` with your actual PythonAnywhere subdomain, without the angle-brackets.)

## Updating the static files on the server

Servers like PythonAnywhere like to treat "static files" (like CSS files) differently from Python files, because they can optimise for them to be loaded faster. As a result, whenever we make changes to our CSS files, we need to run an extra command on the server to tell it to update them. The command is called `collectstatic`.

Start by activating your virtualenv if it's not still active from earlier (PythonAnywhere uses a command called `workon` to do this, it's just like the `source myenv/bin/activate` command you use on your own computer):

{% filename %}PythonAnywhere command-line{% endfilename %}

    $ workon <your-pythonanywhere-domain>.pythonanywhere.com
    (ola.pythonanywhere.com)$ python manage.py collectstatic
    [...]
    

The `manage.py collectstatic` command is a bit like `manage.py migrate`. We make some changes to our code, and then we tell Django to *apply* those changes, either to the server's collection of static files, or to the database.

In any case, we're now ready to hop on over to the ["Web" page](https://www.pythonanywhere.com/web_app_setup/) (from the menu button in the upper right of the console) and hit **Reload**, and then look at the https://subdomain.pythonanywhere.com page to see the result.

And that should be it. Congrats! :)