# Pengantar antarmuka baris perintah

> Bagi para pembaca di rumah: bab ini telah dibahas di video [Your new friend: Command Line](https://www.youtube.com/watch?v=jvZLWhkzX-8).

Ini menarik kan? Anda akan menulis baris kode pertama Anda hanya dalam beberapa menit! :)

**Mari kita perkenalkan Anda ke teman baru pertama Anda: baris perintah!**

Langkah-langkah berikut akan menunjukkan cara menggunakan jendela hitam yang digunakan oleh semua hacker. Mungkin terlihat sedikit menakutkan pada awalnya tapi sebenarnya itu hanya sebuah prompt menunggu perintah dari Anda.

> **Catatan** Perlu diketahui bahwa di sepanjang buku ini kita akan menggunakan istilah 'directory' dan 'folder' secara bergantian tetapi keduanya adalah satu dan sama.

## Apa itu baris perintah?

Jendela, yang biasanya disebut **command line**atau** antarmuka baris perintah**, adalah aplikasi berbasis teks untuk melihat, menangani, dan memanipulasi berkas di komputer Anda. Ini seperti Windows Explorer atau Finder di Mac, tapi tanpa antarmuka grafis. Nama lain dari baris perintah adalah: *cmd*, *CLI*, *prompt*, *konsol* atau *terminal*.

## Buka antarmuka baris perintah

Untuk mulai beberapa percobaan kita perlu untuk membuka baris-perintah antar muka dulu.

{% include â/intro_to_command_line/open_instructions.mdâ %}

## Jendela Perintah

Anda sekarang sebaiknya melihat sebuah window hitam atau putih yang sedang menunggu perintah anda.

<!--sec data-title="Prompt: OS X and Linux" data-id="OSX_Linux_prompt" data-collapse=true ces-->

Bila anda ada di Mac atau Linux, anda akan melihat `$`, seperti ini:

{% filename %}command-line {% endfilename %}

    $
    

<!--endsec-->

<!--sec data-title="Prompt: Windows" data-id="windows_prompt2" data-collapse=true ces-->

Di Windows, mungkin anda melihat `>`, seperti ini:

{% filename %}command-line{% endfilename %}

    >
    

Lihat di bagian atas bagian Linux sekarang â anda akan melihat sesuatu yang sama seperti itu apabila anda masuk ke PhytonAnywhere nanti di tutorial ini.

<!--endsec-->

Setiap perintah akan didahulukan dengan `$` atau `>` dan satu tempat, namun anda tidak perlu mengetiknya. Komputer anda akan melakukannya untuk anda. :)

> Hanya sebuah catatan kecil: dalam alatmh mungkin akan ada seperti `C:\Users\ola>`or ` Olas-MacBook-Air:~ola$` sebelum tanda coba, dan ini artinya 100% OK.

The part up to and including the `$` or the `>` is called the *command line prompt*, or *prompt* for short. It prompts you to input something there.

In the tutorial, when we want you to type in a command, we will include the `$` or `>`, and occasionally more to the left. Ignore the left part and only type in the command, which starts after the prompt.

## Perintah pertama Anda (YAY!)

Let's start by typing this command:

<!--sec data-title="Your first command: OS X and Linux" data-id="OSX_Linux_whoami" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    $ whoami
    

<!--endsec-->

<!--sec data-title="Your first command: Windows" data-id="windows_whoami" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > whoami
    

<!--endsec-->

And then hit `enter`. This is our result:

{% filename %}command-line{% endfilename %}

    $ whoami 
    olasitarska
    

As you can see, the computer has just printed your username. Neat, huh? :)

> Try to type each command; do not copy-paste. You'll remember more this way!

## Hal-hal dasar

Each operating system has a slightly different set of commands for the command line, so make sure to follow instructions for your operating system. Let's try this, shall we?

### Direktori aktif

It'd be nice to know where are we now, right? Let's see. Type this command and hit `enter`:

<!--sec data-title="Current directory: OS X and Linux" data-id="OSX_Linux_pwd" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    $ pwd /
    Users/olasitarska
    

> Note: 'pwd' stands for 'print working directory'.

<!--endsec-->

<!--sec data-title="Current directory: Windows" data-id="windows_cd" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > cd 
    C:\Users\olasitarska
    

> Note: 'cd' stands for 'change directory'. With PowerShell you can use pwd just like on Linux or Mac OS X.

<!--endsec-->

You'll probably see something similar on your machine. Once you open the command line you usually start at your user's home directory.

* * *

### Learn more about a command

Many commands you can type at the command prompt have built-in help that you can display and read! For example, to learn more about the current directory command:

<!--sec data-title="Command help: OS X and Linux" data-id="OSX_Linux_man" data-collapse=true ces-->

OS X and Linux have a `man` command, which gives you help on commands. Try `man pwd` and see what it says, or put `man` before other commands to see their help. The output of `man` is normally paged. Use the space bar to move to the next page, and `q` to quit looking at the help.

<!--endsec-->

<!--sec data-title="Command Help: Windows" data-id="windows_help" data-collapse=true ces-->

Adding a `/?` suffix to most commands will print the help page. You may need to scroll your command window up to see it all. Try `cd /?`.

<!--endsec-->

### List files and directories

So what's in it? It'd be cool to find out. Let's see:

<!--sec data-title="List files and directories: OS X and Linux" data-id="OSX_Linux_ls" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    $ ls 
    Applications 
    Desktop 
    Downloads 
    Music
    ...
    

<!--endsec-->

<!--sec data-title="List files and directories: Windows" data-id="windows_dir" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > dir
     Directory of C:\Users\olasitarska
    05/08/2020 07:28 PM <DIR>      Applications
    05/08/2020 07:28 PM <DIR>      Desktop
    05/08/2020 07:28 PM <DIR>      Downloads
    05/08/2020 07:28 PM <DIR>      Music
    ...
    

> Note: In PowerShell you can also use 'ls' like on Linux and Mac OS X. <!--endsec-->

* * *

### Change current directory

Now, let's go to our Desktop directory:

<!--sec data-title="Change current directory: OS X" data-id="OSX_move_to" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    $ cd Desktop
    

<!--endsec-->

<!--sec data-title="Change current directory: Linux" data-id="Linux_move_to" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    $ cd Desktop
    

Note that the directory name "Desktop" might be translated to the language of your Linux account. If that's the case, you'll need to replace `Desktop` with the translated name; for example, `Schreibtisch` for German.

<!--endsec-->

<!--sec data-title="Change current directory: Windows" data-id="windows_move_to" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > cd Desktop
    

<!--endsec-->

Check if it's really changed:

<!--sec data-title="Check if changed: OS X and Linux" data-id="OSX_Linux_pwd2" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    $ pwd
    /Users/olasitarska/Desktop
    

<!--endsec-->

<!--sec data-title="Check if changed: Windows" data-id="windows_cd2" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > cd
    C:\Users\olasitarska\Desktop
    

<!--endsec-->

Here it is!

> PRO tip: if you type `cd D` and then hit `tab` on your keyboard, the command line will automatically fill in the rest of the name so you can navigate faster. If there is more than one folder starting with "D", hit the `tab` key twice to get a list of options.

* * *

### Create directory

How about creating a practice directory on your desktop? You can do it this way:

<!--sec data-title="Create directory: OS X and Linux" data-id="OSX_Linux_mkdir" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    $ mkdir practice
    

<!--endsec-->

<!--sec data-title="Create directory: Windows" data-id="windows_mkdir" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > mkdir practice
    

<!--endsec-->

This little command will create a folder with the name `practice` on your desktop. You can check if it's there by looking on your Desktop or by running a `ls` or `dir` command! Try it. :)

> PRO tip: If you don't want to type the same commands over and over, try pressing the `up arrow` and `down arrow` on your keyboard to cycle through recently used commands.

* * *

### Exercise!

A small challenge for you: in your newly created `practice` directory, create a directory called `test`. (Use the `cd` and `mkdir` commands.)

#### Solusi:

<!--sec data-title="Exercise solution: OS X and Linux" data-id="OSX_Linux_test_dir" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    $ cd practice
    $ mkdir test
    $ ls
    test
    

<!--endsec-->

<!--sec data-title="Exercise solution: Windows" data-id="windows_test_dir" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > cd practice
    > mkdir test
    > dir
    05/08/2020 07:28 PM <DIR>      test
    

<!--endsec-->

Congrats! :)

* * *

### Clean up

We don't want to leave a mess, so let's remove everything we did until that point.

First, we need to get back to Desktop:

<!--sec data-title="Clean up: OS X and Linux" data-id="OSX_Linux_back" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    $ cd ..
    

<!--endsec-->

<!--sec data-title="Clean up: Windows" data-id="windows_back" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > cd ..
    

<!--endsec-->

Using `..` with the `cd` command will change your current directory to the parent directory (that is, the directory that contains your current directory).

Check where you are:

<!--sec data-title="Check location: OS X and Linux" data-id="OSX_Linux_pwd3" data-collapse=true ces-->

{% filename %}baris-perinah{% endfilename %}

    $ pwd
    /Users/olasitarska/Desktop
    

<!--endsec-->

<!--sec data-title="Check location: Windows" data-id="windows_cd3" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > cd
    C:\Users\olasitarska\Desktop
    

<!--endsec-->

Now time to delete the `practice` directory:

> **Attention**: Deleting files using `del`, `rmdir` or `rm` is irrecoverable, meaning *the deleted files will be gone forever*! So be very careful with this command.

<!--sec data-title="Delete directory: Windows Powershell, OS X and Linux" data-id="OSX_Linux_rm" data-collapse=true ces-->

{% filename %}baris-perintah{% endfilename %}

    $ rm -r practice
    

<!--endsec-->

<!--sec data-title="Delete directory: Windows Command Prompt" data-id="windows_rmdir" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > rmdir /S practice
    practice, Are you sure <Y/N>? Y
    

<!--endsec-->

Done! To be sure it's actually deleted, let's check it:

<!--sec data-title="Check deletion: OS X and Linux" data-id="OSX_Linux_ls2" data-collapse=true ces-->

{% filename %}baris-perintah{% endfilename %}

    $ ls
    

<!--endsec-->

<!--sec data-title="Check deletion: Windows" data-id="windows_dir2" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > dir
    

<!--endsec-->

### Exit

That's it for now! You can safely close the command line now. Let's do it the hacker way, alright? :)

<!--sec data-title="Exit: OS X and Linux" data-id="OSX_Linux_exit" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    $ exit
    

<!--endsec-->

<!--sec data-title="Exit: Windows" data-id="windows_exit" data-collapse=true ces-->

{% filename %}command-line{% endfilename %}

    > exit
    

<!--endsec-->

Cool, huh? :)

## Ringkasan

Here is a summary of some useful commands:

| Perintah (Windows) | Perintah (Mac OS / Linux) | Keterangan                  | Contoh                                             |
| ------------------ | ------------------------- | --------------------------- | -------------------------------------------------- |
| exit               | exit                      | menutup jendela kerja       | **exit**                                           |
| cd                 | cd                        | mengganti direktori         | **cd tes**                                         |
| cd                 | pwd                       | menunjukkan direktori aktif | **cd** (Windows) atau **pwd** (Mac OS / Linux)     |
| dir                | ls                        | daftar direktori/file       | **dir**                                            |
| copy               | cp                        | menyalin berkas             | **copy c:\tes\tes.txt c:\windows\tes.txt**     |
| move               | mv                        | memindakan berkas           | **move c:\tes\tes.txt c:\windows\tes.txt**     |
| mkdir              | mkdir                     | membuat direktori baru      | **mkdir direktorites**                             |
| rmdir (or del)     | rm                        | menghapus berkas            | **del c:\tes\tes.txt**                           |
| rmdir /S           | rm -r                     | menghapus direktori         | **rm -r testdirectory**                            |
| [CMD] /?           | man [CMD]                 | get help for a command      | **cd /?** (Windows) or **man cd** (Mac OS / Linux) |

These are just a very few of the commands you can run in your command line, but you're not going to use anything more than that today.

If you're curious, [ss64.com](http://ss64.com) contains a complete reference of commands for all operating systems.

## Siap?

Let's dive into Python!