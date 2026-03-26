# Marketplace-Safety-ML
Klassificeringsprojekt för marknadsplats-säkerhet; fokus på hög precision och operativ tillförlitlighet.

Modeller är jämförda via Cross Validation, sen är optimering mot precision gjord med vald modell, och top-5% misstänkta ärenden tas fram för arbetslaget. Träning görs på 9,600 rader och pipeline är sparad till joblib. Målet är pricksäkra flaggningar och hållbar daglig arbetsmängd.

Modellen behövs ej tränas om utan kan implementeras på ny data dagligen. Test körs med resultaten hur många modellen prickade rätt, hur många falsklarm och missar som gjordes.

## Strategi

Pipeline behövs vara robust, och vid träning av modellen får inte testdata läcka in i träningen. Ny data ska kunnas tas in även om ordningen på kolumner är annorlunda, om det saknas värden, och för kategorisk data används *Columntransformer* och *OneHotEncoder*.

Vi jämför olika modeller i stratifierad Kfold split på träningsdata, och riktar in oss på bästa precision-resultat. Den modellen optimerar vi hyperparametrarna på för ytterligare bra precision. Vi utvärderar optimerad modell på testdata, och jämför det resultatet med påbyggande beslut att ta fram top-5% av dagliga ärenden. Då får vi se om falsklarm och rätta larm balanseras. Det kan behövas justeras till top-10% ifall det finns tid över för arbetslaget dag-till-dag.

## Hur projektet körs

git clone https://github.com/MaWe96/Marketplace-Safety-ML

Installera biblioteken:

python -m pip install numpy pandas matplotlib seaborn scikit-learn ipykernel

Öppna notebooken

Run All
