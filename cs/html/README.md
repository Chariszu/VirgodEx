# Úvod do HTML

Co je to šablona, se ami ptáš?

A template is a file that we can re-use to present different information in a consistent format – for example, you could use a template to help you write a letter, because although each letter might contain a different message and be addressed to a different person, they will share the same format.

A Django template's format is described in a language called HTML (that's the HTML we mentioned in the first chapter, **How the Internet works**).

## Co je HTML?

HTML is a code that is interpreted by your web browser – such as Chrome, Firefox or Safari – to display a web page for the user.

HTML je zkratka od "HyperText Markup Language". **HyperText** znamená, že je to typ textu, který podporuje hypertextové odkazy mezi stránkami. **Markup** znamená, že jsme vzali dokument a označili ho kódem, abychom něčemu (v tomto případě prohlížeči) řekli, jak interpretovat stránku. HTML kód se vytváží pomocí **tagů**. Každý začíná znakem `<` a končí znakem `>`. Tyto tagy representují **elementy** značkovacího jazyka (Markup.

## Tvá první šablona!

Vytvoření šablony znamená vytvoření souboru šablony. Všechno je soubor, dobře? Toho sis už asi všimla.

Šablony jsou uloženy v adresáři `blog/templates/blog`. Takže nejdříve vytvoř adresář `templates` uvnitř tvé blog složky. Potom vytvoř další složku nazvanou `blog` uvnitř templates složky:

    blog
    └───templates
        └───blog
    

(You might wonder why we need two directories both called `blog` – as you will discover later, this is simply a useful naming convention that makes life easier when things start to get more complicated.)

A teď vytvoř soubor `post_list.html` (pro teď ho nech prázdný) uvnitř adresáře `blog/templates/blog`.

Podívej se jak tvá stránka vypadá teď: http://127.0.0.1:8000/

> Pokud se ti stále zobrazuje chyba`TemplateDoesNotExists`, zkus restartovat server. Go into command line, stop the server by pressing Ctrl+C (Control and C keys together) and start it again by running a `python manage.py runserver` command.

![Figure 11.1](images/step1.png)

Žádná chybová hláška! Gratulujeme :) Nicméně, na tvé stránce se ještě nezveřejnilo nic kromě prázdné stránky, protože tvá šablona je také prázdná. To musíme napravit.

Do souboru šablony (template) přidej následující:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<html>
    <p>Hi there!</p>
    <p>It works!</p>
</html>
```

So how does your website look now? Visit it to find out: http://127.0.0.1:8000/

![Figure 11.2](images/step3.png)

Fungovalo to! Pěkná práce :)

* The most basic tag, `<html>`, is always the beginning of any web page and `</html>` is always the end. Jak vidíš, celý obsah stránky je mezi otevíracím tagem `<html>` a zavíracím tagem `</html>`
* `<p>` je tag pro element paragraf; `</p>` každý paragraf ukončuje

## Head and body

Každá HTML stránka je také rozdělena na dva elementy: **head** (hlavu) a **body** (tělo.

* **head** je element, který obsahuje informace o dokumentu, které se nezobrazují na webu.

* **body** je element který obsahuje vše ostatní, co se zobrazuje jakou součást webové stránky.

`<head>` používáme abychom prohlížeči sdělili konfiguraci stránky, `<body>` abychom sdělili co na té stránce skutečně je.

For example, you can put a web page title element inside the `<head>`, like this:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
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

Ulož soubor a načti znovu svou stránku.

![Figure 11.3](images/step4.png)

Všimla sis, že prohlížeč už ví, že "Ola's blog" je titulek stránky? Interpretoval `<title>Ola's blog</title>` a umístil text jako název záložky.

Pravděpodobně jsi si také všimla, že každý otevírací tag je doplněn *zavíracím tagem* se znakem `/`, a že elementy jsou *vnořené* (tzn. že nemůžeš zavřít daný tag dokud nejsou zavřeny všechny tagy uvnitř).

Je to jako dávat věci do krabic. Máš jednu velkou krabici, `<html></html>`; uvnitř je `<body></body>`, A ta obsahuje další, menší krabice: `<p></p>`.

You need to follow these rules of *closing* tags, and of *nesting* elements – if you don't, the browser may not be able to interpret them properly and your page will display incorrectly.

## Přizpůsob si šablonu

Teď si můžeš užít trochu zábavy a pokusit se přizpůsobit si svou šablonu! Tady je pár užitečných tagů:

* `<h1>A heading</h1>` for your most important heading
* `<h2>Pod-nadpis</h2>` pro nadpis na nižší úrovni
* `<h3>A sub-sub-heading</h3>` …and so on, up to `<h6>`
* `<p>A paragraph of text</p>`
* `<em>text</em>` zvýrazňuje tvůj text
* `<strong>text</strong>` hodně zvýrazňuje tvůj text
* `<br>` goes to another line (you can't put anything inside br and there's no closing tag)
* `<a href="https://djangogirls.org">link</a>` vytváří odkaz
* `<ul><li>První položka seznamu</li><li>second item</li></ul>` vytváří seznam, zrovna jako tento!
* `<div></div>` definuje sekce stránky

Here's an example of a full template, copy and paste it into `blog/templates/blog/post_list.html`:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<html>
    <head>
        <title>Django Girls blog</title>
    </head>
    <body>
        <div>
            <h1><a href="/">Django Girls Blog</a></h1>
        </div>

        <div>
            <p>published: 14.06.2014, 12:14</p>
            <h2><a href="">My first post</a></h2>
            <p>Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.</p>
        </div>

        <div>
            <p>published: 14.06.2014, 12:14</p>
            <h2><a href="">Můj druhý příspěvek</a></h2>
            <p>Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut f.</p>
        </div>
    </body>
</html>
```

Tady vytvoříme tři `div` sekce.

* The first `div` element contains the title of our blog – it's a heading and a link
* Další dva `div` elementy obsahují naše příspěvky s datem zveřejnění, na `h2` s titulkem příspěvku se dá kliknout a dva `p` (paragrafy) obsahují text, jeden datum a druhý samotný příspěvek.

To nám dá následující efekt:

![Figure 11.4](images/step6.png)

Jupííí! But so far, our template only ever displays exactly **the same information** – whereas earlier we were talking about templates as allowing us to display **different** information in the **same format**.

What we really want to do is display real posts added in our Django admin – and that's where we're going next.

## Ještě jedna věc: nasaďme to!

Bylo by fajn vidět všecho tohle venku a živé na internetu, že jo? Pojďme udělat další PythonAnywhere nasazení (deploy):

### Commitni, a pushni svůj kód na Github

Nejdříve se podívejme které soubory se změnily od posledního nasazení (deploy). Zadej tyto příkazy lokálně (ne na PythonAnywhere):

{% filename %}command-line{% endfilename %}

    $ git status
    

Ujisti se, že jsi v `djangogirls` adresáři a řekni `gitu`, ať zahrne všechny nové změny v adresáři:

{% filename %}command-line{% endfilename %}

    $ git add --all .
    

> **Note** `--all` means that `git` will also recognize if you've deleted files (by default, it only recognizes new/modified files). Taky si vzpomeň (ze 3. kapitoly), že `.` znamená aktuální adresář.

Než nahrajeme všechny soubory, zkontrolujme co bude `git` nahrávat (všechny soubory, které bude `git` nahrávat, se zobrazí zeleně):

{% filename %}command-line{% endfilename %}

    $ git status
    

Jsme skoro u konce, teď je čas uložit změny do historie. Vytvoříme "commit zprávu" kde popíšeme co jsme změnili. Můžeš napsat cokoli tě napadne, ale je užitečné napsat něco popisného, aby sis v budoucnosti mohla vzpomenout cos udělala.

{% filename %}command-line{% endfilename %}

    $ git commit -m "Změněn HTML kód stránek."
    

> **Poznámka** Ujisti se, že používáš dvojité uvozovky kolem zprávy.

Once we've done that, we upload (push) our changes up to GitHub:

{% filename %}command-line{% endfilename %}

    $ git push
    

### Stáhni svůj nový kód na PythonAnywhere a načti webovou aplikaci

* Otevři [stránku s konzolí na PythonAnywhere](https://www.pythonanywhere.com/consoles/) a jdi do své **Bash konzole** (nebo začni novou). Potom zadej:

{% filename %}command-line{% endfilename %}

    $ cd ~/my-first-blog
    $ git pull
    [...]
    

A sleduj svůj kód jak se stahuje. Pokud si chceš zkontrolovat, že se kód opravdu nahrál, můžeš skočit do záložky **Files** a podívat se na svůj kód na PythonAnywhere.

* A konečně, skoč na záložku [Web](https://www.pythonanywhere.com/web_app_setup/) a klikni na **Reload** (Znovu načíst).

Obnov svou stránku v prohlížeči. Měla bys vidět změny. :)