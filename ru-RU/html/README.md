# Введение в HTML

Так что же это за шаблон, ты можешь спросить.

Шаблон -- это файл, который мы можем использовать повторно для отображения различной информации в заданном формате, например, ты можешь использовать шаблон, чтобы упростить написание письма, поскольку письма хоть и различаются по содержанию и получателю, но сохраняют общую структуру.

Шаблоны в Django написаны на языке, называемом HTML (это тот HTML, о котором было упоминание в первой главе **Как работает Интернет**).

## Что такое HTML?

HTML -- это простой код, который может быть интерпретирован твоим браузером -- таким как Chrome, Firefox или Safari -- чтобы отобразить веб-страницу пользователю.

HTML (от англ. "HyperText Markup Language") - язык гипертекстовой разметки. **Гипертекст** - это тип текста, поддерживающий гиперссылки между страницами. Под **Разметкой** понимается введение в документ кода, который будет сообщать браузеру как правильно отобразить страницу. HTML код строится при помощи **тегов**, каждый из которых начинается символом `<` и заканчивается - `>`. Эти теги представляют **элементы** разметки.

## Твой первый шаблон!

Создание шаблона означает создание файла шаблона. Все есть файл, верно? Ты уже заметила это, наверно.

Шаблоны сохраняются в директории `blog/templates/blog`. Для начала создай директорию `templates` внутри папки blog. Затем создай другую директорию `blog` внутри папки templates:

    blog
    └───templates
        └───blog
    

(Ты, вероятно, можешь задаться вопросом: зачем нам нужны две директории с одинаковым названием `blog` - как ты узнаешь позже, это просто удобное соглашение об именовании, которое делает жизнь проще, когда вещи серьезно усложняются.)

Теперь создай файл `post_list.html` (для начала оставь его пустым) внутри директории `blog/templates/blog`.

Посмотри как выглядит твой веб-сайт после этого: http://127.0.0.1:8000/

> Если возникает ошибка `TemplateDoesNotExist`, попробуй перезапустить сервер. Перейди в командную строку, останови веб-сервер нажатием Ctrl+C (Ctrl и С одновременно) и запусти его снова командой `python manage.py runserver`.

![Рисунок 11.1](images/step1.png)

Ошибки больше нет! Молодец! :) Однако, твой сайт пока отображает пустую страницу, так как твой шаблон пуст. Нужно это исправить.

Открой новый файл в текстовом редакторе и добавь следующее:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<!DOCTYPE html>
<html>
<body>
    <p>Hi there!</p>
    <p>It works!</p>
</body>
</html>
```

Как теперь выглядит твой веб-сайт? Перейди сюда, чтобы узнать: http://127.0.0.1:8000/

![Рисунок 11.2](images/step3.png)

Сработало. Хорошо постаралась! :)

* The line `<!DOCTYPE html>` is not a HTML tag. It only declares the document type. Here, it informs the browser that document type is [HTML5](https://html.spec.whatwg.org/#the-doctype). This is always the beginning of any HTML5 file.
* The most basic tag, `<html>`, is always the beginning of html content and `</html>` is always the end. As you can see, the whole content of the website goes between the beginning tag `<html>` and closing tag `</html>`
* `<p>` is a tag for paragraph elements; `</p>` closes each paragraph

## Head и body

Каждая HTML-страница также делится на два элемента: **head** и **body**.

* **head** -- это элемент, содержащий информацию о документе, которая не отображается на экране.

* **body** -- это элемент, который содержит все, что будет отражено на веб-странице.

Мы используем тег `<head>` чтобы сообщить браузеру о настройках страницы и тег `<body>` - о её содержимом.

Например, ты можешь разместить заголовок веб-страницы между тегов `<head>`:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Ola's blog</title>
    </head>
    <body>
        <p>Hi there!</p>
        <p>It works!</p>
    </body>
</html>
```

Сохрани файл и обнови страницу.

![Рисунок 11.3](images/step4.png)

Видишь, как браузер понял, что "Ola's blog" -- это заголовок страницы? Он понял `<title>Ola's blog</title>` и разместил текст в заголовке вкладки в твоем браузере (заголовок также будет использоваться при сохранении закладок и т.п.).

Вероятно, ты уже заметила, что каждый открывающий тег имеет пару -- *закрывающий*, с символом `/`, элементы таким образом становятся *вложенными* (ты не можешь закрыть тег, пока остаются открытыми теги внутри него).

Это как складывать вещи в коробки. У нас есть одна большая коробка, `<html></html>`; внутри неё лежит коробка `<body></body>`, которая содержит еще меньшие коробки: `<p></p>`.

Ты должна следовать этим правилам *закрытия* тегов и *вложенности* элементов, если ты станешь их нарушать - браузер не сможет интерпретировать код и корректно отобразить страницу.

## Настраиваем шаблон

Ты можешь немного повеселиться сейчас и попробовать настроить шаблон по своему вкусу! Вот несколько полезных тегов:

* `<h1>Заголовок</h1>` - главный заголовок страницы
* `<h2>Подзаголовок</h2>` для заголовков второго уровня
* `<h3>Заголовок третьего уровня</h3>` ... и так далее, вплоть до `<h6>`
* `<p>Текстовый параграф</p>`
* `<em>текст</em>` подчеркивает твой текст
* `<strong>текст</strong>` - жирный шрифт
* `<br>` переход на следующую строку (внутрь br тега нельзя ничего поместить и закрывающий тег отсутствует)
* `<a href="https://djangogirls.org">link</a>` создает ссылку
* `<ul><li>первый элемент</li><li>второй элемент</li></ul>` создает список, такой же как этот!
* `<div></div>` определяет раздел страницы
* `<nav></nav>` defines a set of navigation links
* `<article></article>` specifies independent, self-contained content
* `<section></section>` defines a section in a document
* `<header></header>` specifies a header for a document or section
* `<main></main>` specifies the main content of a document
* `<aside></aside>` defines some content aside from the content it is placed in (like a sidebar)
* `<footer></footer>` defines a footer for a document or section
* `<time></time>` defines a specific time (or datetime)

Вот пример полного шаблона, скопируйте и вставьте его в `blog/templates/blog/post_list.html`:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Django Girls blog</title>
    </head>
    <body>
        <header>
            <h1><a href="/">Django Girls Blog</a></h1>
        </header>

        <article>
            <time>published: 14.06.2014, 12:14</time>
            <h2><a href="">My first post</a></h2>
            <p>Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.</p>
        </article>

        <article>
            <time>published: 14.06.2014, 12:14</time>
            <h2><a href="">My second post</a></h2>
            <p>Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut f.</p>
        </article>
    </body>
</html>
```

We've created one `header` section and two `article` section here.

* The `header` element contains the title of our blog – it's a heading and a link
* The two `article` elements contain our blog posts with a published date in a `time` element, a `h2` element with a post title that is clickable and a `p` (paragraph) element for text of our blog post.

Это даст нам следующий эффект:

![Рисунок 11.4](images/step6.png)

Ура! Однако, до сих пор наш шаблон отображал лишь **одну и ту же информацию** - тогда как раньше мы говорили, что шаблоны позволяют нам отображать **различную** информацию в **одном и том же формате**.

Что мы действительно хотим - это отображать существующие записи, добавленные через панель администратора Django, этим и займемся в следующий раз.

## И ещё кое-что: публикация!

Хотелось бы увидеть все это в живую в интернете, согласна? Давай проведем еще одно развертывание веб-сайта на PythonAnywhere:

### Commit и push кода в репозиторий Github

Во-первых, давай посмотрим, какие файлы были изменены с момента последнего развертывания (выполни эти команды локально, не на PythonAnywhere):

{% filename %}command-line{% endfilename %}

    $ git status
    

Убедись, что находишься в директории `djangogirls` и сообщи `git` выбрать все изменения в пределах этой папки:

{% filename %}command-line{% endfilename %}

    $ git add
    

Прежде чем мы загрузим файлы, давай проверим, что именно `git` будет загружать (все файлы, который `git` готов отправить на сервер отмечаются шрифтом зеленого цвета):

{% filename %}command-line{% endfilename %}

    $ git status
    

Мы почти у цели, пришло время сохранить изменения в истории. К сохраняемой версии мы приложим небольшое сообщение, в котором кратко опишем изменения. Можешь набрать в качестве сообщения все что захочешь, однако, полезно выбирать информативную запись, так будет проще вспомнить внесенные изменения в будущем.

{% filename %}command-line{% endfilename %}

    $ git commit -m "Changed the HTML for the site."
    

> **Примечание** Убедись, что оборачиваешь комментарий в двойные кавычки. 

После того, как мы сделали это, мы загрузим (сделаем push) изменения на Github:

{% filename %}command-line{% endfilename %}

    $ git push
    

### Загружаем новый код на PythonAnywhere и перезапускаем веб-приложение

* Открой вкладку ["терминалы"](https://www.pythonanywhere.com/consoles/) на PythonAnywhere и переключись на уже запущенную **консоль Bash** (или новую). Затем набери следующую команду:

{% filename %}PythonAnywhere command-line{% endfilename %}

    $ cd ~/<your-pythonanywhere-domain>.pythonanywhere.com
    $ git pull
    [...]
    

Не забудьте заменить `<your-pythonanywhere-domain>` на ваше имя пользователя PythonAnywhere, без угловых скобок. Ваше имя поддомена обычно является вашим именем пользователя на PythonAnywhere но в некоторых случаях оно может немного отличаться (например, если ваше имя пользователя содержит заглавные буквы). Так что если эта команда не работает, используйте команду `ls` (файлы списка) чтобы найти ваше фактическое имя поддомена/папки, а затем `cd` туда.

Теперь наблюдайте как ваш код загружается. Если хочешь проверить, загрузился ли он, можешь перейти в **"Files" page** и посмотреть свой код на PythonAnywhere (можешь также переходить на другие страницы PythonAnywhere из кнопки меню на странице с консолью).

* Наконец, переключись на вкладку [Web](https://www.pythonanywhere.com/web_app_setup/) и нажми кнопку **Reload** на своем веб-приложении.

Обновления должны отобразиться на веб-сайте! Переключись на него и обнови страницу в браузере. Ты должна сразу заметить изменения. :)