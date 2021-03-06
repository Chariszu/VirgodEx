# Model Django

Apa yang akan kita buat sekarang adalah sesuatu untuk menyimpan semua postingan pada blog kita. tetapi untuk bisa melakukan hal itu kita akan sedikit membahas tentang `objects`.

## Benda

Ada konsep dalam pemrograman yang disebut ` pemrograman berorientasi obyek </ 0> . Idenya adalah bahwa alih-alih menulis segala sesuatu sebagai urutan instruksi pemrograman yang membosankan, kita dapat memodelkan berbagai hal dan menentukan bagaimana mereka berinteraksi satu sama lain.</p>

<p>Jadi apa itu obyek? Ini adalah kumpulan properti dan tindakan. Kedengarannya aneh, tapi kami akan memberi contoh.</p>

<p>Jika kita ingin model kucing, kita akan membuat objek <code> Cat </ 0> yang memiliki beberapa properti seperti <code> warna </ 0> , <code> usia </ 0> , <code> mood < / 0> (seperti baik, buruk, atau mengantuk;)), dan <code> pemilik </ 0> (yang dapat diberi objek <code> Person </ 0> - atau mungkin, jika ada kucing yang tersesat, properti ini bisa kosong).</p>

<p>Kemudian <code> Cat </ 0> memiliki beberapa tindakan: <code> purr </ 0> , <code> scratch </ 0> , atau <code> feed </ 0> (dalam hal ini, kami akan memberikannya Cat beberapa <code> CatFood </ 0> , yang bisa jadi objek terpisah dengan properti, seperti <code> taste </ 0> ).</p>

<pre><code>Cat -------- usia warna mood owner purr () scratch () feed (cat_food)
`</pre> 

    Makanan Kucing --------
    

Jadi intinya idenya adalah untuk mendeskripsikan hal-hal nyata dalam kode dengan properti (disebut ` object properties </ 0> ) dan tindakan (disebut <code> methods </ 0> ).</p>

<p>Bagaimana kita akan model posting blog itu? Kami ingin membangun blog, bukan?</p>

<p>Kita perlu menjawab pertanyaan: Apa itu posting blog? Properti apa yang seharusnya dimiliki?</p>

<p>Nah, pastinya posting blog kita butuh beberapa teks dengan konten dan judulnya kan? Akan sangat menyenangkan mengetahui siapa yang menulisnya - jadi kita butuh seorang penulis. Akhirnya, kami ingin tahu kapan posting itu dibuat dan dipublikasikan.</p>

<pre><code>Posting -------- judul teks penulis created_date published_date
`</pre> 

Hal apa saja yang bisa dilakukan dengan posting blog? Akan menyenangkan untuk memiliki beberapa ` metode </ 0> yang menerbitkan posting, kan?</p>

<p>Jadi kita perlu <code> mempublikasikan </ 0> method.</p>

<p>Karena kita sudah tahu apa yang ingin kita capai, mari kita mulai pemodelannya di Django!</p>

<h2>Model Django</h2>

<p>Mengetahui apa itu objek, kita bisa membuat model Django untuk posting blog kita.</p>

<p>Model di Django adalah jenis khusus dari objek - itu disimpan dalam <code> Database </ 0> . Database adalah kumpulan data. Ini adalah tempat di mana Anda akan menyimpan informasi tentang pengguna, posting blog Anda, dll. Kami akan menggunakan database SQLite untuk menyimpan data kami. Ini adalah default database Django adaptor - itu akan cukup bagi kita sekarang.</p>

<p>Anda bisa memikirkan model dalam database sebagai spreadsheet dengan kolom (field) dan baris (data).</p>

<h3>Membuat aplikasi</h3>

<p>Agar semuanya tetap rapi, kami akan membuat aplikasi terpisah di dalam proyek kami. Sangat menyenangkan untuk memiliki semua yang terorganisir sejak awal. Untuk membuat aplikasi kita perlu menjalankan perintah berikut di console (dari <code> djangogirls </ 0> directory dimana <code> manage.py </ 0> file is):</p>

<p>{% filename %}Mac OS X and Linux:{% endfilename %}</p>

<pre><code>(myvenv) ~ / djangogirls $ python manage.py startapp blog
`</pre> 

{% filename %}Windows:{% endfilename %}

    (myvenv) C:\Users\Name\djangogirls> python manage.py startapp blog
    

You will notice that a new `blog` directory is created and it contains a number of files now. The directories and files in our project should look like this:

    djangogirls
    ????????? blog
    ??????? ????????? __init__.py
    ??????? ????????? admin.py
    ??????? ????????? apps.py
    ??????? ????????? migrations
    ??????? ??????? ????????? __init__.py
    ??????? ????????? models.py
    ??????? ????????? tests.py
    ??????? ????????? views.py
    ????????? db.sqlite3
    ????????? manage.py
    ????????? mysite
        ????????? __init__.py
        ????????? settings.py
        ????????? urls.py
        ????????? wsgi.py
    

After creating an application, we also need to tell Django that it should use it. We do that in the file `mysite/settings.py`. We need to find `INSTALLED_APPS` and add a line containing `'blog',` just above `]`. So the final product should look like this:

{% filename %}mysite/settings.py{% endfilename %}

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blog',
]
```

### Membuat model posting blog

In the `blog/models.py` file we define all objects called `Models` ??? this is a place in which we will define our blog post.

Let's open `blog/models.py`, remove everything from it, and write code like this:

{% filename %}blog/models.py{% endfilename %}

```python
from django.db import models
from django.utils import timezone


class Post(models.Model):
    author = models.ForeignKey('auth.User',on_delete=models.CASCADE)
    title = models.CharField(max_length=200)
    text = models.TextField()
    created_date = models.DateTimeField(
            default=timezone.now)
    published_date = models.DateTimeField(
            blank=True, null=True)

    def publish(self):
        self.published_date = timezone.now()
        self.save()

    def __str__(self):
        return self.title
```

> Periksa bahwa Anda menggunakan karakter dua garis bawah (`_`) pada setiap sisi `str`. Konvensi ini sering digunakan dengan Python dan terkadang kita juga menyebutnya "dunder" (singkatan dari "double-underscore").

It looks scary, right? But don't worry ??? we will explain what these lines mean!

All lines starting with `from` or `import` are lines that add some bits from other files. So instead of copying and pasting the same things in every file, we can include some parts with `from ... import ...`.

`class Post(models.Model):` ??? this line defines our model (it is an `object`).

- ` class </ 0> adalah kata kunci khusus yang menunjukkan bahwa kita mendefinisikan suatu objek.</li>
<li><code> Posting </ 0> adalah nama model kami. Kita bisa memberikannya nama yang berbeda (tapi kita harus menghindari karakter dan spasi khusus). Selalu mulai nama kelas dengan huruf besar.</li>
<li><code> models.Model </ 0> berarti bahwa Post adalah Model Django, jadi Django tahu bahwa itu harus disimpan dalam database.</li>
</ul>

<p>Now we define the properties we were talking about: <code>title`, `text`, `created_date`, `published_date` and `author`. To do that we need to define the type of each field (Is it text? A number? A date? A relation to another object, like a User?)</p> 
    - ` models.CharField </ 0> - begitulah cara Anda mendefinisikan teks dengan jumlah karakter yang terbatas.</li>
<li><code> models.TextField </ 0> - ini untuk teks panjang tanpa batas. Kedengarannya ideal untuk konten posting blog kan?</li>
<li><code> models.DateTimeField </ 0> - ini adalah tanggal dan waktu.</li>
<li><code> models.ForeignKey </ 0> - ini adalah link ke model lain.</li>
</ul>

<p>We will not explain every bit of code here since it would take too much time. You should take a look at Django's documentation if you want to know more about Model fields and how to define things other than those described above (https://docs.djangoproject.com/en/1.11/ref/models/fields/#field-types).</p>

<p>What about <code>def publish(self):`? This is exactly the `publish` method we were talking about before. `def` means that this is a function/method and `publish` is the name of the method. You can change the name of the method if you want. The naming rule is that we use lowercase and underscores instead of spaces. For example, a method that calculates average price could be called `calculate_average_price`.</p> 
        Methods often `return` something. There is an example of that in the `__str__` method. In this scenario, when we call `__str__()` we will get a text (**string**) with a Post title.
        
        Also notice that both `def publish(self):` and `def __str__(self):` are indented inside our class. Because Python is sensitive to whitespace, we need to indent our methods inside the class. Otherwise, the methods won't belong to the class, and you can get some unexpected behavior.
        
        If something is still not clear about models, feel free to ask your coach! We know it is complicated, especially when you learn what objects and functions are at the same time. But hopefully it looks slightly less magic for you now!
        
        ### Buat tabel untuk model di database Anda
        
        The last step here is to add our new model to our database. First we have to make Django know that we have some changes in our model. (We have just created it!) Go to your console window and type `python manage.py makemigrations blog`. It will look like this:
        
        {% filename %}command-line{% endfilename %}
        
            (myvenv) ~/djangogirls$ python manage.py makemigrations blog
            Migrations for 'blog':
              blog/migrations/0001_initial.py:
            
              - Create model Post
            
        
        **Note:** Remember to save the files you edit. Otherwise, your computer will execute the previous version which might give you unexpected error messages.
        
        Django prepared a migration file for us that we now have to apply to our database. Type `python manage.py migrate blog` and the output should be as follows:
        
        {% filename %}command-line{% endfilename %}
        
            (myvenv) ~/djangogirls$ python manage.py migrate blog
            Operations to perform:
              Apply all migrations: blog
            Running migrations:
              Rendering model states... DONE
              Applying blog.0001_initial... OK
            
        
        Hurray! Our Post model is now in our database! It would be nice to see it, right? Jump to the next chapter to see what your Post looks like!