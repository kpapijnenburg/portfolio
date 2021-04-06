# Feedback

## Project plan

**Sjoerd - 10-02-2021** <br>
In de introductie van het project plan stond dat er een Digital Twin ontwikkeld was voor het kantoorpand van Handpicked Agencies. Sjoerd had de opmerking dat er tevens een implementatie gemaakt is voor in hotelomgevingen. De introductie is herschreven zodat deze niet specifiek vermeld waar Digital Twins actief zijn.

Daarnaast had Sjoerd nog feedback op de doelstelling. Ik had opgeschreven dat de Twindle applicatie uitgebreid kan worden zodat personen,bijvoorbeeld, de verwarming aan kunnen zetten zodra zij zien dat het te koud wordt. Volgens Sjoerd zou ik hier groter kunnen denken. Na aanleiding van deze feedback heb ik het doel vergroot naar grootschalige verbetering van de luchtkwaliteit waardoor de beleving van de personen in het gebouw vergroot wordt.

**Samet - 19-02-2021** <br>
Ik had beschreven dat we de applicatie wilde uitbreiden zodat deze informatie uit het verleden en toekomst kan tonen. Volgens Samet kon dit beter verwoord worden. Na aanleiding van deze feedback heb ik beter beschreven welke meetwaarden voorspeld gaan worden.

Daarnaast had ik Samet een vraag gesteld waarom er gekozen was om TVOC waarde bij te meten en te gebruiken als luchtkwaliteit indicator. Zijn reactie hierop was dat voor luchtkwaliteit er meer nodig is dan alleen TVOC. Een combinatie van Co2, TVOC, Luchtvochtigheid en temperatuur zegt iets over de luchtkwaliteit. Tijdens de rest van het project kan ik er rekening mee houden dat deze waarden gebruikt worden voor luchtkwaliteit. 

**Bartosz - 01-03-2021** <br>
"Het is aan mij om te onderzoeken hoe Twindle het meest effectief ingezet kan worden voor deze implementatie" het lijkt mij heel breed, kan je ket beter scopen? het gaat over softwre toch en niet business modelleren etc. je gaat een bestaande applicatie aanpassen zodat het model van een hotel van gemaakt kan worden? Wat is de baat van jouw project voor de handipicked en voor de hotel zelf?

Het blijft nog steeds niet helder wat de kern van het probleem is dat je gaat oplosseen en wie erbij welke baat zal hebben (gecontrasteerd met de gebreken van de al bestaande oplossing). je deed een analyze in 1.2.1 op detail niveau, maar voeg die globale informatie wel toe in het begin van je document zoadt de lezer weet wat gaat dit project aanpakken.

- Introductie aangepast zodat hier een betere koppeling is tussen het probleem en de huidige implementatie. 

1.3 gelimiteerde kennis van web hoort in risicos en niet hier. ook zijn de software aspecten van je project mogelijk hier al te vatten. je gaat backend en frontend werk doen, testen, data cleaning etc. Wat zijn de doelen dat je vanuit EDA wilt halen (hoe en waarvoor hoop je de restulaten ervan in te zetten in je daaropvolgende project delen?)?

- Begrenzing vastgesteld
- SW aspecten toegevoegd aan scope en randvoorwaarden
- Gelimiteerd web kennis verplaats naar risico's

1.4 als je naar die methodiek kijkt dan kan je hieruit ook een taal van deliverables nemen en expliciet noemen/verwerken in de rest van je document. bv. data requirements- ga je die opstellen of is dat niet in scope? deployments, hoe zie je dat voor zich?

1.5 "zijn er ethische..." vermijd ja nee vragen. better "welke"
voeg ook iets toe over evaluatie van je oplossing, dat weet je nu nog niet zeker hoe dat het beste kan gebeuren.Weet je ook genoeg van air quality om te kunnen bepalen hoe en wat te meten en wat is goed en wat niet?

1.6 Tests niet vergeten, verder hoe worden je machine learning modellen getrained en geevalueerd is ook iets dat je gaat beschrijven misschien ga je er zelf een pipeline voor bouwen. Hoe ga je verschillende experimenten rapporteren en bijhouden?

- Model evaluatie beschreven
- Integratie verduidelijkt

3.2 Hoeveel interaties van het IBM process ga je uitvoeren? misschien helpt het bij het planing.
probeer ook wat project specifieker te zijn in je planing (bv. welke onderzoeken ga je afronden in welke sprints?

- Producten en onderzoeken aan planning gekoppeld
- Verduidelijkt dat er twee iteraties van het IBM process uitgeovoerd gaan worden.

4.1 Hoe ga je de integratie testen? En de software stukken? Automatisch, met hand?

- Test uitleg toegevoegd

Over je vraag voor 4.3  Ik weet niet precies wat ik hier bij moet invullen. Zijn dit onderdelen zoals CI/CD en dergelijke? -> Ja, hoe je gaat omgaan met versie beheer maar ook deployments en bijhoordende configuraties. denk ook aan change management, wat en waar PR's en CR's, inhoud van je sprints hoe bijhouden? etc.

- 4.3 Versie beheer, deployment confgiguratie toegevoegd

**Bartosz 09-03-2021** <br>
Ik zou nog duidelijker de data preparation/cleaning opnemen in je PID.

- Scope uitgebreid met data verzameling en voorbereiding
- Scope randvoorwaarden verduidelijkt.

Verder zie ik nog steeds " Zijn er ethische aspecten" ipv welke. heb je de laatste versie geupload?

- Deelvraag 4: "Zijn er..." naar "Met welke..."

Voeg ook een deelvraag over air quality toe. Je hebt daar niet genoeg kennis van om te kunnen evalueren dat wat je doet goed is. Weet je ook genoeg van air quality om te kunnen bepalen hoe en wat te meten en wat goed is en wat niet?

- Deelvraag 3 specifiek op luchtkwaliteit gericht.

## Stakeholders analyse 

## Exploratory data analyse

## Machine learning modellen 1.0

## Integratie ontwerp
