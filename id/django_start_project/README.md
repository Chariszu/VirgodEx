# Project Django pertamamu!

> Bagian dari bab ini didasarkan pada tutorial oleh Geek Girls Carrots (https://github.com/ggcarrots/django-carrots).
> 
> Bagian dari bab ini didasarkan pada  Django-marcador    tutorial </ 0> berlisensi di bawah Creative Commons    Lisensi Internasional Attribution-ShareAlike 4.0. Hak cipta tutorial django-marcador oleh Markus Zapke-Gründemann et al.</p> </blockquote> 
> 
> We're going to create a small blog!
> 
> Langkah pertama adalah memulai dengan mebuat projek baru Django. Pada dasarnya, Kita akan menjalankan beberapa skrip yang disediakan oleh Django yang amana akan membuat skeleton projek Django untuk kita. Ini merupakan bagian direktori dan file yang akan kita gunakan nanti.
> 
> Nama untuk beberapa file dan direktori sangat penting untuk Django. Kamu harus mengganti nama file yang akan kita buat. Memindahkan file tersebut ke tempat yang lain bukanlah ide yang bagus. Django perlu mempertahankan struktur tertentu agar bisa menemukan hal penting.
> 
> > Ingatlah untuk menjalankan semuanya di virtualenv. Jika Anda tidak melihat awalan ` (myvenv) </ 0> di konsol Anda, Anda perlu mengaktifkan virtualenv Anda. Kami menjelaskan bagaimana melakukannya di bagian <strong> instalasi Django </ 0> di bagian <strong> Bekerja dengan virtualenv </ 0> . Mengetik <code> myvenv \ Scripts \ activate </ 0> pada Windows atau
 <code> sumber myvenv / bin / activate </ 0> pada Mac OS X atau Linux akan melakukan ini untuk Anda.  </p>
</blockquote>

<!--sec data-title="Create project: OS X or Linux" data-id="django_start_project_OSX_Linux" data-collapse=true ces-->

<p>Di konsol Mac OS X atau Linux Anda, Anda harus menjalankan perintah berikut. <strong> Jangan lupa menambahkan periode (atau titik) <code> . </ 1> di akhir! </ 0></p>

<p>{% filename%} baris perintah {% endfilename%}</p>

<pre><code>(myvenv) ~/djangogirls$ django-admin startproject mysite .
`</pre> 
> > 
> > > Masalah `.` cukup krusial karena ini akan memberi perintah skrip untuk menginstall Django pada direktori-mu saat ini (untuk masalah `.` adalah referensi singkat).
> > > 
> > > ** Catatan </ 0> Saat mengetikkan perintah di atas, ingat bahwa Anda hanya mengetikkan bagian yang dimulai oleh ` Django-admin </ 1>.
  Bagian <code> (myvenv) ~ / djangogirls $ </ 0> yang ditunjukkan di sini hanyalah contoh dari prompt yang akan mengundang masukan Anda pada baris perintah Anda.</p>
</blockquote>

<!--endsec-->


> > > 
> > > <!--sec data-title="Create project: Windows" data-id="django_start_project_windows" data-collapse=true ces-->

<p>Pada Windows Anda harus menjalankan perintah berikut. <strong> (Jangan lupa menambahkan periode (atau titik) <code>. </ 1> di akhir) </ 0>:</p>

<p>{% filename%} baris perintah {% endfilename%}</p>

<pre><code>(myvenv) C: \ Users \ Name \ djangogirls & gt; django-admin.exe startproject mysite.
`</pre> 
> > > 
> > > > Masalah `.` cukup krusial karena ini akan memberi perintah skrip untuk menginstall Django pada direktori-mu saat ini (untuk masalah `.` adalah referensi singkat).
> > > > 
> > > > **Note** When typing the command above, remember that you only type the part which starts by `django-admin.exe`. The `(myvenv) C:\Users\Name\djangogirls>` part shown here is just example of the prompt that will be inviting your input on your command line.
> > > 
> > > <!--endsec-->
> > > 
> > > ` django-admin.py </ 0> adalah script yang akan membuat direktori dan file untuk Anda. Anda sekarang harus memiliki struktur direktori yang terlihat seperti ini:</p>

<pre><code>djangogirls
├───manage.py
└───mysite
         settings.py
         urls.py
         wsgi.py
         __init__.py
`</pre> 
> > > 
> > > > ** Catatan </ 0>: dalam struktur direktori Anda, Anda juga akan melihat direktori ` venv </ 1> yang telah kita buat sebelumnya.</p>
</blockquote>

<p><code> manage.py </ 0> adalah skrip yang membantu pengelolaan situs. Dengan itu kita akan bisa (antara lain) untuk memulai web server di komputer kita tanpa menginstal apapun.</p>

<p>File <code> settings.py </ 0> berisi konfigurasi situs web Anda.</p>

<p>Ingat ketika kita berbicara tentang pembawa surat yang memeriksa kemana harus mengirimkan surat? <code> urls.py </ 0> berisi daftar pola yang digunakan oleh <code> urlresolver </ 0>.</p>

<p>Mari kita abaikan file lainnya untuk saat ini karena kita tidak akan mengubahnya. Satu-satunya hal yang perlu diingat adalah tidak menghapusnya secara tidak sengaja!</p>

<h2>Mengubah pengaturan</h2>

<p>Mari buat beberapa perubahan di <code> mysite / settings.py </ 0>. Buka file dengan menggunakan editor kode yang telah Anda instal sebelumnya.</p>

<p><strong> Catatan </ 0>: Perlu diingat bahwa <code> settings.py </ 1> adalah file biasa, seperti file lainnya. Anda dapat membukanya dari dalam editor kode, dengan menggunakan tindakan menu "file -> open". Ini akan memberi Anda jendela biasa tempat Anda dapat menavigasi ke file <code> settings.py </ 0> dan memilihnya. Sebagai alternatif, Anda dapat membuka file dengan menavigasi ke folder djangogirls di desktop Anda dan mengklik kanannya. Kemudian, pilih editor kode Anda dari daftar. Memilih editor penting karena Anda mungkin menginstal program lain yang bisa membuka file tapi tidak membiarkan Anda mengeditnya.</p>

<p>Alangkah baiknya memiliki waktu yang tepat di situs kami. Pergi ke <a href="https://en.wikipedia.org/wiki/List_of_tz_database_time_zones"> daftar zona waktu Wikipedia </ 0> dan salin zona waktu yang relevan (TZ) (misalnya <code> Eropa / Berlin </ 1> ).</p>

<p>Di <code> settings.py </ 0>, cari baris yang berisi <code> TIME_ZONE </ 0> dan modifikasi untuk memilih zona waktu Anda sendiri. Sebagai contoh:</p>

<p>{% filename%} mysite / settings.py {% endfilename%}</p>

<pre><code class="python">TIME_ZONE = 'Eropa / Berlin'
`</pre> 
> > > > 
> > > > Kode bahasa terdiri dari bahasa, mis. ` en </ 0> untuk bahasa Inggris atau <code> de </ 0> untuk bahasa jerman, dan kode negara, mis. <code> de </ 0> untuk jerman atau <code> ch </ 0> untuk swiss. Anda ingin menambahkan ini jika Anda ingin tombol dan notifikasi default dari Django ada dalam bahasa Anda. Jadi Anda akan memiliki tombol "Batal" yang diterjemahkan ke bahasa yang Anda definisikan di sini. <a href="https://docs.djangoproject.com/en/1.11/ref/settings/#language-code"> Django hadir dengan banyak terjemahan yang disiapkan </ 0> .</p>

<p>Ubah kode bahasa dengan mengubah baris berikut:</p>

<p>{% filename%} mysite / settings.py {% endfilename%}</p>

<pre><code class="python">LANGUAGE_CODE = 'de-ch'
`</pre> 
> > > > 
> > > > Kita juga perlu menambahkan path untuk file statis. (Kita akan mencari tahu semua tentang file statis dan CSS nanti di tutorial.) Turun ke * akhir </ 0> dari file tersebut, dan di bawah entri ` STATIC_URL </ 1> , tambahkan sebuah yang baru disebut <code> STATIC_ROOT </ 1> :</p>

<p>{% filename%} mysite / settings.py {% endfilename%}</p>

<pre><code class="python">STATIC_URL = '/ static /' STATIC_ROOT = os.path.join (BASE_DIR, 'statis')
`</pre> 
> > > > 
> > > > Bila ` DEBUG </ 0> adalah <code> True </ 0> dan <code> ALLOWED_HOSTS </ 0> kosong, host divalidasi terhadap <code> ['localhost', '127.0.0.1', ' [:: 1] '] </ 0> . Ini tidak akan cocok dengan nama host kami di PythonAnywhere begitu kami menerapkan aplikasi kami sehingga kami akan mengubah setelan berikut:</p>

<p>{% filename%} mysite / settings.py {% endfilename%}</p>

<pre><code class="python">ALLOWED_HOSTS = ['127.0.0.1', '.pythonanywhere.com']
`</pre> 
> > > > 
> > > > > ** Catatan </ 0> : Jika Anda menggunakan Chromebook, tambahkan baris ini di bagian bawah file settings.py Anda: ` MESSAGE_STORAGE = 'django.contrib.messages.storage.session.SessionStorage' </ 1>  </p>
  
  <p>Also add <code>.c9users.io` to the `ALLOWED_HOSTS` if you are using cloud9</p> </blockquote> 
> > > > > 
> > > > > ## Buat database
> > > > > 
> > > > > Ada banyak perangkat lunak database yang berbeda yang dapat menyimpan data untuk situs Anda. Kita akan menggunakan yang default, ` sqlite3 </ 0> .</p>

<p>Ini sudah disiapkan di bagian berkas <code> mysite / settings.py </ 0> Anda :</p>

<p>{% filename%} mysite / settings.py {% endfilename%}</p>

<pre><code class="python">DATABASES = {
     'default': {
         'ENGINE': 'django.db.backends.sqlite3',
         'NAME': os.path.join (BASE_DIR, 'db.sqlite3'),
     }}
`</pre> 
> > > > > 
> > > > > Untuk membuat database untuk blog kita, mari kita jalankan yang berikut di konsol: ` python manage.py migrate </ 0> (kita perlu berada di direktori <code> djangogirls </ 0> yang berisi <code> manage.py </ 0> file). Jika berjalan dengan baik, Anda harus melihat sesuatu seperti ini:</p>

<p>{% filename%} baris perintah {% endfilename%}</p>

<pre><code>(myvenv) ~ / djangogirls $ python manage.py migran Operasi yang harus dilakukan:
   Terapkan semua migrasi: auth, admin, contenttypes, sessions Running migration:
   Rendering model states ... DONE
   Menerapkan contenttypes.0001_initial ... OK
   Menerapkan auth.0001_initial ... OK
   Menerapkan admin.0001_initial ... OK
   Menerapkan admin.0002_logentry_remove_auto_add ... OK
   Menerapkan contenttypes.0002_remove_content_type_name ... OK
   Menerapkan auth.0002_alter_permission_name_max_length ... OK
   Menerapkan auth.0003_alter_user_email_max_length ... OK
   Menerapkan auth.0004_alter_user_username_opts ... OK
   Menerapkan auth.0005_alter_user_last_login_null ... OK
   Menerapkan auth.0006_require_contenttypes_0002 ... OK
   Menerapkan auth.0007_alter_validators_add_error_messages ... OK
   Menerapkan sesi.0001_initial ... baik
`</pre> 
> > > > > 
> > > > > Dan kita sudah selesai! Waktunya memulai web server dan melihat apakah website kita bekerja!
> > > > > 
> > > > > ## Memulai server web
> > > > > 
> > > > > Anda harus berada di direktori yang berisi file ` manage.py </ 0> (direktori <code> djangogirls </ 0> ). Di konsol, kita bisa memulai server web dengan menjalankan <code> python manage.py runserver </ 0> :</p>

<p>{% filename%} baris perintah {% endfilename%}</p>

<pre><code>(myvenv) ~ / djangogirls $ python manage.py runserver
`</pre> 
> > > > > 
> > > > > Jika Anda menggunakan Chromebook, gunakan perintah ini sebagai gantinya:
> > > > > 
> > > > > {% filename %}Cloud 9{% endfilename %}
> > > > > 
> > > > >     (myvenv) ~/djangogirls$ python manage.py runserver 0.0.0.0:8080
> > > > >     
> > > > > 
> > > > > Jika Anda menggunakan Windows dan ini gagal dengan ` UnicodeDecodeError </ 0> , gunakan perintah ini sebagai gantinya:</p>

<p>{% filename %}command-line{% endfilename %}</p>

<pre><code>(myvenv) ~/djangogirls$ python manage.py runserver 0:8000
`</pre> 
> > > > > 
> > > > > Sekarang yang perlu Anda lakukan hanyalah memeriksa apakah situs Anda berjalan. Buka browser Anda (Firefox, Chrome, Safari, Internet Explorer atau apapun yang Anda gunakan) dan masukkan alamat ini:
> > > > > 
> > > > > {% filename %}browser{% endfilename %}
> > > > > 
> > > > >     http://127.0.0.1:8000/
> > > > >     
> > > > > 
> > > > > Jika menggunakan Chromebook, Anda akan selalu mengunjungi server uji dengan mengakses:
> > > > > 
> > > > > {% filename %}browser{% endfilename %}
> > > > > 
> > > > >     https://django-girls-<your cloud9 username>.c9users.io
> > > > >     
> > > > > 
> > > > > Selamat! Anda baru saja membuat situs web pertama dan menjalankannya menggunakan server web! Bukankah itu mengagumkan?
> > > > > 
> > > > > ![Ini berhasil!](images/it_worked2.png)
> > > > > 
> > > > > Saat server web berjalan, Anda tidak akan melihat command-line prompt baru untuk memasukkan perintah tambahan. Terminal akan menerima teks baru tapi tidak akan menjalankan perintah baru. Ini karena server web terus berjalan untuk mendengarkan permintaan masuk .
> > > > > 
> > > > > > Kami meninjau bagaimana server web bekerja di ** Bagaimana Internet bekerja** bab.
> > > > > 
> > > > > Untuk mengetikkan perintah tambahan saat server web berjalan, buka jendela terminal baru dan aktifkan virtualenv Anda. Untuk menghentikan server web, kembali ke jendela tempat ia menjalankan dan tekan tombol CTRL + C - Control dan C bersama-sama (di Windows, Anda mungkin harus menekan Ctrl + Break).
> > > > > 
> > > > > Siap untuk langkah selanjutnya? Saatnya untuk membuat beberapa konten!