# Pengantar ke HTML

Apa itu template, mungkin kamu bertanya?

Template adalah file yang dapat kita gunakan kembali untuk menyajikan informasi yang berbeda dalam format yang konsisten - misalnya, Anda dapat menggunakan template untuk membantu menulis surat, karena walaupun setiap huruf mungkin berisi pesan berbeda dan ditujukan kepada yang lain. orang, mereka akan berbagi format yang sama.

Format template-template Django dijelaskan dalam bahasa yang disebut HTML (itulah HTML yang kami sebutkan di bab pertama, ** Bagaimana Internet bekerja </ 0>).</p> 

## HTML adalah?

HTML is a code that is interpreted by your web browser – such as Chrome, Firefox or Safari – to display a web page for the user.

HTML singkatan dari "HyperText Markup bahasa". ** HyperText </ 0> berarti itu adalah jenis teks yang mendukung sebuah link antar halaman. < Markup </ 0> berarti kita telah mengambil sebuah dokumen dan menandai dengan kode untuk mengatakan sesuatu (dalam hal ini, browser internet) bagaimana menafsirkan halaman. Kode HTML dibangun oleh ** tag </ 0>, masing-masing dimulai dengan ` & lt; </ 1> dan diakhiri dengan <code> & gt; </ 1>. Tag ini mewakili markup <strong> elemen </ 0> .</p>

<h2>Template pertama kamu!</h2>

<p>Membuat template berarti membuat file template. Semuanya adalah sebuah file, bukan? Anda mungkin sudah menyadari hal ini.</p>

<p>Template tersimpan di direktori <code> blog / template / blog </ 0>. Jadi pertama menciptakan sebuah direktori yang disebut <code>template` di dalam direktori blog Anda. Kemudian dibuat direktori lain yang disebut `blog` di dalam direktori template Anda:</p> 

    blog 
    └───templates
     └───blog
    

(Anda mungkin bertanya-tanya mengapa kita perlu dua direktori kedua disebut `blog`-seperti yang Anda akan menemukan nanti, ini adalah cukup berguna konvensi penamaan yang membuat hidup lebih mudah ketika keadaan mulai menjadi lebih rumit.)

Dan sekarang membuat `post_list.html` file (Biarkan kosong untuk sekarang) didalam direktori `blog/template/blog`.

Lihatlah bagaimana situs web terlihat sekarang: http://127.0.0.1:8000 /

> Jika Anda masih memiliki kesalahan `TemplateDoesNotExist`, mencoba untuk me-ulang server Anda. Pergi ke baris perintah, menghentikan server dengan menekan Ctrl + C (kontrol dan C kunci bersama-sama) dan mulai lagi dengan menjalankan perintah `python manage.py runserver`.

![Gambar 11.1](images/step1.png)

Tidak ada kesalahan lagi! Selamat :) Namun, situs Anda sebenarnya tidak menerbitkan apapun kecuali halaman kosong, karena template Anda juga kosong. Kita perlu memperbaikinya.

Tambahkan yang berikut ke file template Anda:

{% filename %}blog/static/css/list.html{% endfilename %}

```html
<html><p>Hi sana!</p>     <p>Kerjanya!</p> </html>
```

Jadi bagaimana Apakah situs web Anda terlihat sekarang? Mengunjunginya untuk mengetahui: http://127.0.0.1:8000 /

![Gambar 11.2](images/step3.png)

Itu berhasil! Nice bekerja di sana :)

* Tag paling dasar, `<html>`, selalu adalah awal dari setiap halaman web dan `</html>` selalu akhir. Seperti yang Anda lihat, seluruh isi website terjadi antara awal tag `<html>`dan tag penutup `</html>`
* `<p>`adalah suatu tag untuk elemen ayat; `</p>` menutup setiap ayat

## Kepala dan tubuh

Setiap halaman HTML juga dibagi menjadi dua elemen: **kepala** dan **tubuh**.

* **kepala** merupakan elemen yang berisi informasi tentang dokumen yang tidak ditampilkan di layar.

* **tubuh** merupakan unsur yang berisi segala sesuatu yang lain yang ditampilkan sebagai bagian dari halaman web.

Kami menggunakan `<head>` untuk memberi tahu browser tentang konfigurasi halaman, dan `<body>` untuk memberitahukannya tentang apa yang sebenarnya ada di halaman.

Misalnya, Anda bisa memasukkan elemen judul halaman web ke dalam `<head>`, seperti ini:

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

Simpan dan refresh halaman Anda.

![Gambar 11.3](images/step4.png)

Perhatikan bagaimana browser telah dipahami bahwa "Ola's blog" adalah judul halaman Anda? Ini telah ditafsirkan `<title>Ola's blog</title>` dan ditempatkan teks di bar judul browser Anda (ini juga akan digunakan untuk bookmark dan seterusnya).

Mungkin Anda juga memperhatikan bahwa setiap tag pembuka cocok dengan tag penutup * *, dengan ` / `, dan elemen itu * nested * (yaitu Anda dapat Tutup tag tertentu sampai semua yang ada di dalamnya sudah ditutup juga).

Ini seperti memasukkan barang ke dalam kotak. Anda memiliki satu kotak besar, `<html> </html>`; Di dalamnya ada `<body> </body>`, dan itu berisi kotak yang masih lebih kecil: `<p> </p>`.

You need to follow these rules of *closing* tags, and of *nesting* elements – if you don't, the browser may not be able to interpret them properly and your page will display incorrectly.

## Sesuaikan template Anda

Anda sekarang bisa bersenang-senang dan mencoba menyesuaikan template Anda! Berikut adalah beberapa tag yang berguna untuk itu:

* `<h1> Judul </h1>` untuk pos terpenting Anda
* `<h2> Sub-judul </h2>` untuk judul di tingkat berikutnya
* `<h3>Sub-sub-judul</h3>` ... dan seterusnya, sampai `<h6>`
* `<p>Sebuah paragraf teks </p>`
* `<em> teks</em>` menekankan teks Anda
* `<strong>teks</strong>` sangat menekankan teks Anda
* `<br>` goes to another line (you can't put anything inside br and there's no closing tag)
* `<a href="https://djangogirls.org">link</a>` membuat sebuah link
* `<ul> <li> item pertama </li> <li> item kedua </li> </ul>` membuat daftar, sama seperti yang ini!
* `<div></div>` mendefinisikan bagian dari halaman

Berikut adalah contoh template lengkap, copy dan paste ke `blog/templates/blog/post_list.html`:

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
            <p>Aenean eu leo quam. Anak rok televisi sepak bola dan gas beracun. Donec id elit non mi porta gravida di eget Metus Sed congue. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.</p>
        </div>

        <div>
            <p>published: 14.06.2014, 12:14</p>
            <h2><a href="">My second post</a></h2>
            <p>Aenean eu leo quam. Anak rok televisi sepak bola dan gas beracun. Donec id elit non mi porta gravida di eget Metus Sed congue. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut f.</p>
        </div>
    </body>
</html>
```

We've created three `div` sections here.

* The first `div` element contains the title of our blog – it's a heading and a link
* Another two `div` elements contain our blogposts with a published date, `h2` with a post title that is clickable and two `p`s (paragraph) of text, one for the date and one for our blogpost.

Ini memberi kita efek ini:

![Gambar 11.4](images/step6.png)

Yaaay! But so far, our template only ever displays exactly **the same information** – whereas earlier we were talking about templates as allowing us to display **different** information in the **same format**.

Apa yang sebenarnya ingin kita lakukan adalah menampilkan posting nyata yang ditambahkan di admin Django kita - dan ke sanalah kita akan pergi berikutnya.

## Satu hal lagi: menyebarkan!

Alangkah baiknya melihat semua ini dan tinggal di Internet kan? Mari kita lakukan PythonAnywhere lainnya :

### Komit, dan dorong kode Anda ke Github

Pertama, mari kita lihat file apa yang telah berubah sejak terakhir kita digunakan (jalankan perintah ini secara lokal, bukan di PythonAnywhere ):

{% filename %}command-line{% endfilename %}

    $ git status
    

Make sure you're in the `djangogirls` directory and let's tell `git` to include all the changes within this directory:

{% filename %}command-line{% endfilename %}

    $ git add --all .
    

> **Note** `--all` means that `git` will also recognize if you've deleted files (by default, it only recognizes new/modified files). Also remember (from chapter 3) that `.` means the current directory.

Before we upload all the files, let's check what `git` will be uploading (all the files that `git` will upload should now appear in green):

{% filename %}command-line{% endfilename %}

    $ git status
    

Kita sudah hampir sampai, sekarang saatnya untuk menceritakannya untuk menyimpan perubahan ini dalam sejarahnya. Kami akan memberikan "pesan komit" di mana kami menggambarkan apa yang telah kami ubah. Anda dapat mengetikkan apa pun yang Anda inginkan pada tahap ini, namun sangat membantu untuk mengetikkan sesuatu yang deskriptif sehingga Anda dapat mengingat apa yang telah Anda lakukan di masa mendatang.

{% filename %}baris-perintah{% endfilename %}

    $ git commit -m "Changed the HTML for the site."
    

> **Catatan** Pastikan Anda menggunakan tanda kutip ganda di sekitar pesan komit.

Setelah kami selesai melakukannya, kami mengupload (mendorong) perubahan kami ke GitHub:

{% filename %}command-line{% endfilename %}

    $ git push
    

### Menarik kode baru ke PythonAnywhere, dan isi ulang aplikasi web Anda

* Open up the [PythonAnywhere consoles page](https://www.pythonanywhere.com/consoles/) and go to your **Bash console** (or start a new one). Then, run:

{% filename %}command-line{% endfilename %}

    $ cd ~/my-first-blog
    $ git pull
    [...]
    

And watch your code get downloaded. If you want to check that it's arrived, you can hop over to the **Files tab** and view your code on PythonAnywhere.

* Finally, hop on over to the [Web tab](https://www.pythonanywhere.com/web_app_setup/) and hit **Reload** on your web app.

Pembaruan Anda seharusnya hidup! Silakan dan segarkan situs Anda di browser. Perubahan harus terlihat. :)