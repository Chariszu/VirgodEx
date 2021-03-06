# Form Django

Hal penting terakhir yang akan kita lakukan adalah bagaimana membuat agar user dapat menambah dan mengedit post blog dengan mudah. `Admin` django sudah bagus, tapi sedikit sulit untuk meng-customize dan membuatnya lebih cantik. Dengan ` bentuk </ 0> kita akan memiliki kekuatan mutlak atas antarmuka kita - kita dapat melakukan hampir semua hal yang dapat kita bayangkan!</p>

<p>Bagusnya form django adalah bahwa kita dapat mendefinisikannya dengan mudah atau dengan membuat sebuah <code>ModelForm` yang akan memberikan keluaran form tersebut ke dalam model terkait.

Ini benar-benar merupakan hal yang kita ingin lakukan. Kita akan membuat sebuah form yang kita tujukan untuk model `Post` kita.

Sama seperti tiap bagian penting dari Django, form memiliki file sendiri, yaitu forms.py.

Kita perlu membuat sebuah file dengan nama tersebut di dalam directory `blog`.

    blog
       └── forms.py
    

Baiklah, ayo buka dan ketik kode berikut ini:

{% filename%} blog / forms.py {% endfilename%}

```python
dari bentuk impor Django dari .Models import Post class PostForm (forms.ModelForm):

     class Meta:
         model = Post
         fields = ('title', 'text',)
```

Pertama, kita perlu mengimport form Django (</code>form django import forms</code>) dan model `Post` kita (`from .models import Post</0>).</p>

<p><code>PostForm`, sebagaimana yang barangkali anda duga, adalah nama form kita. Kita perlu memberi tahu Django bahwa bentuk ini adalah ` ModelForm </ 0> (jadi Django akan melakukan sihir untuk kita) - <code> forms.ModelForm </ 0> bertanggung jawab untuk itu.</p>

<p>Selanjutnya, kita memiliki <code>class Meta` dimana kita memberitahu django model yang mana yang harus digunakan untuk menciptakan form ini (`model=post`).

Akhirnya, kita dapat menyatakan field-field mana yang akan muncul di dalam form kita. Dalam skenario ini kita hanya ingin ` title </ 0> dan <code> text </ 0> yang akan terbuka - <code> author </ 0> harus menjadi orang yang saat ini masuk (Anda!) Dan < 0> create_date </ 0> harus disetel secara otomatis saat kita membuat sebuah posting (yaitu dalam kode), bukan?</p>

<p>Begitulah caranya! Yang kita perlu lakukan sekarang adalah menggunakan <em>view</em> dan menampilkannya di dalam sebuah template.</p>

<p>Jadi sekali lagi kita akan membuat link ke halaman, URL, tampilan dan template.</p>

<h2>Mengarahkan link menuju sebuah halaman dengan Form</h2>

<p>Sekarang saatnya membuka <code>blog/templates/base.html`. Kita akan menambahkan sebuah link di dalam `div` yang diberi nama `page-header`:

{% filename%} blog / templates / blog / base.html {% endfilename%}

```html
&lt;a href="{% url 'post_new' %}" class="top-menu"&gt;&lt;span class="glyphicon glyphicon-plus"&gt; </ 0>
```

Perhatikan bahwa kami ingin memanggil tampilan baru kami ` post_new </ 0> . Kelas <code> "glyphicon glyphicon-plus" </ 0> disediakan oleh tema bootstrap yang kami gunakan, dan akan menampilkan tanda tambah bagi kami.</p>

<p>Setelah menambahkan baris, file HTML Anda sekarang harus terlihat seperti ini:</p>

<p>{% filename%} blog / templates / blog / base.html {% endfilename%}</p>

<pre><code class="html">{% load staticfiles%} 
&lt;html&gt; 
&lt;head&gt; &lt;title&gt; Blog Django Girls </ 2> &lt;link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css"&gt; &lt;link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css"&gt; &lt;link href='//fonts.googleapis.com/css?family=Lobster&subset=latin,latin-ext' rel='stylesheet' type='text/css'&gt; &lt;link rel="stylesheet" href="{% static 'css/blog.css' %}"&gt; </ 1> &lt;body&gt; &lt;div class="page-header"&gt; &lt;a href="{% url 'post_new' %}" class="top-menu"&gt;&lt;span class="glyphicon glyphicon-plus"&gt; </ 9 > &lt;h1&gt;&lt;a href="/"&gt; Django Girls Blog </ 10> </ 8> &lt;div class="content container"&gt; &lt;div class="row"&gt; &lt;div class="col-md-8"&gt; {% konten blok%} {% endblock%} </ 13> </ 12> </ 11> </ 7 > </ 0>    
        
        
        
        
        
    
    
        
            
            
        
        
            
                
                    
                    
                
            
        
    

`</pre> 

Setelah disimpan dan merefresh halaman http://127.0.0.1:8000 anda pasti akan melihat tampilan error yang sudah familiar: `NoReverseMatch`, betul?

## URL

Kita buka `blog/urls.py` dan tambahkan baris:

{% filename%} blog / urls.py {% endfilename%}

```python
url (r '^ post / new / $', views.post_new, name = 'post_new'),
```

Dan kode terakhir akan tampak seperti ini:

{% filename%} blog / urls.py {% endfilename%}

```python
dari django.conf.urls url impor dari. impor dilihat urlpatterns = [
     url (r '^ $', views.post_list, name = 'post_list'),
     url (r '^ post / (? P <pk> \ d +) / $', views.post_detail, name = 'post_detail'),
     url (r '^ post / new / $', views.post_new, name = 'post_new'),]
```

Setelah menyegarkan situs, kita melihat ` AttributeError </ 0> , karena kita tidak memiliki tampilan <code> post_new </ 0> yang diterapkan. Mari kita tambahkan sekarang juga.</p>

<h2>view post_view</h2>

<p>Sekarang kita buka file <code>blog/views.py` dan tambahkan baris-baris berikut dengan sisa dari baris-baris `rows`: 

{% filename%} blog / views.py {% endfilename%}

```python
dari .forms import PostForm
```

Dan kemudian * tampilan </ 0> kami :</p> 

{% filename%} blog / views.py {% endfilename%}

```python
def post_new (request):
     form = PostForm ()
     mengembalikan render (request, 'blog / post_edit.html', {'form': form} )
```

Untuk membuat sebuah form `post` baru, kita perlu memanggil `PostForm` dan mengirimkannya ke dalam template tersebut. Kita akan kembali ke tampilan * ini </ 0> , tapi untuk saat ini, mari kita buat template untuk formulir dengan cepat.</p> 

## Template

Kita perlu membuat sebuah file </code>post_edit.html</code> di dalam direktori `blog/templates/blog</0>. Untuk membuat sebuah form agar berjalan, kita perlu beberapa hal:</p>

<ul>
<li>We have to display the form. We can do that with (for example) {% raw %}<code>{{ form.as_p }}`{% endraw %}.</li> 

* Baris di atas tersebut perlu diletakkan di dalam tag form HTML: `<form method="POST">...</form>`.
* Kita perlu sebuah tombol `Save`. Kita lakukan hal itu dengan sebuah tombol HTML: `<button type="submit">Save</button>`.
* Dan akhirnya, tepat setelah tag pembuka `<form ...>` kita perlu menambahkan {% raw%} ` {% csrf_token%} </ 1> {% endraw%} . Ini sangat penting, karena akan menjadikan form anda aman! Jika Anda lupa sedikit ini, Django akan mengeluh saat Anda mencoba menyimpan formulir:</li>
</ul>

<p><img src="images/csrf2.png" alt="Halaman terlarang CSFR" /></p>

<p>Baiklah, jadi mari kita lihat bagaimana HTML di <code> post_edit.html </ 0> akan terlihat:</p>

<p>{% filename%} blog / templates / blog / post_edit.html {% endfilename%}</p>

<pre><code class="html">{% meluas 'blog / base.html'%}

 {% blok konten%} 
&lt;h1&gt; Pos baru </ 0> &lt;form method="POST" class="post-form"&gt; {% csrf_token%} {{form.as_p}} &lt;button type="submit" class="save btn btn-default"&gt; Simpan </ 2> </ 1> {% endblock%}    
    
        
        
    

`</pre> 
    Saatnya merefresh web kita! Wow...! Form anda tampil!
    
    ![Form Baru](images/new_form2.png)
    
    Tapi tunggu sebentar! Saat Anda mengetikkan sesuatu di bidang ` title </ 0> dan <code> text </ 0> dan coba simpan, apa yang akan terjadi?</p>

<p>Tidak ada! Kami sekali lagi ada di halaman yang sama dan teks kami hilang ... dan tidak ada tulisan baru yang ditambahkan. Jadi apa yang salah?</p>

<p>Jawabnya: tidak ada yang salah. Kita hanya perlu bekerja sedikit lagi pada <em>view kita</em>.</p>

<h2>Menyimpan Form</h2>

<p>Buka <code> blog / views.py </ 0> sekali lagi. Saat ini semua yang ada pada tampilan <code> post_new </ 0> adalah sebagai berikut:</p>

<p>{% filename%} blog / views.py {% endfilename%}</p>

<pre><code class="python">def post_new (request):
     form = PostForm ()
     mengembalikan render (request, 'blog / post_edit.html', {'form': form} )
`</pre> 
    
    Saat kita mengirimkan formulir, kita dibawa kembali ke tampilan yang sama, tapi kali ini kita memiliki beberapa data lagi di ` request </ 0> , lebih khusus lagi pada permintaan <code> .POST </ 0> (penamaannya telah tidak ada hubungannya dengan blog "post", ada kaitannya dengan fakta bahwa kita "memposting" data). Ingat bagaimana dalam file HTML, definisi <code><form>` kami memiliki variabel ` method = "POST" </ 1> ? Semua field dari from tersebut kini dalam <code>request.POST`. Anda tidak boleh merename `POST` apapun namanya (satu-satunya nilai valed dari `method` adalah `GET`, akan tetapi kami tidak punya cukup waktu untuk menjelaskan perbedaannya).
    
    Jadi dalam kami * pandangan </ 0> kita memiliki dua situasi yang terpisah untuk menangani: pertama, ketika kita mengakses halaman untuk pertama kalinya dan kami ingin formulir kosong, dan kedua, ketika kita kembali ke * tampilan </ 0> dengan semua data formulir yang baru saja kita ketik. Sehingga kita perlu menambahkan sebuah kondisi (akan kita gunakan `if` untuk keperluan tersebut):</p> 
    
    {% filename%} blog / views.py {% endfilename%}
    
    ```python
jika request.method == "POST":
 [...] 
else:
 form = PostForm ()        
```

Saatnya untuk mengisi titik-titik ` [...] </ 0> . Jika <code> method </ 0> adalah <code> POST </ 0> maka kita ingin membuat <code> PostForm </ 0> dengan data dari form, kan? Kami akan melakukannya sebagai berikut:</p>

<p>{% filename%} blog / views.py {% endfilename%}</p>

<pre><code class="python">form = PostForm (request.POST)
`</pre> 

The next thing is to check if the form is correct (all required fields are set and no incorrect values have been submitted). We do that with `form.is_valid()`.

Kita cek apakah form tersebut valid dan jika ya, kita dapat menyimpannya!

{% filename%} blog / views.py {% endfilename%}

```python
jika form.is_valid ():
     post = form.save (komit = salah)
     post.author = request.user
     post.published_date = timezone.now ()
     post.save () post.save ()
```

Pada dasarnya, kita memiliki dua hal di sini: kita simpan form dengan ` form.save </ 0> dan kita tambahkan seorang penulis (karena tidak ada bidang <code> author </ 0> di <code> PostForm </ 0> dan bidang ini diperlukan). <code> commit = Salah </ 0> berarti kita tidak ingin menyimpan model <code> Post </ 0> - kita ingin menambahkan penulis terlebih dahulu. Sebagian besar waktu Anda akan menggunakan <code> form.save () </ 0> tanpa <code> commit = False </ 0> , namun dalam kasus ini, kita perlu menyediakannya. <code> post.save () </ 0> akan menyimpan perubahan (menambahkan penulis) dan sebuah posting blog baru dibuat!</p>

<p>Akhirnya, akan sangat mengagumkan jika kita bisa langsung masuk ke halaman <code> post_detail </ 0> untuk posting blog kita yang baru dibuat, bukan? Untuk melakukan itu kita memerlukan satu impor lagi:</p>

<p>{% filename%} blog / views.py {% endfilename%}</p>

<pre><code class="python">dari django.shortcuts import redirect
`</pre> 

Tambahkan di awal file Anda. Dan sekarang kita bisa mengatakan, "pergi ke halaman ` post_detail </ 0> untuk posting yang baru dibuat":</p>

<p>{% filename%} blog / views.py {% endfilename%}</p>

<pre><code class="python">pengalihan kembali ('post_detail', pk = post.pk)
`</pre> 

` post_detail </ 0> adalah nama tampilan yang ingin kita tuju. Ingat bahwa <em>view</em> ini memerlukan sebuah variabel <code>pk`? Untuk menyebarkannya ke tampilan, kita menggunakan ` pk = post.pk </ 0> , di mana <code> post </ 0> adalah postingan blog yang baru dibuat!</p>

<p>Baiklah, kita sudah banyak bicara, tapi kita mungkin ingin melihat seperti apa tampilan <em> lihat </ 0> sekarang juga kan?</p>

<p>{% filename%} blog / views.py {% endfilename%}</p>

<pre><code class="python">def post_new (request):
     if request.method == "POST":
         form = PostForm (request.POST)
         jika form.is_valid ():
             post = form.save (commit = false)
             post.author = request.user
             post.             publish_date = timezone.now ()
 post.save ()
             pengalihan kembali ('post_detail', pk = post.pk)
     else:
         form = PostForm ()
     mengembalikan render (permintaan, 'blog / post_edit.html', {'form': bentuk} )
`</pre> 

Mari lihat, apakah dapat berjalan. Pergi ke halaman http://127.0.0.1:8000/post/new/, tambahkan ` judul </ 0> dan <code> teks </ 0> , simpan ... dan voila! Posting blog baru ditambahkan dan kami diarahkan ke halaman <code> post_detail </ 0> !</p>

<p>Anda mungkin telah memperhatikan bahwa kami menetapkan tanggal publikasi sebelum menyimpan pos. Nantinya, kami akan mengenalkan <em> tombol publish </ 0> di <strong> Django Girls Tutorial: Extensions </ 1> .</p>

<p>Sejauh ini bagus !</p>

<blockquote>
  <p>Karena kita baru saja menggunakan antarmuka admin Django, sistem saat ini berpikir kita masih login. Ada beberapa situasi yang bisa menyebabkan kita keluar (menutup browser, memulai ulang DB, dll.). Jika, ketika membuat sebuah posting, Anda menemukan bahwa Anda mendapatkan kesalahan yang mengacu pada kurangnya pengguna yang masuk, masuk ke halaman admin http://127.0.0.1:8000/admin dan masuk lagi. Ini sementara akan menyelesaikan permasalahan. Ada penyelesain permanen yang menanti anda pada bab <strong>Homework: add security to your website!</strong> setelah tutorial utama.</p>
</blockquote>

<p><img src="images/post_create_error.png" alt="Login Error" /></p>

<h2>Validasi Form</h2>

<p>Sekarang, akan kami perlihatkan betapa hebatnya form django itu. Sebuah post blog perlu memiliki field <code>title` dan `text`. Pada model ` Post </ 0> kami tidak mengatakan bahwa bidang ini (berlawanan dengan <code> published_date </ 0> ) tidak diperlukan, jadi Django, secara default, mengharapkannya disetel.</p>

<p>Cobalah untuk menyimpan formulir tanpa <code> judul </ 0> dan <code> teks </ 0> . Coba tebak apa yang akan terjadi!</p>

<p><img src="images/form_validation2.png" alt="Validasi Form" /></p>

<p>Django berusaha untuk memvalidasi bahwa semua bidang dalam formulir kami benar. Bukankah itu mengagumkan?</p>

<h2>Form Edit</h2>

<p>Kini kita tahu bagaimana menambah form baru. Tetapi, bagaimana jika kita ingin mengedit yang sudah ada ? Ini sangat mirip dengan apa yang baru saja kita lakukan. Mari buat beberapa hal penting dengan cepat. (Jika Anda tidak mengerti sesuatu, Anda harus bertanya kepada pelatih Anda atau melihat bab-bab sebelumnya, karena kami telah menyelesaikan semua langkah ini.)</p>

<p>Buka <code> blog / templates / blog / post_detail.html </ 0> dan tambahkan barisnya</p>

<p>{% filename%} blog / templates / blog / post_detail.html {% endfilename%}</p>

<pre><code class="html">&lt;a class="btn btn-default" href="{% url 'post_edit' pk=post.pk %}"&gt;&lt;span class="glyphicon glyphicon-pencil"&gt; </ 0>
`</pre> 

sehingga template akan terlihat seperti ini:

{% filename%} blog / templates / blog / post_detail.html {% endfilename%}

```html
{% meluas 'blog / base.html'%}

 {% blok konten%} 
&lt;div class="post"&gt; {% jika post.published_date%} &lt;div class="date"&gt; {{post.published_date}} </ 1> {% endif%} <2 > </ 2> &lt;h1&gt; {{post.title}} </ 3> &lt;p&gt; {{post.text | linebreaksbr}} </ 4> </ 0> {% endblock%}    
        
            
                
            
        
        
        
        
    

```

Dalam `blog/urls.py` kita tambah baris ini:

{% filename%} blog / urls.py {% endfilename%}

```python
    url (r '^ post / (? P <pk> \ d +) / edit / $', views.post_edit, name = 'post_edit'),
```

Kita akan menggunakan kembali template `blog/templates/blog/post_edit.html`, sehingga sesuatu yang belum adalah sebuah *view*.

Mari buka ` blog / views.py </ 0> dan tambahkan ini di bagian akhir file:</p>

<p>{% filename%} blog / views.py {% endfilename%}</p>

<pre><code class="python">def post_edit (request, pk):
     post = get_object_or_404 (Post, pk = pk)
     jika request.method == "POST":
         form = PostForm (request.POST, instance = post)
         if form.is_valid ():
             post = form .save (commit = False)
             post.author = request.user
             post.published_date = timezone.now ()
             post.save ()
             pengalihan kembali ('post_detail', pk = post.pk)
     else:
         form = PostForm (instance = post )
     mengembalikan render (permintaan, 'blog / post_edit.html', {'form': form} )
`</pre> 

Ini tampak hampir sama persis dengan view `post_new` kita, benar ? Tetapi tidak seluruhnya sama persis. Untuk satu, kami melewatkan parameter ` pk </ 0> tambahan dari url. Selanjutnya, kita mendapatkan <code> Post </ 0> model yang ingin kita edit dengan <code> get_object_or_404 (Post, pk = pk) </ 0> dan kemudian, ketika kita membuat sebuah form, kita melewati postingan ini sebagai < 0> contoh </ 0> , saat kita menyimpan form ...</p>

<p>{% filename%} blog / views.py {% endfilename%}</p>

<pre><code class="python">form = PostForm (request.POST, instance = post)
`</pre> 

... dan saat kami baru saja membuka formulir dengan tulisan ini untuk diedit:

{% filename%} blog / views.py {% endfilename%}

```python
form = PostForm (contoh = post)
```

Baiklah, mari kita uji jika berhasil! Ayo pergi ke halaman ` post_detail </ 0> . Harus ada tombol edit di pojok kanan atas:</p>

<p><img src="images/edit_button2.png" alt="Tombol Edit" /></p>

<p>Ketika anda mengkliknya, anda aka melihat form tersebut berisi post blog kita:</p>

<p><img src="images/edit_form2.png" alt="Form Edit" /></p>

<p>Jangan ragu untuk mengganti judul atau teks dan simpan perubahannya!</p>

<p>Selamat! Aplikasi anda makin lama makin lengkap!</p>

<p>Jika Anda memerlukan informasi lebih lanjut tentang formulir Django, Anda harus membaca dokumentasi: https://docs.djangoproject.com/en/1.11/topics/forms/</p>

<h2>Keamanan</h2>

<p>Telah berhasil membuat post baru hanya dengan melakukan klik pada sebuah link itu hebat! Tapi, sekarang seseorang yang mengunjungi website anda akan dapat memposting postingan baru dan itu mungkin bukan hal yang anda inginkan! Tapi sekarang, siapa pun yang mengunjungi situs Anda akan dapat membuat posting blog baru, dan itu mungkin bukan sesuatu yang Anda inginkan. Mari kita membuatnya jadi tombol muncul untuk Anda tapi tidak untuk orang lain.</p>

<p>Dalam <code>blog/templates/blog/base.html`, temukan `div` dari `page-header` kita dan anchor tag yang anda letakkan sebelumnya. Tampilannya seharusnya seperti ini:

{% filename%} blog / templates / blog / base.html {% endfilename%}

```html
&lt;a href="{% url 'post_new' %}" class="top-menu"&gt;&lt;span class="glyphicon glyphicon-plus"&gt; </ 0>
```

Kami akan menambahkan tag ` {% jika%} </ 0> ke ini, yang akan membuat tautan hanya muncul untuk pengguna yang masuk ke admin. Sekarang, itu hanya kamu! Ubah tag 0>&lt;a&gt;` agar menjadi ini:

{% filename%} blog / templates / blog / base.html {% endfilename%}

```html
{% if user.is_authenticated %}
    <a href="{% url 'post_new' %}" class="top-menu"><span class="glyphicon glyphicon-plus"></span></a>
{% endif %}
```

Ini ` {% jika%} </ 0> akan menyebabkan tautan dikirim ke browser hanya jika pengguna yang meminta halaman masuk. Ini tidak melindungi adanya penulisan post baru seluruhnya, tapi cukup bagus untuk langkah awal. Kita akan mempelajari masalah keamanan lebih jauh pada pelajaran tentang extension.</p>

<p>Ingat ikon edit yang baru saja kita tambahkan ke halaman detail kita? Kami juga ingin menambahkan perubahan yang sama di sana, sehingga orang lain tidak dapat mengedit posting yang ada.</p>

<p>Buka <code> blog / templates / blog / post_detail.html </ 0> dan temukan baris ini:</p>

<p>{% filename%} blog / templates / blog / post_detail.html {% endfilename%}</p>

<pre><code class="html">&lt;a class="btn btn-default" href="{% url 'post_edit' pk=post.pk %}"&gt;&lt;span class="glyphicon glyphicon-pencil"&gt; </ 0>
`</pre> 

Ubah ke ini:

{% filename%} blog / templates / blog / post_detail.html {% endfilename%}

```html
{% jika user.is_authenticated%} 
&lt;a class="btn btn-default" href="{% url 'post_edit' pk=post.pk %}"&gt;&lt;span class="glyphicon glyphicon-pencil"&gt; </ 0> {% endif%}     

```

Karena Anda mungkin masuk, jika Anda menyegarkan halaman, Anda tidak akan melihat sesuatu yang berbeda. Muatkan halaman di browser lain atau jendela penyamaran (disebut "InPrivate" di Windows Edge), meskipun, dan Anda akan melihat bahwa tautan tidak muncul, dan ikonnya juga tidak ditampilkan!

## Satu hal lagi: saatnya melakukan deploy!

Mari kita lihat apakah itu semua dapat berjalan di PythonAnywhere. Saatnya melakukan deploy lagi!

* Pertama, lakukan commit kode baru anda dan kirim ke GitHub:

{% filename%} baris perintah {% endfilename%}

    $ git status $ git add --all. $ git status $ git commit -m "Ditambahkan tampilan untuk membuat / mengedit posting blog di dalam situs." $ git push
    

* Kemudian dalam konsol Bash [PythonAnywhere](https://www.pythonanywhere.com/consoles/):

{% filename%} baris perintah {% endfilename%}

    $ cd my-first-blog $ git pull
     [...]
    

* Yang terakhir, cari [Web tab](https://www.pythonanywhere.com/web_app_setup/) dan klik **Reload**.

Dan seharusnya dapa berjalan! Selamat :)