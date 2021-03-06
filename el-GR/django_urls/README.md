# Django URLs

Είμαστε έτοιμοι να χτίσουμε την πρώτη μας σελίδα: μια αρχική σελίδα (homepage) για το blog μας! Αλλά πρώτα πρέπει να μάθουμε λίγα πράγματα για τα Django URLs.

## Τι είναι ένα URL;

Ένα URL είναι μια διεύθυνση ιστού. Μπορείτε να δείτε ένα URL κάθε φορά που επισκέπτεστε μια σελίδα. Είναι ορατό στην γραμμή διεύθυνσης. (Ναι! `127.0.0.1:8000` είναι ένα URL! Και το `https://djangogirls.org` είναι, επίσης, ένα URL.)

![URL](images/url.png)

Κάθε σελίδα στο ιντερνετ χρειάζεται το δικό της URL. Με αυτό τον τρόπο η εφαρμογή σας θα ξέρει τι να δείξει στον χρήστη που ανοίγει αυτό το URL. Στο Django, χρησιμοποιούμε κάτι που το ονομάζουμε `URLconf` (URL configuration). Το URLconf είναι ένα σετ από μοτίβα που το Django θα προσπαθήσει να ταιριάξει με το ζητούμενο URL ούτως ώστε να βρει το κατάλληλο view.

## Πως δουλεύουν τα URLs στο Django;

Ας ανοίξουμε το αρχείο `mysite/urls.py` και να δούμε τι έχει μέσα:

{% filename %}mysite/urls.py{% endfilename %}

```python
"""mysite URL Configuration

[...]
"""
from django.contrib import admin
from django.urls import path

urlpatterns = [
    path('admin/', admin.site.urls),
]
```

Όπως βλέπετε, το Django έχει γράψει μέσα κάποια πράγματα για εμάς.

Οι γραμμές μεταξύ των τριπλών εισαγωγικών (`'''` ή `"""`) ονομάζονται docstrings. Μπορείτε να τα γράψετε στην αρχή κάθε Python αρχείου, κλάσης, μεθόδου ή συνάρτησης για να περιγράψετε το τι κάνει. Δεν θα εκτελεστούν από την Python.

Το admin URL, το οποίο επισκεφτήκατε σε προηγούμενο κεφάλαιο, είναι ήδη εκεί:

{% filename %}mysite/urls.py{% endfilename %}

```python
    path('admin/', admin.site.urls),
```

Η γραμμή αυτή σημαίνει ότι για κάθε URL που ξεκινά με τη λέξη `admin/`, το Django θα ψάξει να βρει το αντίστοιχο *view*. Σε αυτή την περίπτωση συμπεριλαμβάνουμε αρκετά admin URLs ούτως ώστε να μην εμφανίζονται όλα σε αυτό το αρχείο. Είναι περισσότερο ευανάγνωστο κατ' αυτό τον τρόπο.

## Το πρώτο σας Django URL!

Ώρα να δημιουργήσουμε το πρώτο σας URL! Θέλουμε η διεύθυνση 'http://127.0.0.1:8000/' να είναι η αρχική μας σελίδα για το blog, η οποία θα εμφανίζει όλα τα posts.

Θέλουμε, επίσης, να κρατήσουμε το αρχείο `mysite/urls.py` καθαρό. Οπότε, θα κάνουμε import τα URLs από το `blog` application στο αρχείο `mysite/urls.py`.

Πηγαίνετε λοιπόν, και προσθέστε αυτή τη γραμμή στο αρχείο `blog.urls`. Θα χρειαστεί, επίσης, να αλλάξετε την γραμμή `from django.urls…` επειδή χρησιμοποιούμε την συνάρτηση `include`. Επομένως, θα χρειαστεί να προσθέσετε αυτή τη γραμμή.

Το αρχείο σας `mysite/urls.py` θα μοιάζει κάπως έτσι:

{% filename %}mysite/urls.py{% endfilename %}

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('blog.urls')),
]
```

Το Django, τώρα, θα ανακατευθύνει οτιδήποτε έρχεται στο 'http://127.0.0.1:8000/' προς το αρχείο `blog.urls` και από κει και πέρα θα πράττει αναλόγως.

## blog.urls

Δημιουργήστε ένα κενό αρχείο `urls.py` μέσα στο φάκελο `blog` και ανοίξτε το. Τέλεια! Προσθέστε αυτές τις δύο γραμμές:

{% filename %}blog/urls.py{% endfilename %}

```python
from django.urls import path
from . import views
```

Εδώ κάνουμε import τη συνάρτηση `path` του Django και όλα τα `views` από το `blog` application. (Δεν κάποια views ακόμα αλλά θα φτάσουμε εκεί σε λίγο!)

Μετά από αυτό, μπορούμε να προσθέσουμε το πρώτο μας URL μοτίβο (URL pattern):

{% filename %}blog/urls.py{% endfilename %}

```python
urlpatterns = [
    path('', views.post_list, name='post_list'),
]
```

Όπως μπορείτε να δείτε, αναθέτουμε ένα `view` με το όνομα `post_list` στο πηγαίο URL. This URL pattern will match an empty string and the Django URL resolver will ignore the domain name (i.e., http://127.0.0.1:8000/) that prefixes the full URL path. Αυτό το μοτίβο θα πει στο Django ότι το view `views.post_list` είναι το σωστό μέρος να πας αν κάποιος επισκεφτεί τη διεύθυνση 'http://127.0.0.1:8000/'.

Το τελευταίο μέρος, `name='post_list'`, είναι το όνομα του URL το οποίο θα χρησιμοποιηθεί για να αναγνωρίσουμε αυτό το URL. Αυτό μπορεί να είναι το ίσιο όπως το όνομα του view αλλά μπορεί να είναι κάτι τελείως το διαφορετικό αν θέλετε. Θα χρησιμοποιούμε τα URLs με όνομα (named URLs) αργότερα στο project, οπότε είναι σημαντικό να ονομάσετε κάθε URL στην εφαρμογή σας. Θα προσπαθήσουμε, επίσης, να κρατήσουμε τα ονόματα μοναδικά μεταξύ τους και εύκολα να τα θυμόμαστε.

Αν προσπαθήσετε να επισκεφτείτε τη διεύθυνση http://127.0.0.1:8000/, τότε θα δείτε ένα σφάλμα τύπου 'web page not available'. Αυτό προκύπτει επειδή ο server (θυμάστε όταν γράψατε `runserver`?) δεν τρέχει. Δείτε στην κονσόλα που έτρεχε ο server σας και δείτε το γιατί.

![Σφάλμα](images/error1.png)

Η κονσόλα, σας εμφάνισε σφάλμα αλλά μην ανησυχείτε. Είναι στην ουσία πολύ χρήσιμο: σας λέει **no attribute 'post_list'**. Αυτό είναι το όνομα του *view* το οποίο προσπαθεί να βρει και να χρησιμοποιήσει το Django αλλά δεν το έχουμε δημιουργήσει ακόμα. Σε αυτό το σημείο, ούτε η σελίδα `/admin/` δεν θα λειτουργεί. Μην ανησυχείτε. Θα φτάσουμε και εκεί. Αν δείτε κάποιο διαφορετικό σφάλμα προσπαθείστε να επανεκκινήσετε τον τοπικό server σας. To do that, in the console window that is running the web server, stop it by pressing Ctrl+C (the Control and C keys together). On Windows, you might have to press Ctrl+Break. Then you need to restart the web server by running a `python manage.py runserver` command.

> If you want to know more about Django URLconfs, look at the official documentation: https://docs.djangoproject.com/en/2.2/topics/http/urls/