# Hoe het internet werkt

> Voor thuislezers: dit hoofdstuk wordt behandeld in de [How the Internet Works](https://www.youtube.com/watch?v=oM9yAA09wdc) video.
> 
> Dit hoofdstuk is geïnspireerd door de presentatie "How the Internet works" door Jessica McKellar (http://web.mit.edu/jesstess/www/).

Gokje: je gebruikt het Internet zeker elke dag? Maar weet je écht wat er gebeurt als je een adres zoals https://djangogirls.org in je browser ingeeft en op de `enter` knop drukt?

Het eerste wat je moet weten is dat een website gewoon wat bestanden zijn die bij elkaar op een harde schijf staan -- net zoals je films, je muziek of je foto's. Er is echter één dingetje dat uniek is voor websites: ze bevatten computercode genaamd HTML.

Als je nog niet zo bekend bent met programmeren, kan het in het begin lastig zijn om HTML te begrijpen. Je webbrowsers (zoals Chrome, Safari, Firefox, etc.) zijn er anders wel gek op. Web browsers zijn ontworpen om deze code te begrijpen. Ze volgen de instructies in die code en tonen de bestanden waar jouw website uit bestaat, precies zoals jij het wilt.

Net zoals bij elk bestand, moeten we de HTML bestanden ergens op een harde schijf opslaan. Voor het Internet gebruiken we speciale, krachtige computers genaamd *servers*. Ze hebben geen scherm, muis of toetsenbord omdat hun voornaamste doel het opslaan en serveren (aanleveren) van gegevens is (denk aan een serveerster die in een restaurant jouw bestelde drankje komt aanleveren). Dit is waarom ze *servers* worden genoemd - omdat ze jouw data *serveren*.

Ok, maar je wilt weten hoe het internet er uit ziet, nietwaar?

We hebben een plaatje voor jou getekend! Het ziet er zo uit:

![Figuur 1.1](images/internet_1.png)

Ziet er uit als een puinhoop, toch? In feite is het een netwerk van aaneengesloten machines (de hierboven genoemde *servers*). Honderdduizenden machines! Vele, vele kilometers kabels over de hele wereld! Je kunt een onderzeeër kabel kaart website bekijken (http://submarinecablemap.com) om te zien hoe ingewikkeld het net is. Hier is een screenshot van de website:

![Figuur 1.2](images/internet_3.png)

Het is fascinerend, nietwaar? Maar het is uiteraard niet mogelijk om een kabel te hebben tussen elk apparaat dat verbonden is met het internet. Dus, om een machine te bereiken (bijvoorbeeld degene waarop https://djangogirls.org staat), moeten we een verzoek versturen dat langs vele, vele verschillende machines gaat.

Het ziet er zo uit:

![Figuur 1.3](images/internet_2.png)

Stel je voor dat wanneer je naar https://djangogirls.org een brief typt waarin staat: "Beste Django Girls, ik wil de djangogirls.org website zien. Stuur die naar me, alsjeblieft! "

Je brief gaat naar het dichtsbijzijnde postkantoor. Dan gaat 'ie naar een ander postkantoor iets dichter bij de bestemming, dan naar een volgend postkantoor nog wat dichterbij, en weer één daaropvolgend, totdat de brief afgeleverd kan worden op diens eindbestemming. Het bijzondere is nu dat als je meerdere brieven stuurt (*data pakketten*) naar dezelfde bestemming, ze via héél verschillende postkantoren (*routers*) kunnen gaan. Dit hangt er maar vanaf hoe ze verdeeld worden op ieder postkantoor.

![Figuur 1.4](images/internet_4.png)

Zo werkt het - je verstuurt een bericht en verwacht een antwoord. In plaats van pen en papier gebruik je bytes met gegevens, maar het idee is hetzelfde!

In plaats van adressen met een straatnaam, woonplaats, postcode en landnaam gebruiken we IP-adressen. Je computer vraagt eerst aan het DNS (Domein Naam Systeem) om 'djangogirls.org' om te zetten naar een IP-adres. Dat werkt een beetje als een ouderwets telefoonboek waarin je de naam kunt opzoeken van de persoon die je wilt bellen en dan diens telefoonnummer en adres vindt.

Als je een brief verstuurt, moet die brief gekenmerkt worden met een adres, een postzegel en dergelijke om goed af te kunnen leveren. Je gebruikt ook een taal die de ontvanger begrijpt, nietwaar? Datzelfde geldt voor de *data pakketten* die je verzendt om een website te zien. We gebruiken een werkvoorschrift dat HTTP (Hypertext Transfer Protocol) heet.

In principe moet je, als je een web site hebt, een *server* (machine) hebben waarop die web site staat. Als de *server* een inkomend *verzoek* ontvangt (in een brief), verstuurt hij de web site terug (in een andere brief).

Aangezien dit een Django tutorial is, vraag je je misschien af wat Django dan doet. Als je een antwoord verzendt, wil je niet altijd precies hetzelfde naar iedereen sturen. Een persoonlijke touch toevoegen aan de brieven is veel fijner, vooral voor degene die jou net aangeschreven had, toch? Django helpt je met het opstellen van deze persoonlijke, interessante brieven. :)

Genoeg gekletst nu; tijd om iets te maken!