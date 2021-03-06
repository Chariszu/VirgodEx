# Шаблоны Django

Пришло время отобразить данные на сайте! Django поможет нам с этим при помощи встроенных **тегов шаблонов**.

## Что представляют из себя теги шаблонов?

Как видишь, в HTML нельзя помещать код Python, поскольку браузеры не понимают его. Они знают только HTML. Мы помним, что HTML статичен, в то время как Python позволяет делать динамические изменения.

**Теги шаблонов Django** позволяют нам вставлять Python в HTML, так что ты можешь создавать динамические веб-сайты быстрее и проще. То что надо!

## Отображаем шаблон списка записей

В предыдущей главе мы передали нашему шаблону список записей в переменной `posts`. Теперь мы отобразим его в HTML.

Чтобы вставить переменную в шаблон Django, нам нужно использовать двойные фигурные скобочки с именем переменной внутри:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
{{ posts }}
```

Попробуй это в шаблоне `blog/templates/blog/post_list.html`. Открой это в редакторе кода и замени все со второй `<div>` до третьего `</div>` на `{{ posts }}`. Сохрани файл и обнови страницу, чтобы увидеть результат:

![Рисунок 13.1](images/step1.png)

Как ты можешь заметить, мы получили следующую строку:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<QuerySet [<Post: My second post>, <Post: My first post>]>
```

Это показывает, что Django понял переменную как список объектов. Помнишь из главы **Введение в Python** как мы можем аккуратно отобразить список? Правильно, циклом for! В шаблонах Django ты можешь использовать их таким образом:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
{% for post in posts %}
    {{ post }}
{% endfor %}
```

Попробуй вставить это в свой шаблон.

![Рисунок 13.2](images/step2.png)

Сработало! Но мы хотим, чтобы они отображались как статические записи, которые мы создавали в главе **Введение в HTML**. ты можешь смешивать HTML и теги шаблонов. Наш элемент `body` будет выглядеть следующим образом:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<header>
    <h1><a href="/">Django Girls Blog</a></h1>
</header>

{% for post in posts %}
    <article>
        <time>published: {{ post.published_date }}</time>
        <h2><a href="">{{ post.title }}</a></h2>
        <p>{{ post.text|linebreaksbr }}</p>
    </article>
{% endfor %}
```

{% raw %}Всё что ты поместишь между `{% for %}` и `{% endfor %}` будет повторено для каждого объекта в списке. Обнови страницу:{% endraw %}

![Рисунок 13.3](images/step3.png)

Ты заметила, что мы использовали немного другую запись в этот раз `{{ post.title }}` или `{{ post.text }}`)? Мы обращаемся к различным полям нашей модели `Post`. Также `|linebreaks` прогоняет текст через фильтр, для преобразования переносов строк в параграфы.

## Еще один момент

Пришло время еще раз убедиться, что наш сайт будет работать в сети, согласна? Попробуем развернуть новую версию сайта на PythonAnywhere. Краткий обзор необходимых шагов...

* Сначала загрузи свой код на GitHub

{% filename %}command-line{% endfilename %}

    $ git status
    [...]
    $ git add .
    $ git status
    [...]
    $ git commit -m "Modified templates to display posts from database."
    [...]
    $ git push
    

* Затем заходим на [PythonAnywhere](https://www.pythonanywhere.com/consoles/), открываем **Bash console** и набираем команду:

{% filename %}PythonAnywhere command-line{% endfilename %}

    $ cd ~/<your-pythonanywhere-domain>.pythonanywhere.com
    $ git pull
    [...]
    

(Не забудьте заменить `<your-pythonanywhere-domain>` на ваше имя пользователя PythonAnywhere, без угловых скобок.)

* Наконец, переключись на вкладку [Web](https://www.pythonanywhere.com/web_app_setup/) и нажми кнопку **Reload**. (Чтобы перейти на другие страницы PythonAnywhere из консоли, используйте кнопку меню в верхнем правом углу.) Ваше обновление должно быть доступно на https://subdomain.pythonanywhere.com - проверьте его в браузере! Если сообщения в блоге на сайте PythonAnywhere не соответствуют сообщениям, появляющимся на блоге, размещенном на локальном сервере, то это нормально. Базы данных на локальном компьютере и на PythonAnywhere не синхронизируются с остальными вашими файлами.

Поздравляем! Теперь иди вперед и попробуй добавить новую должность в Django admin (не забудь добавить published_date!) Убедись, что ты находишься на Django admin для твоего сайта pythonanywhere, https://subdomain.pythonanywhere.com/admin. Затем обнови свою страницу, чтобы увидеть, появляется ли там сообщение.

Работает восхитительно? Мы гордимся тобой! Отойди от компьютера немного - ты заработала перерыв. 

![Рисунок 13.4](images/donut.png)