# Iluze backtestu: Statistická nevyhnutelnost náhody a overfitting

Krásně rostoucí historická křivka neznamená, že má strategie reálný tržní edge. Ve světě algoritmického obchodování je vygenerování ziskového backtestu na historických datech triviální záležitost. Drtivá většina takových křivek však nereprezentuje prediktivní sílu do budoucna, ale pouze statistickou nevyhnutelnost náhody.

Tento výzkum zkoumá fenomén přeoptimalizace (curve-fitting), masivní degradaci systémů v Out-of-Sample fázi a porovnává čistý brute-force datamining s logickými jádry strategií.

![In-Sample vs Out-of-Sample přežití](https://cichra-quant.cz/assets/selection_bias_2_donut2.webp)

### Klíčové poznatky z testování milionů iterací:

* **Statistická nevyhnutelnost náhody (Selection Bias):** Při otestování 100 000 strategií bude čistě na základě pravděpodobnosti ("efekt házení mincí") přibližně 15 až 20 % z nich ziskových. Pokud výzkumník zkusí desítky parametrů a vybere ten nejlepší, neobjevil edge, ale pouze vybral ten, který měl historické štěstí.
* **Paradox přeoptimalizace:** Na datech z testovacího enginu se jasně ukazuje negativní korelace u překombinovaných systémů: čím vyššího zisku strategie dosáhla v In-Sample datech (díky obrovskému množství filtrů), tím hůře dopadla v neviděných OOS datech. 
* **Logická jádra vs. Brute-force:** Srovnávací test ukázal drtivý rozdíl v přežití (Drop-off rate). Náhodně spojené podprůměrné triggery s mnoha filtry měly šanci na přežití v OOS pouhých 4,95 %. Naproti tomu očištěná jádra strategií, založená na reálné tržní mikrostruktuře (bez vyhlazování dat), prokázala téměř desetinásobnou míru přežití.

![Ukázka přeoptimalizace](https://cichra-quant.cz/assets/overfit-example-2.webp)

### Kompletní datová analýza

Hlubší rozbor trychtýřového grafu přežití, ukázky negativní korelace u overfitu a principy, jak rozpoznat skutečný edge od statistického šumu, najdete v celém článku.

🔗 **[Přečíst kompletní výzkum o iluzi backtestu a overfittingu](https://cichra-quant.cz/posts/overfitting-a-iluze-backtestu/)**
