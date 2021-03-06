# Kaj je Django?

Django (*džango*) je brezplačno odprtokodno ogrodje, narejeno v programskem jeziku Python. Ogrodje je skupek že napisanih programov, ki ti pomagajo spletne strani graditi hitreje in lažje.

Kot si opazila, obstajajo določeni gradniki, ki jih ima vsaka spletna stran: sistem za registriranje, plošča za upravljanje spletne strani, kontaktni obrazec, sistem za nalaganje datotek in podobno.

Na srečo so se našli ljudje, ki so to ugotovili in so skupaj razvili ogrodja (kot je Django), ki nam nudijo že narejene določene komponente spletne strani.

Ogrodja nas torej rešujejo pred ponovnim odkrivanjem stvari, ki so že dolgo znane oziroma narejene. To jasno precej pospeši postopek razvoja spletnih strani.

## Zakaj potrebujemo ogrodja?

Da bi res dobro razumeli, kaj pravzaprav je Django, si podrobneje oglejmo spletni strežnik. Prva stvar, ki jo mora strežnik vedeti je, da od njega želiš podatke o spletni strani.

Predstavljaj si nabiralnik, ki čaka na prejeta pisma. Točno to počno spletni strežniki. Preberejo pismo in pošljejo odgovor v obliki spletne strani. Ta spletna stran pa mora jasno imeti neko vsebino. Pri ustvarjanju le-te, ti bo pomagal Django.

## Kaj se zgodi, ko nekdo od našega strežnika zahteva spletno stran?

Ko strežnik dobi prošnjo po spletni strani, jo preda Djangu, ta pa poskuša ugotoviti, kaj točno ta prošnja od njega hoče. Najprej pogleda naslov spletne strani in poskuša na podlagi le-tega ugotoviti, kaj se od njega zahteva. This part is done by Django's **urlresolver** (note that a website address is called a URL – Uniform Resource Locator – so the name *urlresolver* makes sense). It is not very smart – it takes a list of patterns and tries to match the URL. Django checks patterns from top to bottom and if something is matched, then Django passes the request to the associated function (which is called *view*).

Predstavljaj si poštarja, ko dostavlja pismo. Ko hodi po ulici, da bi ga dostavil, mora za vsak naslov preveriti, če je isti, kot tisti na pismu. Ko najde pravi naslov, pismo tam odloži. Django deluje povsem enako!

In the *view* function, all the interesting things are done: we can look at a database to look for some information. Recimo, da želi uporabnik spremeniti svoje podatke, ki jih imamo shranjene v bazi. Like a letter saying, "Please change the description of my job." The *view* can check if you are allowed to do that, then update the job description for you and send back a message: "Done!" Then the *view* generates a response and Django can send it to the user's web browser.

The description above is a little bit simplified, but you don't need to know all the technical things yet. Having a general idea is enough.

So instead of diving too much into details, we will start creating something with Django and we will learn all the important parts along the way!