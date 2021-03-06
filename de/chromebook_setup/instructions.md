Du kannst diese [Section](http://tutorial.djangogirls.org/en/installation/#install-python) direkt überspringen, falls du kein Chromebook benutzt. Wenn du eins benutzt wird deine Installation ein wenig anders sein. Du kannst den Rest der Installationsanweisungen ignorieren.

### Cloud 9

Cloud 9 is a tool that gives you a code editor and access to a computer running on the Internet where you can install, write, and run the software. Während des Tutorials wird dir Cloud 9 als dein *lokaler Rechner* dienen. Du wirst die gleichen Befehle ausführen, wie deine Klassenkameradinnin, die OS X, Ubuntu oder Windows benutzen, jedoch ist dein Terminal verbunden mit einem Computer, der von Cloud 9 gehostet wird.

1. Installiere Cloud 9 aus dem [Chrome web store](https://chrome.google.com/webstore/detail/cloud9/nbdmccoknlfggadpfkmcpnamfnbkmkcp)
2. Gehe auf [c9.io](https://c9.io)
3. Erstelle dir einen Account
4. Klicke auf *Create a New Workspace*
5. Gib ihm den Namen *django-girls*
6. Wähle *Blank* aus( das zweite von links in der untersten Reihe mit dem orangen Logo)

Jetzt solltest du ein Interface mit Sidebar, ein grosses Fenster mit Text und am unteren Rand ein Feld sehen, das wie folgt aussieht:

{% filename %}Cloud 9{% endfilename %}

    deinbenutzername:~/workspace $
    

This bottom area is your *terminal*, where you will give the computer Cloud 9 has prepared for your instructions. You can resize that window to make it a bit bigger.

### Virtuelle Umgebung

Eine virtuelle Umgebung (auch virtualenv genannt) ist ein privater Behälter, in den wir nützlichen Code packen können, um an einem Projekt arbeiten zu können. Wir benutzen diese, um Code für verschiedene Projekte getrennt aufzubewahren, damit diese nicht vermischt werden.

Führe im Terminal den folgenden Code aus( das Terminal befindet sich am unteren Rand des Cloud 9 Interface):

{% filename %}Cloud 9{% endfilename %}

    sudo apt update
    sudo apt install python3.6-venv
    

Wenn du Probleme hast frag deinen Coach nach Hilfe.

Als nächstes führe die folgenden Befehle aus:

{% filename %}Cloud 9{% endfilename %}

    mkdir djangogirls
    cd djangogirls
    python3.6 -mvenv myvenv
    source myvenv/bin/activate
    pip install django~=1.11.0
    

(beachte, dass wir im letzten Befehl eine Tilde gefolgt von einem Gleichheitssymbol benutzen: ~=).

### Github

Erstelle einen [Github](https://github.com) Account.

### PythonAnywhere

Das Django Girls tutorial beinhaltet einen Teil zu Deployment. Beim Deployment nimmst du den Code, der deiner Web Anwendung zu Grunde liegt und packst ihn auf einen öffentlich zugänglichen Computer (Server), damit auch andere Leute deine Arbeit betrachten können.

Dieser Teil ist ein bisschen seltsam, wenn du ihn auf einem Chromebook ausführst, da er bereits nur in der Cloud ist( im Gegensatz zu einem Laptop). Es ist aber trotzdem sinnvoll mitzumachen, wir stellen uns dann einfach unseren Cloud 9 Arbeitsplatz als "work in progress" vor und Python Anywhere als Platz auf dem wir unser Projekt vorführen können.

Deshalb solltest du dich auf [www.pythonanywhere.com](https://www.pythonanywhere.com) für einen Python Anywhere Account anmelden.