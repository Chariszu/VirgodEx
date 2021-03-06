Túto časť [môžeš preskočiť](http://tutorial.djangogirls.org/en/installation/#install-python) ak nepoužívaš Chromebook. Ak ho používaš, tak tvoja inštalácia bude trochu iná. Môžeš odignorovať zvyšok inštalačného postupu.

### Cloud 9

Cloud 9 is a tool that gives you a code editor and access to a computer running on the Internet where you can install, write, and run the software. Počas tohto tutoriálu Cloud 9 sa bude tvariť ako tvoj *lokálny stroj*. Príkazy budeš zadávať do terminálového rozhrania, tak ako tvoji spolužiaci čo používajú OS X, Ubuntu, alebo Windows, ale tvoj temrinál bude pripojený na počítač, ktorý beží niekde inde a ktorý Cloud 9 pripraví pre teba.

1. Nainštaluj si Cloud 9 z [Chrome web store](https://chrome.google.com/webstore/detail/cloud9/nbdmccoknlfggadpfkmcpnamfnbkmkcp)
2. Hoď na [c9.io](https://c9.io)
3. Založ si učet
4. Klikni na *Create a New Workspace*
5. Pomenuj ho *django-girls*
6. Zvoľ *Blank* (druhý sprava v dolnom riadku čo má oranžové logo)

Teraz by si mala vidieť rozhranie s bočnou lištou, veľké hlavné okno s trochu textu a malé okno v dolnej časti, ktoré vyzerá takto nejak:

{% filename %}Cloud 9{% endfilename %}

    yourusername:~/workspace $
    

This bottom area is your *terminal*, where you will give the computer Cloud 9 has prepared for your instructions. You can resize that window to make it a bit bigger.

### Virtuálne prostredie

Virtuálne prostredie (tiež nazývané virtualenv) je ako súkromná krabica, do ktorej môžeme uložiť úžitočný počítačový kód patriaci projektu na ktorom pracujeme. Používame ich na oddelenie rôznych častí kódu pre rôzne projekty, aby sa nám nepomiešali veci medzi rôznymi projektami.

V termináli, v spodnej časti Cloud 9 rozhrania, spusti nasledovné:

{% filename %}Cloud 9{% endfilename %}

    sudo apt update
    sudo apt install python3.6-venv
    

Ak to ešte stále nefunguje, požiadaj svojho mentora/ku o pomoc.

Ďalej zadaj nasledovné príkazy:

{% filename %}Cloud 9{% endfilename %}

    mkdir djangogirls
    cd djangogirls
    python3.6 -mvenv myvenv
    source myvenv/bin/activate
    pip install django~=1.11.0
    

(všimni si, že v poslednom riadku sme použili vlnovku a za ňou znamienko rovnosti).

### Github

Vytvor si [Github](https://github.com) účet.

### PythonAnywhere

Django Girls tutoriál obsahuje kapitolu o tom čomu sa hovorí nasadenie (Deployment). Je to proces prenesenia kódu, ktorý používa tvoja nová webová aplikácia, na verejne dostupný počítač (ešte nazývaný aj server) aby aj ostatný ludia videli tvoju prácu.

Táto časť je trochu divná, keď pracuješ s týmto tutoriálom na Chromebooku, lebo už používaš počítač, ktorý je na internete (v porovnani s laptopom). Napriek tomu, je stále užitočná, lebo si môžeme predstaviť Cloud 9 pracovné prostredie ako miesto kde sa nachádza rozpracovaná práca a Python Anywhere ako miesto, kde ukážeme našu prácu, ktorá bude hotová.

Teda vytvor si nový Python Anywhere účet na [www.pythonanywhere.com](https://www.pythonanywhere.com).