## Model experimenten versie 1

Voor de uitbreiding van het Twindle project zullen machine learning modellen gebruikt worden om de luchtkwaliteit te voorspellen. Dit zullen modellen zijn voor luchtvochtigheid, temperatuur, CO2 en TVOC.

### Eisen

Vanuit de product owner is het doel gesteld dat de modellen tenminste 90% accuraat moeten zijn. De meetwaarden die gemodelleerd dienen te worden zijn continu en niet uit te
drukken in procent accuracy. R-squared score kan gebruikt worden voor dit soort modellen.

Het geeft een waarde tussen 0.0 en 1.0 aan wat geïnterpreteerd kan worden als een percentage. Wanneer een R2 Score van 0.9 wordt behaald zal het model aan de eisen voldoen.

Om de modellen onderling met elkaar te vergelijken zal, naast r-squared, ook de root mean squared error scoring methode worden gebruikt. Deze methode resulteert in een waarde in dezelfde eenheid als het target. Hierdoor kan gezien worden in hoeverre de gemiddelde voorspelling zal afwijkt van de realiteit.

### Beschrijving & resultaten

Om een betere indicatie te krijgen wat voor soort modellen toegepast kunnen worden is extra data exploratie verricht[^1]. Hieruit is gebeleken dat de data seizoensgebonden- en niet stationair is. Dit betekend dat standaard least-squares regressie niet toegepast kan worden, dit namelijk leiden tot sterke overfitting.

Na onderzoek[^2] te hebben gedaan naar modellering technieken voor dit soort data is besloten om met de volgende modellen te experimenteren:

- Lineare Regressie
- Exponential Smoothing
- Autoregressive Integrated Moving Average

**Lineaire Regressie** <br>
Om lineare regressie toe te kunnen passen moet de data geen autocorrelaties bevatten en stationair zijn. Hiervoor zijn differencing, het verschil tussen een meting en de voorgaande meting, technieken toegepast. Daarnaast is er een techniek[^3] gebruikt om de opeenvolgende data voor te bereiden voor gebruik in de algoritmen.

De volgende modellen zijn toegepast:

- [LinearRegression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html) (LR)
- [KNearestNeigbors](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsRegressor.html) (KNN)
- [RandomForestRegressor](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html) (RF)

![Gemiddelde R-squared per meetwaarde en model](images/linear-regression-results.png)

<center>_Afbeelding 1: Gemiddelde R-squared per meetwaarde en model_</center>

Aan de bovenstaande afbeeldingen is het volgende af te leiden:

- Geen enkel linear regressie model behaalt de eis van 0.9 r-squared.
- De lage of negatieve r-squared scores betekenen dat er geen patronen gevonden zijn.

Waarschijnlijk missen er nog cruciale features. In verder iteraties zal dit verder onderzocht worden.

**Exponential Smoothing** <br>
Voorspelling die gemaakt worden met exponential smoothing methoden zijn gemiddelden van eerdere waarnemingen, waarbij de eerdere waarnemingen zwaarder meewegen dan de ouderen.

De Holt-Winters seasonal methode is gebruikt om te kunnen profiteren van de trends en seizoensgebondenheid die aanwezig zijn in de data. Het `statsmodel` package heeft hier de volgende implementatie van:

- [ExponentialSmoothing](https://www.statsmodels.org/dev/generated/statsmodels.tsa.holtwinters.ExponentialSmoothing.html)

![Exponential smoothing per meetwaarde](images/exponential-smooting.png)

<center>_Afbeelding 2: Exponential Smoothing resultaten per meetwaarde_</center>

Dit soort modellen lijken op het begin de trend goed te volgen. Na ongeveer een of twee uur beginnen ze echter steeds minder accuraat te worden en overschieten ze vaak het doel. Voor meetwaarden die afhankelijk zijn van andere factoren, zoals luchtvochtigheid en temperatuur, zijn deze modellen minder accuraat.

**Autoregressive Integrated Moving Average** <br>
Autoregressive integrated moving average (ARIMA) modellen maken gebruik van een combinatie van de volgende technieken.

- Autoregression (AR)
- Moving average (MA)

Het kan gebruik maken van de trends, autocorrelatie en seizoensgebondenheid van de data. In dit geval is er gekozen voor de `auto_arima` methode van het `PMDARIMA` package. Hierbij worden meerdere combinaties van het model uitgetests en uiteindelijk het hoogst scorende model opgeslagen.

![ARIMA resultaten per meetwaarden](images/arima.png)

Net als bij de Exponential Smoothing modellen presteert deze techniek beter op de TVOC en CO2 meetwaarden. Deze waarden hebben ook een wekelijkse seizoensgebondenheid die momenteel nog niet gemodelleerd is. Wanneer er meer data beschikbaar is zal dit meegenomen worden in het model wat waarschijnlijk resulteert in hogere scores.

### Bevindingen
Momenteel is er nog geen enkel model wat de gestelde eis van 0.9 r-squared score behaalt. Wel komen de ARIMA modellen redelijk dicht in de buurt. Met deze reden is er voor gekozen om de eerste iteratie van de implementatie deze modellen toe te passen.

## Architectuur

## Model experimenten versie 2

[^1]: [Model experimenten rapport - versie 1: Gegevensoverzicht](pdfs/model_experimenten_v1.pdf#page=3) _blz. 3 t/m 9_
[^2]: [Model experimenten rapport - versie 1: Bronnen](pdfs/model_experimenten_v1.pdf#page=21) _blz. 21_
[^3]: [Model experimenten rapport - versie 1: Gegevensvoorbereiding](pdfs/model_experimenten_v1.pdf#page=13) _blz. 12_
