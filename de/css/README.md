# CSS - mach es hübsch!

Unser Blog sieht immer noch ziemlich unfertig aus, oder? Zeit das zu ändern! Dafür nutzen wir CSS.

## Was ist CSS?

Cascading Style Sheets (CSS) ist eine Sprache, die das Aussehen und die Formatierung einer Website beschreibt. Es handelt sich wie bei HTML um eine Auszeichnungssprache (Markup Language). Sie ist sowas wie das "Make-up" unserer Website. ;)

Aber wir wollen nicht nochmal bei Null anfangen, oder? Einmal mehr werden wir etwas verwenden, dass ProgrammiererInnen entwickelt haben und gratis im Internet zur Verfügung stellen. Wir wollen ja nicht das Rad neu erfinden.

## Lass uns Bootstrap verwenden!

Bootstrap ist eines der bekanntesten HTML- und CSS-Frameworks für die Entwicklung von schönen Websites: https://getbootstrap.com/

Es wurde ursprünglich von ProgrammiererInnen bei Twitter geschrieben. Heute wird es von Freiwilligen aus der ganzen Welt weiterentwickelt!

## Bootstrap installieren

Um Bootstrap zu installieren, müssen Sie das hinzufügen, um Ihre `<head>`in Ihre `Html`-Datei:

{% filename %}blog/templates/blog/post_list{% endfilename %}

```html
<link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css">
<link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css">
```

Dies fügt deinem Projekt keine Dateien hinzu. Es verweist nur auf Dateien, die im Internet vorhanden sind. Öffne und aktualisiere deine Webseite. Da ist sie!

![Abbildung 14.1](images/bootstrap1.png)

Sie sieht jetzt schon viel schöner aus!

## Statische Dateien in Django

Schlussendlich werden wir einen genaueren Blick auf die Dinge werfen, die wir bisher **statische Dateien** genannt haben. Statische Dateien sind alle deine CSS- und Bilddateien. Ihr Inhalt hängt nicht vom Requestkontext ab sondern gilt für alle Benutzer gleichermassen.

### Wohin kommen die statischen Dateien für Django

Django weiss schon wo die statischen Dateien für die integrierte "admin" App zu finden sind. Wir müssen nur noch die statischen Dateien für unsere `blog` App hinzufügen.

Dies tun wir, indem wir einen Ordner namens `static` in der Blog-App erstellen:

    djangogirls
    ├── blog
    |     ├── migrationen
    |     ├── statisch
    |     └── vorlagen
    └── meineseite
    

Django findet automatisch jede datei mit dem namen "static" in jeder ihrer apps ordner. Danach wird er in der lage sein ihr Inhalt als statische dateien zu benutzen.

## Deine erste CSS-Datei!

Lassen Sie uns jetzt eine CSS-Datei erstellen, um einen eigenen Stil zu Ihrer Webseite hinzuzufügen. Erstelle ein neues Verzeichnis namens `css` in deinem `static`-Verzeichnis. Dann erstelle eine neue Datei namens `blog.css` in diesem `css`-Verzeichnis. Fertig?

    djangogirls
    └─── blog
         └─── static
              └─── css
                   └─── blog.css
    

Zeit ein wenig CSS zu schreiben! Öffne die `blog/static/css/blog.css` Datei in Deinem Code-Editor.

We won't be going too deep into customizing and learning about CSS here. There is a recommendation for a free CSS course at the end of this page if you would like to learn more.

Aber lass uns wenigstens etwas Kleines probieren. Beispielsweise könnten wir die Farbe unserer Kopfzeile ändern. Computer benutzen spezielle Codes, um Farben zu verstehen. Diese Codes beginnen mit `#` gefolgt von 6 Buchstaben (A-F) und nummern (0-9). Blau zum Beispiel ist `#0000FF`. Beispiele für solche Farbcodes findest Du hier: http://www.colorpicker.com/. Du kannst auch [vordefinierte Farben](http://www.w3schools.com/colors/colors_names.asp) wie `red` und `green` benutzen.

In deiner `blog/static/css/blog.css` Datei änderst du den folgenden Code:

{% filename %}blog/static/css/blog.css{% endfilename %}

```css
h1 a {
color: #FCA205;
}
```

`h1 a` ist ein CSS-Selektor. Das bedeutet, sass wir unsere Styles auf alle `a` Elemente innerhalb von einem `h1` Element anwenden. Also wenn wir so etwas wie `<h1><a href="">link</a></h1>`, der `h1 a` stil wird gelten. In diesem Fall sagen wir, dass es seine Farbe in `#FCA205` ändern soll, was für Orange steht. Du kannst hier natürlich deine eigene Farbe angeben!

In einer CSS-Datei werden Stile für Elemente der HTML-Datei festgelegt. Ein Weg HTML-Elemente zu identifizieren ist der Name des Elements. Du erinnerst dich vielleicht an diese Namen als 'Tags' aus dem HTML Kapitel. Zum Beispiel sind `a`, `h1` und `body` solche Elementnamen. Wir identifizieren Elemente auch über die Attribute `class` oder `id`. Klassen (`class`) und IDs (`id`) sind Namen, die du den Elementen selbst gibst. Klassen definieren dabei Gruppen von Elementen und IDs verweisen auf bestimmte Elemente. Du könntest zum Beispiel den folgenden Tag anhand des Elementnamen `a`, der Klasse `external_link` oder der Id `link_to_wiki_page` identifizieren:

```html
<a href="https://en.wikipedia.org/wiki/Django" class="external_link" id="link_to_wiki_page">
```

You can read more about [CSS Selectors at w3schools](http://www.w3schools.com/cssref/css_selectors.asp).

We also need to tell our HTML template that we added some CSS. Open the `blog/templates/blog/post_list.html` file and add this line at the very beginning of it:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
{% load staticfiles %}
```

We're just loading static files here. :) Between the `<head>` and `</head>` tags, after the links to the Bootstrap CSS files, add this line:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<link rel="stylesheet" href="{% static 'css/blog.css' %}">
```

Der Browser liest die Dateien in der Reihenfolge in der sie im File stehen. Darum müssen wir sicherstellen, dass die Zeile am richtigen Ort steht. Otherwise the code in our file may be overriden by code in Bootstrap files. Wir haben unserer Vorlage gerade gesagt, wo sich die CSS-Datei befindet.

Deine Datei sollte jetzt so aussehen:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
{% load staticfiles %}
<html>
    <head>
        <title>Django Girls blog</title>
        <link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css">
        <link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css">
        <link rel="stylesheet" href="{% static 'css/blog.css' %}">
    </head>
    <body>
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
    </body>
</html>
```

OK, speicher die Datei und lade die Seite neu!

![Abbildung 14.2](images/color2.png)

Gut gemacht! Vielleicht wollen wir unserer Webseite etwas mehr Luft geben, indem wir den Abstand auf der linken Seite vergrößern? Probieren wir es aus!

{% filename %}blog/static/css/blog.css{% endfilename %}

```css
body {
    padding-left: 15px;
}
```

Add that to your CSS, save the file and see how it works!

![Abbildung 14.3](images/margin2.png)

Vielleicht können wir auch die Schrift in unserem HTML-Kopf anpassen? Füge dies zu `<head>` in `blog/templates/blog/post_list.html` hinzu:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<link href="//fonts.googleapis.com/css?family=Lobster&subset=latin,latin-ext" rel="stylesheet" type="text/css">
```

As before, check the order and place before the link to `blog/static/css/blog.css`. This line will import a font called *Lobster* from Google Fonts (https://www.google.com/fonts).

Find the `h1 a` declaration block (the code between braces `{` and `}`) in the CSS file `blog/static/css/blog.css`. Now add the line `font-family: 'Lobster';` between the braces, and refresh the page:

{% filename %}blog/static/css/blog.css{% endfilename %}

```css
h1 a {
    color: #FCA205;
    font-family: 'Lobster';
}
```

![Abbildung 14.3](images/font.png)

Super!

Wie oben erwähnt basiert CSS auf dem Konzept von Klassen. Dies erlaubt Dir einen Teil des HTML Codes mit einem Namen zu versehen und nur für diesen Teil einen Stil hinzuzufügen ohne Auswirkungen auf andere Teile des Codes. Dies kann sehr hilfreich sein! Eventuell hast Du zwei divs die etwas vollkommen Verschiedenes auszeichnen (wie einen Seitentitel oder Post Beitrag). Die Klasse hilft dir sie unterschiedlich aussehen zu lassen.

Im nächsten Schritt werden wir den HTML-Code einteilen. Füge eine Klasse (class) names `page-header` dem `div` hinzu, der die Kopfzeilen (header) enthalten soll:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<div class="page-header">
    <h1><a href="/">Django Girls Blog</a></h1>
</div>
```

Jetzt fügen wir noch eine Klasse `post` für den Blog-Inhalt (Post) dem `div` hinzu.

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<div class="post">
    <p>published: {{ post.published_date }}</p>
    <h1><a href="">{{ post.title }}</a></h1>
    <p>{{ post.text|linebreaksbr }}</p>
</div>
```

Gemäß der Änderungen im HTML erweitern wir unser CSS mit entsprechenden Selektoren. Selektoren, die mit `.` anfangen, beziehen sich auf Klassen im HTML. There are many great tutorials and explanations about CSS on the Web that can help you understand the following code. Für den Anfang reicht es aus, folgenden Text in deine `blog/static/css/blog.css`-Datei zu kopieren:

{% filename %}blog/static/css/blog.css{% endfilename %}

```css
.page-header {     background-color: #ff9400;     margin-top: 0;     padding: 20px 20px 20px 40px; } .page-header h1, .page-header h1 a, .page-header h1 a:visited, .page-header h1 a:active {     color: #ffffff;     font-size: 36pt;     text-decoration: none; } .content {     margin-left: 40px; } h1, h2, h3, h4 {     font-family: 'Lobster', cursive; } .date {     color: #828282; } .save {     float: right; } .post-form textarea, .post-form input {     width: 100%; } .top-menu, .top-menu:hover, .top-menu:visited {     color: #ffffff;     float: right;     font-size: 26pt;     margin-right: 20px; } .post {     margin-bottom: 70px; } .post h1 a, .post h1 a:visited {     color: #000000; }
```

Der HTML-Code, der für die Anzeige der Blogposts verantwortlich ist, soll durch Klassen erweitert werden. Ersetze den folgenden Code:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
{% for post in posts %}
    <div class="post">
        <p>published: {{ post.published_date }}</p>
        <h1><a href="">{{ post.title }}</a></h1>
        <p>{{ post.text|linebreaksbr }}</p>
    </div>
{% endfor %}
```

in `blog/templates/blog/post_list.html` durch diesen:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}

```html
<div class="content container">
    <div class="row">
        <div class="col-md-8">
            {% for post in posts %}
                <div class="post">
                    <div class="date">
                        <p>published: {{ post.published_date }}</p>
                    </div>
                    <h1><a href="">{{ post.title }}</a></h1>
                    <p>{{ post.text|linebreaksbr }}</p>
                </div>
            {% endfor %}
        </div>
    </div>
</div>
```

Speichere die geänderten Dateien und aktualisiere die Webseite.

![Abbildung 14.4](images/final.png)

Juhuu! Sieht super aus, oder? Schau dir den Code an den wir gerade eingefügt haben. Da siehst du wo wir überall Klassen zu den HTML Objekten hinzugefügt haben um sie in CSS zu referenzieren. Wo würdest du eine Änderung machen um das Datum in Türkis anzuzeigen?

Hab keine Angst, etwas mit dieser CSS Datei herumzuspielen und versuche ein paar Dinge zu ändern. Mit CSS herumzuspielen kann dir helfen zu verstehen was die verschiedenen Dinge genau machen. Mach dir keine Sorgen wenn etwas kaputt geht, du kannst deine Änderungen immer rückgängig machen!

Wir empfehlen diesen kostenlosen [Codeacademy HTML & CSS Kurs](https://www.codecademy.com/tracks/web). Er wird dir helfen deine Webseiten mit CSS schöner zu gestalten.

Bereit für das nächste Kapitel? :)