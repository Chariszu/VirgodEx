# Komut satırı arayüzüne giriş

> Evden okuyanlar için: Bu bölüm [ içinde anlatıldı. Yeni arkadaşınız: Command Line](https://www.youtube.com/watch?v=jvZLWhkzX-8) video.

Heyecanlı değil mi?! Birkaç dakika içinde ilk kod satırını yazacaksın! :)

**Sizi yeni arkadaşınızla tanıştıralım: komut satırı!**

Gelecek aşamalar size tüm "hacker"ların kullandığı siyah pencerenin nasıl kullanıldığını gösterecek. Başta biraz korkutucu görünebilir fakat bu sadece sizden komut bekleyen bir pencere.

> **Note** Please note that throughout this book we use the terms 'directory' and 'folder' interchangeably but they are one and the same thing.

## Komut satırı nedir?

Genellikle **komut satırı** veya **komut satırı arabirimi** adı verilen pencere, bilgisayarınızdaki dosyaları görmek, düzenlemek ve yönetmek için kullanılan metin tabanlı bir uygulamadır. Bu tıpkı windows gezgini yada mac'teki finder gibi fakat grafiksel arayüzü olmadan. Komut satırının diğer adları: *cmd*, *CLI*, *komut istemcisi*, *konsol* veya *terminal (uçbirim)*dir.

## Komut satırı arabirimini açın

Birkaç deneme yapmak için önce komut satırı arabirimini açmamız gerekir.

<!--sec data-title="Opening: Windows" data-id="windows_prompt" data-collapse=true ces-->

Başlat'a gidin → windows sistemi → Komut istemcisi.

> Daha eski bir windows sistemi için, Başlat menüsü →Tüm programlar → aksesuarlar → Komut istemcisi.

<!--endsec-->

<!--sec data-title="Opening: OS X" data-id="OSX_prompt" data-collapse=true ces-->

Uygulamalar → Araçlar →Terminal.

<!--endsec-->

<!--sec data-title="Opening: Linux" data-id="linux_prompt" data-collapse=true ces-->

Muhtemelen Uygulamalar → Donatılar → Terminal altında olmalı, fakat sistemler arası farklılık gösterebilir. Eğer orada değilse İnternet'te arayın. :)

<!--endsec-->

## İstemci

Şu anda yüksek ihtimalle sizden komut bekleyen siyah ya da beyaz bir ekran görüyor olmalısınız.

<!--sec data-title="Prompt: OS X and Linux" data-id="OSX_Linux_prompt" data-collapse=true ces-->

Eğer Mac veya GNU/Linux kullanıyorsanız, yüksek ihtimalle `$` işareti göreceksiniz, tıpkı bunun gibi:

{% filename %}komut-satırı{% endfilename %}

    $
    

<!--endsec-->

<!--sec data-title="Prompt: Windows" data-id="windows_prompt2" data-collapse=true ces-->

Windows'da ise `>` işareti göreceksiniz, bunun gibi:

{% filename %}komut-satırı{% endfilename %}

    >
    

<!--endsec-->

Tüm komutlar bu işaret ve bir boşluktan sonra gelir fakat bunu yazmak zorunda değilsiniz. Bilgisayarınız bunu sizin için yapacaktır. :)

> Küçük bir not: sizin durumunuzda `C:\Users\ola>` veya `Olas-MacBook-Air:~ ola$` benzeri bir durumda olabilir ve kesinlikle tamamdır.

The part up to and including the `$` or the `>` is called the *command line prompt*, or *prompt* for short. It prompts you to input something there.

Bu kılavuzda bir komut girmeniz istendiğinde, biz `$` veya `>` ekleyeceğiz, genellikle sola doğru. Sol tarafı göz ardı edeiblirsiniz ve işlemi başlatan komutu gireiblirsiniz.

## İlk komutunuz (Yaşasın!)

Let's start by typing this command:

<!--sec data-title="Your first command: OS X and Linux" data-id="OSX_Linux_whoami" data-collapse=true ces-->

{% filename %}komut-satırı{% endfilename %}

    $ whoami
    

<!--endsec-->

<!--sec data-title="Your first command: Windows" data-id="windows_whoami" data-collapse=true ces-->

{% filename %}komut-satırı{% endfilename %}

    > whoami
    

<!--endsec-->

Ve ardından `enter` tuşuna basın. Sonucumuz bu:

{% filename %}komut-satırı{% endfilename %}

    $ whoami zeynep
    

Gördüğünüz gibi bilgisayar kullanıcı adınızı yazdı. Şahane, değil mi ? :)

> Her komutu yazmaya çalışın; kopyala - yapıştır yapmayın. Böylece daha akılda kalıcı olur!

## Temeller

Tüm işletim sistemleri komut satırı için birbirinden biraz farklı komutlar kullanır, bu nedenle işletim sisteminize uygun yönergeleri izlediğinizden emin olun. Deneyelim mi?

### Geçerli Dizin

Nerede olduğumuzu bilmek güzel olurdu, değil mi? Bakalım. Bu komutu yazın ve `enter` tuşuna basın:

<!--sec data-title="Current directory: OS X and Linux" data-id="OSX_Linux_pwd" data-collapse=true ces-->

{% filename %}komut-satırı{% endfilename %}

    $ pwd
    /Users/zeynep
    

> Not: 'pwd'nin anlamı "print working directory" yani "çalışma dizinini yazdır"dır.

<!--endsec-->

<!--sec data-title="Current directory: Windows" data-id="windows_cd" data-collapse=true ces-->

{% filename %}komut-satırı{% endfilename %}

    > cd
    C:\Users\zeynep
    

> Note: 'cd' stands for 'change directory'. With powershell you can use pwd just like on Linux or Mac OS X.

<!--endsec-->

Muhtemelen makinenizde benzeri bir yazı göreceksiniz. Komut satırını açtığınızda genellikle kullanıcınızın ev dizininde başlarsınız.

* * *

### Dosya ve dizinleri listele

Yani içeride ne var? Bilmek harika olurdu. Haydi bakalım:

<!--sec data-title="List files and directories: OS X and Linux" data-id="OSX_Linux_ls" data-collapse=true ces-->

{% filename %}komut-satırı{% endfilename %}

    $ ls
    Uygulamalar
    Masaüstü
    İndirilenler
    Müzik
    ...
    

<!--endsec-->

<!--sec data-title="List files and directories: Windows" data-id="windows_dir" data-collapse=true ces-->

{% filename %}komut-satırı{% endfilename %}

    > dir  Directory of C:\Users\zeynep 
    05/08/2014 07:28 PM <DIR> Uygulamalar 
    05/08/2014 07:28 PM <DIR> Masaüstü 
    05/08/2014 07:28 PM <DIR> İndirilenler 
    05/08/2014 07:28 PM <DIR> Müzik 
    ...
    

> Note: In powershell you can also use 'ls' like on Linux and Mac OS X. <!--endsec-->

* * *

### Geçerli dizini değiştir

Şimdi, haydi Masaüstü dizinimize gidelim:

<!--sec data-title="Change current directory: OS X and Linux" data-id="OSX_Linux_move_to" data-collapse=true ces-->

{% filename %}komut-satırı{% endfilename %}

    $ cd Masaüstü
    

<!--endsec-->

<!--sec data-title="Change current directory: Windows" data-id="windows_move_to" data-collapse=true ces-->

{% filename %}komut-satırı{% endfilename %}

    > cd Masaüstü
    

<!--endsec-->

Gerçekten değişmiş mi bir bakalım:

<!--sec data-title="Check if changed: OS X and Linux" data-id="OSX_Linux_pwd2" data-collapse=true ces-->

{% filename %}komut-satırı{% endfilename %}

    $ pwd
    C:\Users\zeynep\Masaüstü
    

<!--endsec-->

<!--sec data-title="Check if changed: Windows" data-id="windows_cd2" data-collapse=true ces-->

{% filename %}komut-satırı{% endfilename %}

    > cd 
    C:\Users\zeynep\Masaüstü
    

<!--endsec-->

İşte oldu!

> PRO tip: if you type `cd D` and then hit `tab` on your keyboard, the command line will automatically fill in the rest of the name so you can navigate faster. If there is more than one folder starting with "D", hit the `tab` key twice to get a list of options.

* * *

### Dizin oluşturun

Uygulamalı yapmak için masaüstünüzde bir dizin oluşturmaya ne dersiniz? Bu şekilde yapabilirsiniz:

<!--sec data-title="Create directory: OS X and Linux" data-id="OSX_Linux_mkdir" data-collapse=true ces-->

{% filename %}komut-satırı{% endfilename %}

    $ mkdir uygulama
    

<!--endsec-->

<!--sec data-title="Create directory: Windows" data-id="windows_mkdir" data-collapse=true ces-->

{% filename %}komut-satırı{% endfilename %}

    > mkdir uygulama
    

<!--endsec-->

Bu küçük komut masaüstünüzde `uygulama` isimli bir klasör oluşturacaktır. Orada olup olmadığını kontrol etmek için `ls` veya `dir` komutlarını kullanabilirsiniz! Deneyin. :)

> Profesyonel ipucu: Eğer aynı komutları tekrar tekrar yazmak istemiyorsanız, `yukarı ok` ve `aşağı ok` tuşlarına basarak yazdığınız komutlar arasında geçiş yapabilirsiniz.

* * *

### Alıştırma!

A small challenge for you: in your newly created `practice` directory, create a directory called `test`. (Use the `cd` and `mkdir` commands.)

#### Çözüm:

<!--sec data-title="Exercise solution: OS X and Linux" data-id="OSX_Linux_test_dir" data-collapse=true ces-->

{% filename %}komut-satırı{% endfilename %}

    $ cd uygulama
    $ mkdir test
    $ ls
    test
    

<!--endsec-->

<!--sec data-title="Exercise solution: Windows" data-id="windows_test_dir" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > cd uygulama
    > mkdir test
    > dir
    05/08/2014 07:28 PM <DIR>      test
    

<!--endsec-->

Tebrikler! :)

* * *

### Temizlik

Ortalığı dağınık bırakmak istemeyiz, haydi yaptığımız her şeyi silelim.

İlk önce masaüstüne geri dönmemiz gerek:

<!--sec data-title="Clean up: OS X and Linux" data-id="OSX_Linux_back" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    $ cd ..
    

<!--endsec-->

<!--sec data-title="Clean up: Windows" data-id="windows_back" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > cd ..
    

<!--endsec-->

Using `..` with the `cd` command will change your current directory to the parent directory (that is, the directory that contains your current directory).

Nerede olduğunuzu kontrol edin:

<!--sec data-title="Check location: OS X and Linux" data-id="OSX_Linux_pwd3" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    $ pwd
    C:\Users\zeynep\Masaüstü
    

<!--endsec-->

<!--sec data-title="Check location: Windows" data-id="windows_cd3" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > cd 
    C:\Users\zeynep\Masaüstü
    

<!--endsec-->

Şimdi `uygulama` dizinini silme vakti:

> **Attention**: Deleting files using `del`, `rmdir` or `rm` is irrecoverable, meaning *the deleted files will be gone forever*! So be very careful with this command.

<!--sec data-title="Delete directory: Windows Powershell, OS X and Linux" data-id="OSX_Linux_rm" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    $ rm -r uygulama
    

<!--endsec-->

<!--sec data-title="Delete directory: Windows Command Prompt" data-id="windows_rmdir" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > rmdir /S uygulama
    uygulama, Emin misiniz <E/H>? E
    

<!--endsec-->

Bitti! Gerçekten silindiğinden emin olalım:

<!--sec data-title="Check deletion: OS X and Linux" data-id="OSX_Linux_ls2" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    $ ls
    

<!--endsec-->

<!--sec data-title="Check deletion: Windows" data-id="windows_dir2" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > dir
    

<!--endsec-->

### Çıkış

Şimdilik bu kadar! Şimdi komut satırını güvenle kapatabilirsiniz. Bunu "hacker" tarzında yapalım, tamam mı? :)

<!--sec data-title="Exit: OS X and Linux" data-id="OSX_Linux_exit" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    $ exit
    

<!--endsec-->

<!--sec data-title="Exit: Windows" data-id="windows_exit" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > exit
    

<!--endsec-->

Harika, değil mi? :)

## Özet

İşte bazı yararlı komutların özeti:

| Komut (Windows) | Komut (Mac OS - GNU/Linux) | Açıklama                   | Örnek                                             |
| --------------- | -------------------------- | -------------------------- | ------------------------------------------------- |
| çıkış           | çıkış                      | pencereyi kapatır          | **çıkış**                                         |
| cd              | cd                         | dizin değiştir             | **cd test**                                       |
| cd              | pwd                        | show the current directory | **cd** (Windows) or **pwd** (Mac OS / Linux)      |
| dir             | ls                         | dizin/dosyaları listele    | **dir**                                           |
| copy            | cp                         | dosya kopyala              | **copy c:\test\test.txt c:\windows\test.txt** |
| move            | mv                         | dosya taşı                 | **move c:\test\test.txt c:\windows\test.txt** |
| mkdir           | mkdir                      | yeni bir dizin oluştur     | **mkdir testdizini**                              |
| rmdir (or del)  | rm                         | dosyayı silin              | **del c:\test\test.txt**                        |
| rmdir /S        | rm -r                      | klasörü siliniz            | **rm -r testdirectory**                           |

Bu kullanabileceğiniz komutlardan sadece birkaçı, fakat bugün bundan daha fazlasını kullanmayacaksınız.

Eğer merak ediyorsanız, [ss64.com](http://ss64.com) adresinden tüm işletim sistemleri için tüm komutların kullanımına ulaşabilirsiniz.

## Hazır mısınız?

Haydi Python'a giriş yapalım!