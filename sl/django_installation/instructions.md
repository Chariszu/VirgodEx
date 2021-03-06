> Part of this section is based on tutorials by Geek Girls Carrots (https://github.com/ggcarrots/django-carrots).
> 
> Part of this section is based on the [django-marcador tutorial](http://django-marcador.keimlink.de/) licensed under the Creative Commons Attribution-ShareAlike 4.0 International License. Vodič django-marcador tutorial je avtorsko delo Markus Zapke-Gründemann et al.

## Virtualno okolje

Preden namestiš Django, se boš seznanila z zelo uporabnim orodjem, ki ti bo omogočilo vzpostavitev urejenega delovnega prostora. Ta korak sicer ni obvezen, vendar pa je zelo priporočljiv. Uporaba virtualnega okolja nam dolgoročno prihrani veliko težav!

Ustvarimo torej **virtualno okolje** (angl. virtual environment ali *virtualenv*). Navidezno/virtualno okolje bo omejilo spremembe, ki jih bomo naredili v Pythonu in Djangu, le na naš projekt. To pomeni, da omenjene spremembe ne bodo vplivale na noben drug projekt, ki ga imaš morda tudi na računalniku. To se zdi smiselno.

Za začetek najdi imenik, v katerem želiš ustvariti `virtualno okolje`. Recimo tvoj domači imenik. On Windows, it might look like `C:\Users\Name` (where `Name` is the name of your login).

> **NOTE:** On Windows, make sure that this directory does not contain accented or special characters; if your username contains accented characters, use a different directory, for example, `C:\djangogirls`.

V tem vodiču bomo v tvojem domačen imeniku ustvarili nov imenik `djangogirls`:

{% filename %}command-line{% endfilename %}

    $ mkdir djangogirls
    $ cd djangogirls
    

Zdaj bomo ustvarili navidezno okolje `myvenv`. Splošen ukaz zgleda nekako takole:

{% filename %}command-line{% endfilename %}

    $ python3 -m venv myvenv
    

<!--sec data-title="Virtual environment: Windows" data-id="virtualenv_installation_windows"
data-collapse=true ces-->

To create a new `virtualenv`, you need to open the command prompt and run `python -m venv myvenv`. It will look like this:

{% filename %}command-line{% endfilename %}

    C:\Users\Name\djangogirls> python -m venv myvenv
    

Where `myvenv` is the name of your `virtualenv`. Ubistvu si lahko zmisliš katerokoli ime, ki vsebuje le male črke in ne vsebuje presledkov, naglasov in podobnih posebnih znakov. It is also good idea to keep the name short – you'll be referencing it a lot!

<!--endsec-->

<!--sec data-title="Virtual environment: Linux and OS X" data-id="virtualenv_installation_linuxosx"
data-collapse=true ces-->

We can create a `virtualenv` on both Linux and OS X by running `python3 -m venv myvenv`. It will look like this:

{% filename %}command-line{% endfilename %}

    $ python3 -m venv myvenv
    

myvenv je ime tvojega virtualnega okolja. Ubistvu si lahko zmisliš katerokoli ime, ki vsebuje le male črke in ne vsebuje presledkov, naglasov in podobnih posebnih znakov. It is also a good idea to keep the name short as you'll be referencing it a lot!

> **NOTE:** On some versions of Debian/Ubuntu you may receive the following error:
> 
> {% filename %}command-line{% endfilename %}
> 
>     The virtual environment was not created successfully because ensurepip is not available.  On Debian/Ubuntu systems, you need to install the python3-venv package using the following command.
>        apt-get install python3-venv
>     You may need to use sudo with that command.  After installing the python3-venv package, recreate your virtual environment.
>     
> 
> In this case, follow the instructions above and install the `python3-venv` package: {% filename %}command-line{% endfilename %}
> 
>     $ sudo apt-get install python3-venv
>     
> 
> **NOTE:** On some versions of Debian/Ubuntu initiating the virtual environment like this currently gives the following error:
> 
> {% filename %}command-line{% endfilename %}
> 
>     Error: Command '['/home/eddie/Slask/tmp/venv/bin/python3', '-Im', 'ensurepip', '--upgrade', '--default-pip']' returned non-zero exit status 1
>     
> 
> To lahko rešiš tako, da raje uporabiš ukaz `virtualenv`.
> 
> {% filename %}command-line{% endfilename %}
> 
>     $ sudo apt-get install python-virtualenv
>     $ virtualenv --python=python3.6 myvenv
>     
> 
> **NOTE:** If you get an error like
> 
> {% filename %}command-line{% endfilename %}
> 
>     E: Unable to locate package python3-venv
>     
> 
> then instead run:
> 
> {% filename %}command-line{% endfilename %}
> 
>     sudo apt install python3.6-venv
>     

<!--endsec-->

## Delo z virtualnim okoljem

S prejšnjimi ukazi si ustvarila imenik z imenom `myvenv` (oziroma z imenom, ki si ga izbrala sama), ki predstavlja virtualno okolje (v bistvu je to zgolj kup imenikov in datotek).

<!--sec data-title="Working with virtualenv: Windows" data-id="virtualenv_windows"
data-collapse=true ces-->

Virtualno okolje zaženeš takole:

{% filename %}command-line{% endfilename %}

    C:\Users\Name\djangogirls> myvenv\Scripts\activate
    

> **NOTE:** on Windows 10 you might get an error in the Windows PowerShell that says `execution of scripts is disabled on this system`. In this case, open another Windows PowerShell with the "Run as Administrator" option. Then try typing the following command before starting your virtual environment:
> 
> {% filename %}command-line{% endfilename %}
> 
>     C:\WINDOWS\system32> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
>         Execution Policy Change
>         The execution policy helps protect you from scripts that you do not trust. Changing the execution policy might expose you to the security risks described in the about_Execution_Policies help topic at http://go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy? [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): A
>     

<!--endsec-->

<!--sec data-title="Working with virtualenv: Linux and OS X" data-id="virtualenv_linuxosx"
data-collapse=true ces-->

Virtualno okolje zaženeš takole:

{% filename %}command-line{% endfilename %}

    $ source myvenv/bin/activate
    

Ne pozabi nadomestiti imena `myvnev` z imenom, ki se ga izbrala!

> **OPOMBA:** če `source` noče delovati, poskusi naslednje:
> 
> {% filename %}command-line{% endfilename %}
> 
>     $ . myvenv/bin/activate
>     

<!--endsec-->

You will know that you have `virtualenv` started when you see that the prompt in your console is prefixed with `(myvenv)`.

Ko delaš z virtualnim okoljem, je privzeta različica `pythona` enaka tisti, ki jo ima virtualno okolje. Zato lahko vedno uporabljaš ukaz `python` namesto `python3`.

OK, teren je pripravljen. Končno lahko namestimo Django!

## Namestitev Djanga

Now that you have your `virtualenv` started, you can install Django.

Before we do that, we should make sure we have the latest version of `pip`, the software that we use to install Django:

{% filename %}command-line{% endfilename %}

    (myvenv) ~$ pip install --upgrade pip
    

Then run `pip install django~=1.11.0` (note that we use a tilde followed by an equal sign: `~=`) to install Django.

{% filename %}command-line{% endfilename %}

    (myvenv) ~$ pip install django~=1.11.0
    Collecting django~=1.11.0
      Downloading Django-1.11.3-py2.py3-none-any.whl (6.8MB)
    Installing collected packages: django
    Successfully installed django-1.11.3
    

<!--sec data-title="Installing Django: Windows" data-id="django_err_windows"
data-collapse=true ces-->

> If you get an error when calling pip on Windows platform, please check if your project pathname contains spaces, accents or special characters (for example, `C:\Users\User Name\djangogirls`). If it does, please consider using another place without spaces, accents or special characters (suggestion: `C:\djangogirls`). Create a new virtualenv in the new directory, then delete the old one and try the above command again. (Moving the virtualenv directory won't work since virtualenv uses absolute paths.)

<!--endsec-->

<!--sec data-title="Installing Django: Windows 8 and Windows 10" data-id="django_err_windows8and10"
data-collapse=true ces-->

> Your command line might freeze after when you try to install Django. If this happens, instead of the above command use:
> 
> {% filename %}command-line{% endfilename %}
> 
>     C:\Users\Name\djangogirls> python -m pip install django~=1.11.0
>     

<!--endsec-->

<!--sec data-title="Installing Django: Linux" data-id="django_err_linux"
data-collapse=true ces-->

> Če dobiš napako, ko zaženeš ukaz pip na operacijskem sistemu Ubuntu 12.04, poženi ukaz `python -m pip install -U --force-reinstall pip`.

<!--endsec-->

To je to! Zdaj si (končno) pripravljena, da narediš svojo Django aplikacijo!