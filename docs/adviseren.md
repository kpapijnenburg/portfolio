## Data

### Missende gegevens

Tijdens de [data exploratie](analyseren.md#missende-gegevens) was opgemerkt dat niet in iedere ruimte dezelfde data bijgehouden werd, zie tabel 1. Dit heeft ervoor gezorgd dat het niet mogelijk was om voor elke ruimte hetzelfde machine learning model te ontwikkelen.

| Ruimte        | Fijnstofdeeltjes | Luchtdruk | CO2 | Verlichting | Activiteit | Temperatuur | Luchtvochtigheid | Deurstatus\* | Deurgebruik\* |
| ------------- | ---------------- | --------- | --- | ----------- | ---------- | ----------- | ---------------- | ------------ | ------------- |
| Apenrots West |                  |           |     |             |            | X           | X                |              |               |
| Apenrots Oost |                  |           |     |             |            | X           | X                |              |               |
| The Living    |                  |           |     |             |            |             |                  | X            | X             |
| Classroom     |                  |           |     |             |            | X           | X                |              |               |
| Toilets       |                  |           |     |             |            |             |                  | X            | X             |
| Boardroom     | X                | X         | X   | X           | X          | X           | X                |              |               |

<center><small>Tabel 1: Dataverzameling per ruimte in de Big Top</small></center>
<small>*Deurstatus en deurgebruik zijn momenteel geen onderdeel van het machine learning model.</small>

Een oplossing zou zijn om voor iedere ruimte sensoren te installeren die de waarden meten die in table 1 worden gespecificeerd. Op deze manier kan er voor iedere ruimte een model ontwikkeld worden en zal de applicatie beter gebruikt kunnen worden om de luchtkwaliteit te verbeteren. 

### Verzameling

De data die beschikbaar was tijdens het project verzameld tussen `2021-01-07 09:11` en `2021-02-09 12:54`. Dit betekend dat er maar ongeveer een maand aan data gebruikt kon worden om de machine learning modellen te trainen. Tijdens het onderzoek van Kallio et al.[^1] werd een dataset van een jaar gebruikt. Dit is belangrijk om bepaalde seizoensgebonden trends op te kunnen nemen in het model.

De voorgestelde oplossing is om een jaar aan data te verzamelen en daarna de modellen te trainen op de complete dataset. Op deze manier kan gevalideerd worden of de bevindingen van dit project juist waren.

## Workflow

### Teststrategie

Gedurende het ontwikkelen van de machine learning API is er gewerkt op een [test driven](beheer.md#) manier. Het voordeel hiervan is dat veranderingen die delen de software breken tijdig opgespoord konden worden. In het front-end en back-end van de Twindle applicatie is deze strategie niet toegepast. Hierdoor kon het lastig zijn om te bepalen waar bugs vandaan kwamen. 

Het voorstel is om in de toekomst een striktere teststrategie te hanteren. Op deze manier zal uitbreiding van besstaande applicaties vloeiender verlopen.

### Continuous integration & deployment

De bedoeling was om tijdens het project gebruik te maken van [continous integration (CI) en deployment (CD)](beheer.md#deployment). Hiervoor was een sterke teststrategie en versiebeheersysteem toegepast. Daarnaast moet er ook een omgeving zijn om de applicaties te hosten. Deze was er wel maar was niet beschikbaar voor de automatische pipelines.

Om in de toekomst betere demoes te kunnen geven en hogere kwaliteit software af te leveren is het advies om een development en release omgeving beschikbaar te stellen voor de stagiaires. 

## Ethiek
Om te bepalen met welke ethische aspecten rekening gehouden moet worden en op welke manier is de TICT-tool[^2] toegepast. Dit is een tool die helpt bij het inschatten van de impact die een nieuwe technology gaat maken. Voor dit project is gebruik gemaakt van de "quick scan" optie om een globaal overzicht van de situatie te krijgen[^3].

Belangrijke bevingingen van deze quickscan zijn dat er al veel rekening gehouden wordt met privacy en dat er een positieve impact gemaakt wordt op de personen die de applicatie gebruiken. 

Er zijn plannen om de applicatie uit te breiden zodat deze kan de brandveiligheid kan monitoren. Wanneer deze uitbreidingen worden gemaakt is het belangrijk dat er aan dezelfde  hoge privacy eisen wordt gehouden.

[^1]: [Forecasting office indoor CO2 concentration using machine learning with a one-year dataset](https://doi.org/10.1016/j.buildenv.2020.107409)
[^2]: [Technology Impact Cycle Tool](https://www.tict.io/)
[^3]: [TICT Quickscan](pdfs/tict_quickscan.pdf)