# Marketplace-Safety-ML
Klassificeringsprojekt för marknadsplats-säkerhet; fokus på hög precision och operativ tillförlitlighet

# *Operations*-team på Marketplace Safety

Maskininlärnings-projekt som klassificerar misstänksam aktivitet utifrån features. Modeller är jämförda via Cross Validation, sen är optimering mot precision gjord med vald modell, och top-5% misstänkta ärenden tas fram för arbetslaget. Träning görs på 12,000 rader och pipeline är sparad till joblib. Ny data ska testas, målet är pricksäkra flaggningar och hållbar daglig arbetsmängd.

## Kravkortet: Ali, Operations manager “Vi drunknar i flaggningar”

Det är för stor backlog och otydliga flaggningar, så för att återställa tillit i teamets arbetsuppgifter behövs färre falsklarm och begränsning på inkommande ärenden (medan det förblir viktigt att identifiera misstänkt aktivitet).

Modellen ska inte behövas tränas om utan ska kunna implementeras på ny data dagligen (med hantering av saknade värden, numerisk såväl som kategorisk data). Splitta train/test och så tar vi fram ett resultat på test-data; hur många modellen prickade rätt, hur många falsklarm och missar som gjordes.

## Strategi

Pipeline behövs vara robust, och vid träning av modellen får inte testdata läcka in i träningen. Ny data ska kunnas tas in även om ordningen på kolumner är annorlunda, om det saknas värden, och för kategorisk data används *Columntransformer* och *OneHotEncoder*.

Vi jämför olika modeller i stratifierad Kfold split på träningsdata, och riktar in oss på bästa precision-resultat. Den modellen optimerar vi hyperparametrarna på för ytterligare bra precision. Vi utvärderar optimerad modell på testdata, och jämför det resultatet med påbyggande beslut att ta fram top-5% av dagliga ärenden. Då får vi se om falsklarm och rätta larm balanseras. Det kan behövas justeras till top-10% ifall det finns tid över för arbetslaget dag-till-dag.

## Ansvarsfördelning
| Ansvarsområde | Ansvarig |
| -------------------- | ------------ |
| Dataförståelse | Hamed |
| Pipeline & preprocess | Hamed |
| Modelljämförelse | Jazdan |
| Optimering | Martin |
| Prioritering | Martin |
| Pitch & Risker | Jazdan |

## Hur projektet körs

git clone https://github.com/MaWe96/Marketplace-Safety-ML

Installera biblioteken:

python -m pip install numpy pandas matplotlib seaborn scikit-learn ipykernel

Öppna notebooken

Run All