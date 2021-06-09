## Introductie

Tijdens het achtste semester van de studie ICT & Software Engineering heeft mijn afstudeerstage bij Handpicked Agencies plaatsgevonden. Het project waar ik aan gewerkt heb is de digital twin genaamd [Twindle](https://demo.twindle.io/).

Dit product is vorig jaar ontwikkeld door [Handpicked Labs](https://labs.handpickedagencies.com/) in samenwerking met [Techtenna](https://techtenna.com/). Het doel van de applicatie was om de luchtkwaliteit, energieverbruik en brandveiligheid van gebouwen in kaart te brengen door middel van een digitale kopie van het gebouw.

### Probleemstelling

Twindle meet, onder andere, de temperatuur, luchtvochtigheid en CO2 en bepaalt of er voldaan wordt aan de gestelde luchtkwaliteitseisen. Mede door COVID-19 is de luchtkwaliteit in een ruimte steeds belangrijker geworden. Slechte luchtkwaliteit kan ernstige gezondheidsproblemen veroorzaken. Door de luchtkwaliteit te voorspellen en meldingen te maken wanneer deze in gevaar is willen we de leefbaarheid van ruimten verbeteren.

### Hoofd- en deelvragen

Tijdens het gehele project is onderzoek verricht worden volgens het [Development Oriented Triangulation (DOT) framework](https://ictresearchmethods.nl/The_DOT_Framework). Dit framework bestaat uit verschillende onderzoekscategorieën die gecombineerd moeten worden om tot een valide conclusie te komen.

Om het onderzoek te structureren is er een hoofdvraag en meerdere deelvragen opgesteld. Tijdens de conclusie zullen deze hoofd- en deelvragen beantwoord worden.

**Hoofdvraag** <br>

> **_Hoe kan Twindle uitgebreidt worden om een hoge luchtkwaliteit in ruimten te garanderen?_**

**Deelvragen** <br>
Onderstaand zijn de deelvragen opgesomd. In het projectplan is een overzicht[^1] te vinden waarin wordt toegelicht welke onderzoeksmethoden gebruikt zijn om de vraag te beantwoorden.

- Wie zijn de gebruikers van Twindle?
- Welke data is benodigd om luchtkwaliteit te voorspellen
- Hoe kan machine learning worden toegepast om luchtkwaliteit te voorspellen?
- Met welke ethische aspecten dient rekening gehouden te worden? En op welke manier?
- Hoe kunnen machine learning modellen gekoppeld worden aan Twindle?

### Doelstelling

> **_Vanaf 18-06 zullen de gebruikers van Twindle meldingen kunnen ontvangen wanneer slechte luchtkwaliteit wordt verwacht. Het machine learning model wat hiervoor wordt toegepast zal een "recall" en "precision" score hebben van minimaal 90%._**

Een verdere beschrijving van het doel kan in hoofdstuk _1.2.1 SMART_ [^2] van het projectplan gevonden worden.

## Leeswijzer

Tijdens het afstuderen is gewerkt aan de ICT competenties zoals beschreven in de [HBO-I domeinbeschrijving](https://hboidomein-212218.appspot.com/pdf?template=https://hboidomein-212218.appspot.com/template.html&deep=true&full=true&lang=NL&skipcache=&viewport=1156x818&url=https://hboidomein-212218.appspot.com/pdfdoc). In de onderstaande secties zal per competentie kort samengevat worden hoe deze aangetoond is.

### Analyseren

Voordat begonnen was aan het ontwikkelen van het product was het belangrijk om te weten wie er bij betrokken waren en wat zij belangrijk vonden. Hiervoor is tijdens het opstellen van het project is de volgende vraag gesteld:

> **_Wie zijn de gebruikers van Twindle?_**

Door middel van een [stakeholders analyse](analyseren.md#stakeholders-analyse) is deze vraag beantwoord. Hierna is verder onderzocht wat de behoeften van deze stakeholders waren door gebruik te maken van [story mapping technieken](analyseren.md#story-mapping).

Daarnaast werd er geanalyseerd welke data de Twindle applicatie tot nu toe heeft verzameld in een [exploratory data analyse](analyseren.md#exploratory-data-analyse). De resultaten van deze analyses zijn verwerkt in requirements. Deze zijn opgesplitst in de volgende categorieën:

- [Software](analyseren.md#software-requirements)
- [Data](analyseren.md#data-requirements)
- [Machine learning](analyseren.md#machine-learning-requirements)

Deze requirements onderzoeken hebben geleidt tot een antwoord op de vraag:

> **_Welke data is benodigd om luchtkwaliteit te voorspellen?_**

### Ontwerpen

Uit de verschillende analyses was gebleken dat het belangrijk is dat personen snel geinformeerd worden wanneer de luchtkwaliteit dreigt te verslechteren. De eerste stap hierin is om de meetwaarden die samen de luchtkwaliteit vormen te voorspellen. Hiervoor is de volgende vraag gesteld:

> **_Hoe kan machine learning worden toegepast om luchtkwaliteit te voorspellen?_**

Tijdens de [model experimenten](ontwerpen.md#model-experimenten-versie-1) zijn meerdere machine learning technieken onderzocht en getest om een antwoord op deze vraag te kunnen geven.

De tweede stap was om een systeem te ontwerpen waardoor de machine learning modellen up-to-date blijven, periodiek nieuwe voorspellingen maken en deze toegankelijk maken voor, bijvoorbeeld, front-end applicaties. Dit ontwerp geeft antwoord de de vraag:

> **_Hoe kunnen machine learning modellen gekoppeld worden aan Twindle?_**

Na het ontwerp te hebben geïmplementeerd was dit [opgeleverd](realiseren.md#oplevering-2-integratie-arima-modellen). Hieruit bleek dat er meerdere problemen waren met de machine learning modellen die opgelost moesten worden. Hiervoor is een [tweede iteratie](ontwerpen.md#model-experimenten-versie-2) van de model experimenten gedaan.

### Realiseren <br>

Om het ontwerp te realiseren was iteratief gewerkt. Iedere vier weken heeft er een oplevering plaatsgevonden voor de stakeholders van Handpicked Labs en Techtenna. 

Tijdens de [eerste oplevering](realiseren.md#oplevering-1-ontwerp) was het ontwerp besproken met de stakeholders, zij waren allemaal akkoord met de beslissingen die daar gemaakt werden. 

Daarnaast werd voorgesteld om het doel te wijzigen. Tot dit moment in het project was het doel om voor alle servicelagen (luchtkwaliteit, duurzaamheid en brandveiligheid) machine learning modellen te ontwikkelen. Voorgesteld was om de focus te leggen op de luchtkwaliteit, daar een robuust systeem voor te bouwen en daarna uit te breiden naar de rest van de servicelagen. De stakeholders gingen hiermee akkoord.   

Hierna was tijdens de [tweede oplevering](realiseren.md#oplevering-2-integratie-arima-modellen) het resultaat van de ARIMA modellen gepresenteerd. Hier bleken nog enkele problemen mee te zijn:

1. Voorspellingen waren op een te kort termijn 
2. Modellen waren te groot (> 1GB)
3. Voorspelligen waren niet accuraat genoeg.
   
Het doel was om deze problemen om te lossen voor de [derde oplevering](realiseren.md#oplevering-3-iteratie-op-integratie). Hiervoor was een tweede iteratie van de [model experimenten](ontwerpen.md#model-experimenten-versie-2) uitgevoerd wat resulteerde in verbeterde modellen. Deze loste de problemen van de voorgaande oplevering op en de stakeholders waren tevreden over de gemaakte veranderingen.

### Adviseren <br>

Tijdens de realisatie zijn er meerdere onderwerpen waar adviezen over gemaakt zijn:

- Aanpak & scope
- Volgende stappen
- Ethische gevolgen

> **_Met welke ethische aspecten dient rekening gehouden te worden? En op welke manier?_**

### Onderhouden <br>

- Versie beheer
- Planning
- Feedback

## Behaalde resultaten

Hier komt een overzicht van de behaalde resultaten zodra dit het project afgerond is.

[^1]: [Projectplan 1.4.1 & 1.4.2](./pdfs/project_plan.pdf#page=13) _blz. 13 - 15_
[^2]: [Projectplan 1.2.1 SMART](./pdfs/project_plan.pdf#page=8) _blz. 8 - 9_
[^3]: [Projectplan 1.4 Onderzoeksvragen](./pdfs/project_plan.pdf#page=12) _blz. 12 - 15_
[^4]: [Projectplan 1.5 Eindproducten](./pdfs/project_plan.pdf#page=8) _blz. 16 - 17_
