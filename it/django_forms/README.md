# Form Django

Infine vogliamo creare un bel modo per poter aggiungere e cambiare in nostri blog posts. Django `admin` è bello, ma è alquanto difficile da personalizzare e rendere carino. With `forms` we will have absolute power over our interface – we can do almost anything we can imagine!

La bella cosa dei Django forms è che possiamo sia inventare un nuovo form da zero che creare un `ModelForm` che salverà il risultato del form sul nostro modello.

Questo è esattamente quello che stiamo per fare: stiamo per creare un form per il nostro modello dei `Post`.

Come ogni parte importante di Django, i forms hanno il proprio file: `forms.py`.

Dobbiamo creare un file con questo nome all'interno della cartella `blog`.

    blog
       └── forms.py
    

OK, let's open it and type the following code:

{% filename %}blog/forms.py{% endfilename %}

```python
from django import forms

from .models import Post

class PostForm(forms.ModelForm):

    class Meta:
        model = Post
        fields = ('title', 'text',)
```

Dobbiamo importare prima di tutto i Django Forms (`from django import forms`) e, ovviamente, il nostro `Post` model (`from .models import Post`).

`PostForm`, come probabilmente hai intuito, è nome del nostro form. We need to tell Django that this form is a `ModelForm` (so Django will do some magic for us) – `forms.ModelForm` is responsible for that.

Successivamente, abbiamo `class Meta`, con cui diciamo a Django quale model utilizzare per creare questo form (`model = Post`).

Finalmente, possiamo indicare uno o più campi che il nostro form deve avere. In this scenario we want only `title` and `text` to be exposed – `author` should be the person who is currently logged in (you!) and `created_date` should be automatically set when we create a post (i.e. in the code), right?

E questo è tutto! Tutto quello che dobbiamo fare ora é usare il form nella nostra *view* e visualizzarlo nel template.

So once again we will create a link to the page, a URL, a view and a template.

## Link ad una pagina usando il form

È tempo di aprire `blog/templates/blog/base.html`. Aggiungeremo un link nel `div` chiamato `page-header`:

{% filename %}blog/templates/blog/base.html{% endfilename %}

```html
<a href="{% url 'post_new' %}" class="top-menu"><span class="glyphicon glyphicon-plus"></span></a>
```

Nota che noi vogliamo chiamare la nostra vista `post_new`. La classe `"glyphicon glyphicon-plus"` è data dal tema di bootstrap che stiamo usando e visualizzerà un segno più per noi.

After adding the line, your HTML file should now look like this:

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
            <a href="{% url 'post_new' %}" class="top-menu"><span class="glyphicon glyphicon-plus"></span></a>
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
</html>
```

Dopo aver salvato e aggiornato la pagina http://127.0.0.1:8000 vedrai ovviamente un errore familiare `NoReverseMatch`, giusto?

## URL

Apri il file `blog/urls.py` e aggiungi:

{% filename %}blog/urls.py{% endfilename %}

```python
url(r'^post/new/$', views.post_new, name='post_new'),
```

Il risultato finale sarà:

{% filename %}blog/urls.py{% endfilename %}

```python
from django.conf.urls import url
from . import views

urlpatterns = [
    url(r'^$', views.post_list, name='post_list'),
    url(r'^post/(?P<pk>\d+)/$', views.post_detail, name='post_detail'),
    url(r'^post/new/$', views.post_new, name='post_new'),
]
```

After refreshing the site, we see an `AttributeError`, since we don't have the `post_new` view implemented. Let's add it right now.

## post_new view

Apri il file `blog/views.py` e aggiungi quanto segue con il resto delle importazioni `from`:

{% filename %}blog/views.py{% endfilename %}

```python
from .forms import PostForm
```

And then our *view*:

{% filename %}blog/views.py{% endfilename %}

```python
def post_new(request):
    form = PostForm()
    return render(request, 'blog/post_edit.html', {'form': form})
```

Per creare un nuovo `Post` form, dobbiamo chiamare il metodo `PostForm()` e passarlo nel nostro template. We will go back to this *view*, but for now, let's quickly create a template for the form.

## Template

All'interno della cartella `blog/templates/blog` dobbiamo creare il file `post_edit.html`. Per far si che il nostro form funzioni abbiamo bisogno di diverse cose:

* We have to display the form. We can do that with (for example) {% raw %}`{{ form.as_p }}`{% endraw %}.
* Le righe scritte sopra hanno bisogno di 'essere avvolte' da un HTML tag: `<form method="POST">...</form>`.
* Ci serve un `Save` pulsante. Possiamo fare Ciò con HTML button: `<button type="submit">Save</button>`.
* And finally, just after the opening `<form ...>` tag we need to add {% raw %}`{% csrf_token %}`{% endraw %}. Questo passaggio è molto importante dal momento che rende il nostro form sicuro! If you forget about this bit, Django will complain when you try to save the form:

![CSFR Forbidden page](images/csrf2.png)

OK, so let's see how the HTML in `post_edit.html` should look:

{% filename %}blog/templates/blog/post_edit.html{% endfilename %}

```html
{% extends 'blog/base.html' %}

{% block content %}
    <h1>New post</h1>
    <form method="POST" class="post-form">{% csrf_token %}
        {{ form.as_p }}
        <button type="submit" class="save btn btn-default">Save</button>
    </form>
{% endblock %}
```

Ora aggiorna la pagina! Yeah! Puoi ora visualizzare il tuo form!

![New form](images/new_form2.png)

But, wait a minute! When you type something in the `title` and `text` fields and try to save it, what will happen?

Nothing! We are once again on the same page and our text is gone… and no new post is added. So what went wrong?

La risposta è: nulla. Dobbiamo solo fare un po' di lavoro in più nella nostra *view*.

## Salvare il form

Open `blog/views.py` once again. Currently all we have in the `post_new` view is the following:

{% filename %}blog/views.py{% endfilename %}

```python
def post_new(request):
    form = PostForm()
    return render(request, 'blog/post_edit.html', {'form': form})
```

When we submit the form, we are brought back to the same view, but this time we have some more data in `request`, more specifically in `request.POST` (the naming has nothing to do with a blog "post"; it's to do with the fact that we're "posting" data). Remember how in the HTML file, our `<form>` definition had the variable `method="POST"`? Per cui ora, tutto quello che l'utente ha inserito nel form è disponibile in `method="POST"`. Non è necessario rinominare `POST` in nessuna altra maniera (l'unico altro valore valido per `method` è `GET`, ma al momento non abbiamo abbastanza tempo per spiegare la differenza).

So in our *view* we have two separate situations to handle: first, when we access the page for the first time and we want a blank form, and second, when we go back to the *view* with all form data we just typed. Per cui dobbiamo aggiungere una condizione(useremo `if`):

{% filename %}blog/views.py{% endfilename %}

```python
if request.method == "POST":
    [...]
else:
    form = PostForm()
```

It's time to fill in the dots `[...]`. If `method` is `POST` then we want to construct the `PostForm` with data from the form, right? We will do that as follows:

{% filename %}blog/views.py{% endfilename %}

```python
form = PostForm(request.POST)
```

The next thing is to check if the form is correct (all required fields are set and no incorrect values have been submitted). We do that with `form.is_valid()`.

Se la forma viene ritenuta valida verrà salvata!

{% filename %}blog/views.py{% endfilename %}

```python
if form.is_valid():
    post = form.save(commit=False)
    post.author = request.user
    post.published_date = timezone.now()
    post.save()
```

In pratica, ci sono due cose da fare: salviamo il form con `form.save` e aggiungiamo un autore(dal momento che non c'era nessun campo autore `author` nel form `PostForm` e questo campo non può essere lasciato bianco). `commit=False` means that we don't want to save the `Post` model yet – we want to add the author first. Most of the time you will use `form.save()` without `commit=False`, but in this case, we need to supply it. `post.save()` will preserve changes (adding the author) and a new blog post is created!

Finally, it would be awesome if we could immediately go to the `post_detail` page for our newly created blog post, right? To do that we need one more import:

{% filename %}blog/views.py{% endfilename %}

```python
from django.shortcuts import redirect
```

Add it at the very beginning of your file. And now we can say, "go to the `post_detail` page for the newly created post":

{% filename %}blog/views.py{% endfilename %}

```python
return redirect('post_detail', pk=post.pk)
```

`post_detail` è il nome della vista su cui vogliamo andare. Ti ricordi che questa *view* ha bisogno della `pk` variabile? To pass it to the views, we use `pk=post.pk`, where `post` is the newly created blog post!

OK, we've talked a lot, but we probably want to see what the whole *view* looks like now, right?

{% filename %}blog/views.py{% endfilename %}

```python
def post_new(request):
    if request.method == "POST":
        form = PostForm(request.POST)
        if form.is_valid():
            post = form.save(commit=False)
            post.author = request.user
            post.published_date = timezone.now()
            post.save()
            return redirect('post_detail', pk=post.pk)
    else:
        form = PostForm()
    return render(request, 'blog/post_edit.html', {'form': form})
```

Vediamo se funziona. Go to the page http://127.0.0.1:8000/post/new/, add a `title` and `text`, save it… and voilà! The new blog post is added and we are redirected to the `post_detail` page!

You might have noticed that we are setting the publish date before saving the post. Later on, we will introduce a *publish button* in **Django Girls Tutorial: Extensions**.

Fantastico!

> As we have recently used the Django admin interface, the system currently thinks we are still logged in. There are a few situations that could lead to us being logged out (closing the browser, restarting the DB, etc.). If, when creating a post, you find that you are getting errors referring to the lack of a logged-in user, head to the admin page http://127.0.0.1:8000/admin and log in again. Questo risolverà temporaneamente il problema. C'è una correzione permanente che ti aspetta nella sezione degli esercizi extra alla fine del tutorial principale **Compiti: aggiungi sicurezza al tuo sito web!**.

![Logged in error](images/post_create_error.png)

## Validazione del form

E adesso ti dimostreremo quanto siano belli i form di Django. Sappiamo che un post ha bisogno di `title` e `text`. In our `Post` model we did not say that these fields (as opposed to `published_date`) are not required, so Django, by default, expects them to be set.

Try to save the form without `title` and `text`. Guess what will happen!

![Validazione del form](images/form_validation2.png)

Django is taking care to validate that all the fields in our form are correct. Isn't it awesome?

## Form di modifica

Ora sappiamo come aggiungere un form. Ma cosa succede se ne vogliamo cambiarne uno esistente? This is very similar to what we just did. Let's create some important things quickly. (If you don't understand something, you should ask your coach or look at the previous chapters, since we covered all these steps already.)

Open `blog/templates/blog/post_detail.html` and add the line

{% filename %}blog/templates/blog/post_detail.html{% endfilename %}

```html
<a class="btn btn-default" href="{% url 'post_edit' pk=post.pk %}"><span class="glyphicon glyphicon-pencil"></span></a>
```

so that the template will look like this:

{% filename %}blog/templates/blog/post_detail.html{% endfilename %}

```html
{% extends 'blog/base.html' %}

{% block content %}
    <div class="post">
        {% if post.published_date %}
            <div class="date">
                {{ post.published_date }}
            </div>
        {% endif %}
        <a class="btn btn-default" href="{% url 'post_edit' pk=post.pk %}"><span class="glyphicon glyphicon-pencil"></span></a>
        <h1>{{ post.title }}</h1>
        <p>{{ post.text|linebreaksbr }}</p>
    </div>
{% endblock %}
```

In `blog/urls.py` aggiugi:

{% filename %}blog/urls.py{% endfilename %}

```python
    url(r'^post/(?P<pk>\d+)/edit/$', views.post_edit, name='post_edit'),
```

Riutilizzeremo il model `blog/templates/blog/post_edit.html`, quindi l'ultima cosa che manca è una *view*.

Let's open `blog/views.py` and add this at the very end of the file:

{% filename %}blog/views.py{% endfilename %}

```python
def post_edit(request, pk):
    post = get_object_or_404(Post, pk=pk)
    if request.method == "POST":
        form = PostForm(request.POST, instance=post)
        if form.is_valid():
            post = form.save(commit=False)
            post.author = request.user
            post.published_date = timezone.now()
            post.save()
            return redirect('post_detail', pk=post.pk)
    else:
        form = PostForm(instance=post)
    return render(request, 'blog/post_edit.html', {'form': form})
```

Questo sembra quasi esattamente la view `post_new`, giusto? Ma non del tutto. For one, we pass an extra `pk` parameter from urls. Next, we get the `Post` model we want to edit with `get_object_or_404(Post, pk=pk)` and then, when we create a form, we pass this post as an `instance`, both when we save the form…

{% filename %}blog/views.py{% endfilename %}

```python
form = PostForm(request.POST, instance=post)
```

…and when we've just opened a form with this post to edit:

{% filename %}blog/views.py{% endfilename %}

```python
form = PostForm(instance=post)
```

OK, let's test if it works! Let's go to the `post_detail` page. There should be an edit button in the top-right corner:

![Edit button](images/edit_button2.png)

Quando ci clicchi, vedrai il modulo con i nostri post del blog:

![Form di modifica](images/edit_form2.png)

Feel free to change the title or the text and save the changes!

Complimenti! La tua application è sempre più completa!

If you need more information about Django forms, you should read the documentation: https://docs.djangoproject.com/en/1.11/topics/forms/

## Sicurezza

Riuscire a creare nuovi post semplicemente cliccando su un link è bellissimo! But right now, anyone who visits your site will be able to make a new blog post, and that's probably not something you want. Facciamo spuntare il bottone solo per te e non per gli altri.

Vai al tuo `blog/templates/blog/base.html` e trova il `page-header` `div` con il tag di tipo anchor che hai messo prima. Dovrebbe apparire così:

{% filename %}blog/templates/blog/base.html{% endfilename %}

```html
<a href="{% url 'post_new' %}" class="top-menu"><span class="glyphicon glyphicon-plus"></span></a>
```

We're going to add another `{% if %}` tag to this, which will make the link show up only for users who are logged into the admin. Right now, that's just you! Cambia il tag `<a>` in modo che risulti così:

{% filename %}blog/templates/blog/base.html{% endfilename %}

```html
{% if user.is_authenticated %}
    <a href="{% url 'post_new' %}" class="top-menu"><span class="glyphicon glyphicon-plus"></span></a>
{% endif %}
```

This `{% if %}` will cause the link to be sent to the browser only if the user requesting the page is logged in. Con questa condizione non ci siamo protetti del tutto dalla creazione di nuovi post, ma abbiamo fatto un buon passo avanti. Nelle lezioni estensione ci occuperemo di più della sicurezza.

Ricordi l'icona modifica che abbiamo aggiunto sulla nostra pagina di dettaglio? Vogliamo faro la stessa cosa qui, così le altre persone non potranno editare i post esistenti.

Open `blog/templates/blog/post_detail.html` and find this line:

{% filename %}blog/templates/blog/post_detail.html{% endfilename %}

```html
<a class="btn btn-default" href="{% url 'post_edit' pk=post.pk %}"><span class="glyphicon glyphicon-pencil"></span></a>
```

Change it to this:

{% filename %}blog/templates/blog/post_detail.html{% endfilename %}

```html
{% if user.is_authenticated %}
     <a class="btn btn-default" href="{% url 'post_edit' pk=post.pk %}"><span class="glyphicon glyphicon-pencil"></span></a>
{% endif %}
```

Siccome probabilmente sei loggata, se ricarichi la pagina non vedrai differenze. Load the page in a different browser or an incognito window (called "InPrivate" in Windows Edge), though, and you'll see that the link doesn't show up, and the icon doesn't display either!

## Ultima cosa: ora di fare il deploy!

Vediamo se funziona su PythonAnywhere. È l'ora di un altro deploy!

* Innanzitutto, fai un commit del tuo nuovo codice e fai il push per caricarlo su Github:

{% filename %}command-line{% endfilename %}

    $ git status
    $ git add --all .
    $ git status
    $ git commit -m "Added views to create/edit blog post inside the site."
    $ git push
    

* Poi, in una [console PythonAnywhere Bash](https://www.pythonanywhere.com/consoles/):

{% filename %}command-line{% endfilename %}

    $ cd my-first-blog
    $ git pull
    [...]
    

* Infine, vai sulla [Web tab](https://www.pythonanywhere.com/web_app_setup/) e premi **Reload**.

Fatto! Congratulazioni :)