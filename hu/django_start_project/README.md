# Az első Django projekted!

> Part of this chapter is based on tutorials by Geek Girls Carrots (https://github.com/ggcarrots/django-carrots).
> 
> Parts of this chapter are based on the [django-marcador tutorial](http://django-marcador.keimlink.de/) licensed under the Creative Commons Attribution-ShareAlike 4.0 International License. A django-marcador tutorial jogait, Markus Zapke-Gründemann és társai birtokolják.

We're going to create a small blog!

Az első lépés, hogy indítsunk egy új Django projektet. Ez annyit jelent, hogy lefuttatunk néhány scriptet, amit a Django tartalmaz, ezzel létrehozzuk a projekt vázát. Ez tulajdonképpen néhány mappa és fájl, amit majd később fogunk használni.

Néhány fájl és könyvtár neve nagyon fontos a Django-ban. A fájlokat, amiket most hozunk létre, ne nevezd át! Az áthelyezésük sem egy jó ötlet. Fontos, hogy megtartsunk egy bizonyos szerkezetet, ami segít a Django-nak, hogy megtalálja a fontos dolgokat.

> Figyelem: mindent a virtualenv-ben futtass. If you don't see a prefix `(myvenv)` in your console, you need to activate your virtualenv. Ezt a **Django telepítés** fejezetben írtuk le, a **Virtuális környezetben való fejlesztés** résznél. Typing `myvenv\Scripts\activate` on Windows or `source myvenv/bin/activate` on Mac OS X or Linux will do this for you.

<!--sec data-title="Create project: OS X or Linux" data-id="django_start_project_OSX_Linux" data-collapse=true ces-->

In your Mac OS X or Linux console, you should run the following command. **Don't forget to add the period (or dot) `.` at the end!**

{% filename %}command-line{% endfilename %}

    (myvenv) ~/djangogirls$ django-admin startproject mysite .
    

> The period `.` is crucial because it tells the script to install Django in your current directory (for which the period `.` is a short-hand reference).
> 
> **Note** When typing the command above, remember that you only type the part which starts by `django-admin`. The `(myvenv) ~/djangogirls$` part shown here is just example of the prompt that will be inviting your input on your command line.

<!--endsec-->

<!--sec data-title="Create project: Windows" data-id="django_start_project_windows" data-collapse=true ces-->

On Windows you should run the following command. **(Don't forget to add the period (or dot) `.` at the end)**:

{% filename %}command-line{% endfilename %}

    (myvenv) C:\Users\Name\djangogirls> django-admin.exe startproject mysite .
    

> The period `.` is crucial because it tells the script to install Django in your current directory (for which the period `.` is a short-hand reference).
> 
> **Note** When typing the command above, remember that you only type the part which starts by `django-admin.exe`. The `(myvenv) C:\Users\Name\djangogirls>` part shown here is just example of the prompt that will be inviting your input on your command line.

<!--endsec-->

A `django-admin.py` egy script, ami könyvtárakat és fájlokat hoz létre neked. Most ilyen könyvtárszerkezetednek kell lennie:

    djangogirls
    ├───manage.py
    └───mysite
            settings.py
            urls.py
            wsgi.py
            __init__.py
    

> **Note**: in your directory structure, you will also see your `venv` directory that we created before.

`manage.py` is a script that helps with management of the site. With it we will be able (amongst other things) to start a web server on our computer without installing anything else.

A `settings.py` tartalmazza a weboldalat konfigurációját (beállításait),.

Remember when we talked about a mail carrier checking where to deliver a letter? `urls.py` file contains a list of patterns used by `urlresolver`.

Most ne foglalkozzunk a többi fájllal, mert azokat nem fogjuk módosítani. Az egyetlen dolog, amit ne felejts el, hogy ne töröld ki őket véletlenül!

## A beállítások megváltoztatása

Változtassunk meg néhány dolgot a `mysite/settings.py` fájlban. Nyisd meg a fájlt a kódszerkesztővel, amit korábban telepítettél!

**Note**: Keep in mind that `settings.py` is a regular file, like any other. You can open it from inside the code editor, using the "file -> open" menu actions. This should get you the usual window in which you can navigate to your `settings.py` file and select it. Alternatively, you can open the file by navigating to the djangogirls folder on your desktop and right-clicking on it. Then, select your code editor from the list. Selecting the editor is important as you might have other programs installed that can open the file but will not let you edit it.

Jó lenne, ha a weboldalunk a mi időzónánk szerinti időt mutatná. Go to [Wikipedia's list of time zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) and copy your relevant time zone (TZ) (e.g. `Europe/Berlin`).

In `settings.py`, find the line that contains `TIME_ZONE` and modify it to choose your own timezone. For example:

{% filename %}mysite/settings.py{% endfilename %}

```python
TIME_ZONE = 'Europe/Berlin'
```

A language code consist of the language, e.g. `en` for english or `de` for german, and the country code, e.g. `de` for germany or `ch` for switzerland. You will want to add this if you want the default buttons and notifications from Django to be in your language. So you would have "Cancel" button translated into the language you defined here. [Django comes with a lot of prepared translations](https://docs.djangoproject.com/en/1.11/ref/settings/#language-code).

Change the language code by changing the following line:

{% filename %}mysite/settings.py{% endfilename %}

```python
LANGUAGE_CODE = 'de-ch'
```

We'll also need to add a path for static files. (We'll find out all about static files and CSS later in the tutorial.) Go down to the *end* of the file, and just underneath the `STATIC_URL` entry, add a new one called `STATIC_ROOT`:

{% filename %}mysite/settings.py{% endfilename %}

```python
STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR, 'static')
```

When `DEBUG` is `True` and `ALLOWED_HOSTS` is empty, the host is validated against `['localhost', '127.0.0.1', '[::1]']`. This won't match our hostname on PythonAnywhere once we deploy our application so we will change the following setting:

{% filename %}mysite/settings.py{% endfilename %}

```python
ALLOWED_HOSTS = ['127.0.0.1', '.pythonanywhere.com']
```

> **Note**: If you're using a Chromebook, add this line at the bottom of your settings.py file: `MESSAGE_STORAGE = 'django.contrib.messages.storage.session.SessionStorage'`
> 
> Also add `.c9users.io` to the `ALLOWED_HOSTS` if you are using cloud9

## Set up a database

Sok különféle adatbázis-szoftver létezik, ami adatokat tud tárolni a weboldalakhoz. Mi az alapértelmezettet fogjuk használni, az `sqlite3`-ot.

Ez már be van állítva a `mysite/settings.py` fájlodban:

{% filename %}mysite/settings.py{% endfilename %}

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}
```

Hogy létrehozz egy adatbázist a blogodhoz, futtasd le a következő parancsot a konzolban: `python manage.py migrate` (fontos, hogy a `djangogirls` könyvtárban legyél, ami tartalmazza a `djangogirls` fájlt). Ha minden jól megy, valami ilyesmit kell látnod:

{% filename %}command-line{% endfilename %}

    (myvenv) ~/djangogirls$ python manage.py migrate
    Operations to perform:
      Apply all migrations: auth, admin, contenttypes, sessions
    Running migrations:
      Rendering model states... DONE
      Applying contenttypes.0001_initial... OK
      Applying auth.0001_initial... OK
      Applying admin.0001_initial... OK
      Applying admin.0002_logentry_remove_auto_add... OK
      Applying contenttypes.0002_remove_content_type_name... OK
      Applying auth.0002_alter_permission_name_max_length... OK
      Applying auth.0003_alter_user_email_max_length... OK
      Applying auth.0004_alter_user_username_opts... OK
      Applying auth.0005_alter_user_last_login_null... OK
      Applying auth.0006_require_contenttypes_0002... OK
      Applying auth.0007_alter_validators_add_error_messages... OK
      Applying sessions.0001_initial... OK
    

Készen is vagyunk! Itt az ideje, hogy elindítsd a webszervert, és meglásd, hogy működik-e.

## Starting the web server

Ehhez abban a könyvtárban kell lenned, ahol a `manage.py` fájl van (a `djangogirls` könyvtárban). A konzolban a következő paranccsal tudod elindítani a szervert: `python manage.py runserver`.

{% filename %}command-line{% endfilename %}

    (myvenv) ~/djangogirls$ python manage.py runserver
    

If you are on a Chromebook, use this command instead:

{% filename %}Cloud 9{% endfilename %}

    (myvenv) ~/djangogirls$ python manage.py runserver 0.0.0.0:8080
    

Ha Windowst használsz, és `UnicodeDecodeError` hibaüzenetet kapsz, ezt a parancsot használd:

{% filename %}command-line{% endfilename %}

    (myvenv) ~/djangogirls$ python manage.py runserver 0:8000
    

Now all you need to do is check that your website is running. Open your browser (Firefox, Chrome, Safari, Internet Explorer or whatever you use) and enter this address:

{% filename %}browser{% endfilename %}

    http://127.0.0.1:8000/
    

If you're using a Chromebook, you'll always visit your test server by accessing:

{% filename %}browser{% endfilename %}

    https://django-girls-<your cloud9 username>.c9users.io
    

Gratulálunk! Létrehoztad az első weboldaladat, és futtatad is egy webszerver segítségével! Nem fantasztikus?

![It worked!](images/it_worked2.png)

While the web server is running, you won't see a new command-line prompt to enter additional commands. The terminal will accept new text but will not execute new commands. This is because the web server continuously runs in order to listen for incoming requests.

> We reviewed how web servers work in the **How the Internet works** chapter.

To type additional commands while the web server is running, open a new terminal window and activate your virtualenv. To stop the web server, switch back to the window in which it's running and press CTRL+C - Control and C keys together (on Windows, you might have to press Ctrl+Break).

Készen állsz a következő lépésre? Itt az ideje, hogy létrehozzunk némi tartalmat!