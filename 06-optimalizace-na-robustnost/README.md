# Architektura Objective Function a prevence overfittingu v AI

Pokročilé optimalizační algoritmy (např. Bayesovský TPE sampler v enginu Optuna) fungují na principu cesty nejmenšího odporu. Pokud jako cílovou metriku pro maximalizaci zvolíme hrubý zisk (Net PnL), optimalizátor nevyhnutelně vygeneruje matematický overfit těžbou historických anomálií a izolovaných extrémů. 

Tento koncept představuje návrh vlastní kompozitní objective function, která strojovému učení matematicky svazuje ruce a nutí jej hledat plošnou robustnost.

![Analýza degradace strategie](https://cichra-quant.cz/assets/04_degradation_analysis-2D.webp)

### Mechanismy pro vynucení robustnosti:

* **Kompozitní Skóre (Composite Score):** Nahrazení izolovaných metrik jedinou komplexní rovnicí, která v každé iteraci současně vyhodnocuje stabilitu, statistickou četnost a ziskovost. Cesta nejmenšího odporu tak vede k nalezení reálné tržní logiky, nikoliv chyby v parametrech.
* **Měření linearity ($R^2$) a penalizace nestability:** Aplikace koeficientu determinace ($R^2$) na ekvitní křivku doplněná o dynamický exponent (Strictness). Nekompromisně penalizuje zubaté a nekonzistentní průběhy zisku, čímž tlačí engine k vyhlazené ekvitě.
* **Zastropování extrémů (Anti-Overfitting):** Využití funkce `min()` pro tvrdé odříznutí nesmyslných anomálií. Omezení maximální započítané hodnoty Profit Factoru (např. na 3.0) a Recovery Factoru (na 4.0) brání enginu vyhrát přes ojedinělé "black swan" obchody a nutí ho replikovat stabilní výsledky.
* **Řízení statistické četnosti (Robustness):** Křivkové penalizace (např. `sqrt` nebo `log10`) eliminující strategie, které udělají buď statisticky bezvýznamné minimum obchodů (štěstí), nebo naopak tisíce obchodů (stochastický šum).

### Kompletní vzorec a výzkum

Plné znění rovnice, analýzu jednotlivých parametrů a filozofii za konstrukcí objective function naleznete v celém článku.

🔗 **[Přečíst kompletní výzkum o návrhu optimalizační rovnice](https://cichra-quant.cz/posts/optimalizace-na-robustnost-vs-overfitting/)**
