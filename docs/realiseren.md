## Manier van aanpak

Tijdens het realiseren van het project is de scrum methode toegepast. Dit betekend dat er gewerkt is in sprints van twee weken. Aan het eind van deze twee weken zijn demo's gegeven aan de mede stagiairs en begeleiders. Daarnaast heeft er iedere vier weken een oplevering voor de belangrijkste stakeholders, Handpicked Labs & Techtenna plaatsgevonden.

In de onderstaande secties zal per oplevering de geplande werkzaamheden, de gerealiseerde werkzaamheden, feedback en reflectie worden toegelicht.

## Oplevering 1: Ontwerp

De eerste oplevering had vooral betrekking op het ontwerp van de applicatie en de machine learning modellen. Meer details over het ontwerp kunnen gevonden worden op de ["Ontwerpen"](ontwerpen.md) pagina.

### Geplande- en afgeronde werkzaamheden

| Sprint # | Werkzaamheden             | Afgerond |
| -------- | ------------------------- | -------- |
| 3        | Data requirements analyse | Ja       |
| 3        | Data verzameling          | Ja       |
| 4        | Model experimenten        | Ja       |
| 4        | Ontwerp                   | Ja       |

### Resultaten
Tijdens het ontwerpen van de applicatie werd duidelijk dat de modellen redelijk lastig waren om te ontwikkelen. Het oorspronkelijke doel was om voor alle service lagen, luchtkwaliteit, energiebesparing en brandveiligheid, modellen te ontwikkelen. Dit doel bleek niet realistisch te zijn.

Om te voorkomen dat de machine learning modellen falen in de productie omgeving was voorgesteld om het doel te beperken tot luchtkwaliteit. Hierdoor kon er meer focus gelegd worden op het ontwikkelen van een systeem wat periodiek de modellen update en evalueert. Wanneer dit goed werkt kan het uitgebreid worden naar de andere service lagen.

### Feedback
Op het eind van de opleveringspresentatie[^1] werd het voorstel gedaan om het doel aan te passen. De reacties hierop waren positief. De stakeholders van Handpicked Labs & Techtenna vonden het een goed idee om klein te beginnen, een robuust systeem te bouwen en daarna uit te breiden.

### Reflectie
Het grootste gedeelte van deze sprints had ik besteed aan de experimenteren. Hierbij was het doel om voor vier verschillende meetwaarden een geschikt model te vinden. Om deze modellen te ontwikkelen waren verschillende technieken onderzocht[^2].

Ik had wat moeite met geschikte modellen ontwikkelen, de ARIMA modellen werkte uiteindelijk het beste maar het is een techniek waar ik nog nooit mee gewerkt had en het bleek lastig om mee te werken. Na wat experimenten uit te voeren vond ik een erg goede bron voor dit type machine learning[^3]. In de toekomst zou het beter zijn als ik eerst dit soort bronnen zoek voordat ik begin met experimenteren.

## Oplevering 2: Integratie ARIMA modellen

Vorige oplevering waren het ontwerp en doelswijzigvoorstel goedgekeurd. Deze oplevering was een eerste versie van dit ontwerp geïmplementeerd.

### Geplande- en afgeronde werkzaamheden

| Sprint # | Werkzaamheden          | Afgerond |
| -------- | ---------------------- | -------- |
| 5        | Pipeline implementatie | Ja       |
| 6        | Front-end aanpassingen | Ja       |

### Resultaten
In de onderstaande afbeelding is te zien hoe de gewenste uitkomst van de implementatie gepland was. In de linker afbeelding is de start situatie te zien, dit is een visualisatie van de luchtvochtigheid van de afgelopen dag. In de gewenste situatie wordt deze visualisatie uitgebreid met de verwachte luchtvochtigheid voor de komende uren.

![Gewenste situatie](images/realisatie/gewenste-situatie.png)

<center><small>Afbeelding 1: Gewenste situatie</small></center>

Om deze situatie te kunnen realiseren is de pipeline zoals deze in het ontwerp is beschreven ontwikkeld. Onderstaand is in een schematische tekening te zien hoe deze pipeline functioneert.

Periodiek wordt er nieuwe data opgevraagt die voorbereid wordt om de ARIMA modellen te updaten. Hierna worden voorspellingen en evaluaties gemaakt die opgeslagen worden in een database. Deze worden beschikbaar gesteld via een API om, bijvoorbeeld, in het front-end gevisualiseerd te worden.

![Pipeline implementatie](images/realisatie/pipeline.png)

<center><small>Afbeelding 2: Pipeline implementatie</small></center>

Onderstaand is te zien hoe deze voorspellingen verwerkt waren in het front-end. Het eind resultaat lijkt redelijk op de gewenste situatie. Er zijn echter wat onderdelen die niet naar verwachting werkte.

1. De voorspelling is slechts een uur in de toekomst.
2. De ARIMA modellen zijn erg groot (>1GB).
3. De voorspellingen zijn niet accuraat genoeg.

<center>![Front-end implementatie](images/realisatie/front-end.png)</center>
<center><small>Afbeelding 3: Front-end implementatie</small></center>

### Feedback
Tijdens de presentatie[^4] van de oplevering werd de onderstaande afbeelding getoond. Hierin is te zien dat de voorspellingen altijd ~ 1 uur achter lijken te lopen. Om dit op te lossen is veel tijd besteed aan het controleren met welke data de modellen werden geüpdatet en voor welke tijdstippen de voorspellingen werden gemaakt. 

Uiteindelijk was, mede door feedback van Marco van Techtenna, de conclusie gemaakt dat dit een eigenschap is van de modellen die zijn toegepast. Tijdens de tweede model experimenten is deze feedback meegenomen.

![Arima evaluatie](images/realisatie/arima-evaluatie.png)

<center><small>Afbeelding 4: ARIMA evaluaties</small></center>

Andere feedback was dat de impact van de visualisatie niet sterk genoeg was om mensen aan te sporen de situatie te veranderen. Aangezien dit de kern van het probleem is moest hiervoor een [tweede iteratie](ontwerpen.md#model-experimenten-versie-2) van de machine learning modellen gedaan worden.

### Reflectie
Tijdens de 5e en 6e sprint was ik vooral bezig met het omzetten van de model experimenten naar een geautomatiseerde pipeline. Hierbij heb ik een API ontwikkelt en het front-end uitgebreid. Via deze API kan het front-end voorspellingen ophalen om te visualiseren.

De voorspellingen die uiteindelijk gevisualiseerd waren maakte niet de gewenste impact en waren niet accuraat genoeg. Hierdoor moest ik meer model experimenten uitvoeren.

Daarnaast had ik voor het implementeren van de applicatie maar een sprint ingepland. Uiteindelijk had ik een complete sprint nodig om alleen de pipeline en API te ontwikkelen en een extra halve sprint om het front-end uit te breiden. Hierdoor verwachte ik in tijdsnood zou kunnen komen.

## Oplevering 3: Iteratie op integratie

Na aanleiding van de feedback op de tweede iteratie waren nieuwe [model experimenten](ontwerpen.md#model-experimenten-versie-2) uitgevoerd. Deze modellen zijn gebruikt om de pipeline en het front-end aan te passen.

### Geplande werkzaamheden

| Sprint # | Werkzaamheden          | Afgerond |
| -------- | ---------------------- | -------- |
| 7        | Model experimenten     | Ja       |
| 8        | Pipeline aanpassingen  | Ja       |
| 8        | Front-end aanpassingen | Ja       |
| 8        | Meldingen weergeven    | Nee      |

### Gerealiseerde werkzaamheden
Voordat begonnen was aan het implementeren van de nieuwe modellen in de pipeline en front-end was er een mock-up gemaakt van de gewenste eind situatie.

<center>
![Mock-up](images/realisatie/mock-up.png)
</center>

<center><small>Afbeelding 5: Mock-up </small></center>

Door de korte termijn voorspellingen een aparte balkgrafiek te visualiseren en de kleur aan te passen wanneer bepaalde waarden worden overschreden wordt er een grotere impact gemaakt. Op deze manier zal de gebruiker aangespoord worden om in te grijpen wanneer de situatie dreigt te verslechteren.

De aanpassingen die aan de pipeline gemaakt moesten worden waren minimaal. Over het algemeen kon de applicatie versimpeld worden omdat het machine learning model niet afhankelijk is van `timestamps`.

Onderstaand is de front-end implementatie van de mock-up van afbeelding 5 te zien. De realisatie was goed gelukt er zijn echter nog wat verbeter punten:

1. Date objecten worden niet goed vertaald naar labels
2. Horizontale belijning is hardcoded.

<center>
![Front-end implementatie](images/realisatie/mock-up-realisatie.png)
</center>
<center><small> Afbeelding 6: Mock-up realisatie </small></center>

### Feedback
Tijdens de presentatie[^5] waren de meningen erg positief. De stakeholders vonden dat de feedback die voorgaande oplevering gegeven was goed verwerkt was.

De manier waarop de voorspelling worden gevisualiseerd is op deze manier beter en spoort aan om in te grijpen wanneer de situatie dreigt te verslechteren.

### Reflectie
Gedurende de zevende en achtste sprints ben ik bezig geweest met model experimenten uitvoeren en de resulterende modellen verwerken in de pipeline en front-end. Hierbij wilde ik de drie problemen die geïdentificeerd waren, zie feedback op oplevering 2, oplossen.

Om niet opnieuw het wiel uit te vinden, iets wat ik voorgaande iteratie wel het geval was, was ik begonnen met get zoeken naar vergelijkbare oplossingen voor het machine learning model. Hierdoor kon ik gerichter werken wat resulteerde in een beter machine learning model. Ik ben erg tevreden met deze manier van werken en zal dit in de toekomst vaker toepassen.

Het verwerken van het model in de pipeline ging vlot. Ik had er rekening mee gehouden dat er veranderingen konden plaatsvinden en kon hier snel op inspelen. Wel is het nog redelijk veel werk om modellen te verwijderen of te vervangen. Wanneer dit product echt gebruikt gaat worden zal hier een oplossing voor gevonden moeten worden.

De front-end implementatie verliep niet zo soepel. Ik ben erg lang bezig geweest om met Chart.js informatieve grafieken te maken. Aangezien ik hier nog geen ervaring mee had ging het erg moeizaam. Daarnaast ging door een update aan het package de date parsing kapot. Momenteel heb ik dit handmatig opgelost maar dit resulteert nog niet in de gewenste visualisaties.

[^1]: [Oplevering Twindle 3.0 Techtenna #1 07-02-21](pdfs/oplevering_1.pdf)
[^2]: [Ontwerpen: Machine learning experimenten versie 1](ontwerpen.md#model-experimenten-versie-1)
[^3]: [Forecasting: Principles and Practice](https://otexts.com/fpp2/index.html)
[^4]: [Oplevering Twindle 3.0 Techtenna #2 04-05-21](pdfs/oplevering_2.pdf)
[^5]: [Oplevering Twindle 3.0 Techtenna # 3 02-06-21](pdfs/oplevering_3.pdf)
