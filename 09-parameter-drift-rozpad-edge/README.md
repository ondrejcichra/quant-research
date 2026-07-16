# Strukturální rozpad edge a nestacionarita tržní mikrostruktury

Trh není statický systém. Likvidita, volatilita i chování účastníků se v čase neustále proměňují. Hledání jednoho "perfektního" parametru strategie je matematická chyba, protože tento parametr v budoucnu s vysokou pravděpodobností selže v důsledku nestacionarity.

Tento výzkum analyzuje jev zvaný *Parameter Drift* (vektor posunu těžiště ziskovosti) a vysvětluje, proč se nejlepší In-Sample nastavení zaručeně posune mimo oblast ziskovosti v Out-of-Sample datech.

![Vizualizace posunu těžiště ziskovosti](https://cichra-quant.cz/assets/03_1d_drift_levy_kurtosis.webp)

### Klíčové inženýrské poznatky:

* **Teorie posouvajících se zón:** Skutečný tržní edge není bod, ale celá oblast (ostrov) v parametrickém prostoru. Problém je, že tento ostrov se vlivem vývoje trhu v čase posouvá. Strategie, které cílí na úzké "ideální" parametry z historie, jsou při prvním posunu trhu okamžitě vyřazeny z provozu.
* **Fáze destrukce algoritmů:** Analýza degradace ukazuje, že strategie s příliš velkým množstvím logických filtrů (překombinované systémy) vytvářejí velmi malé a křehké zóny ziskovosti. Jakýkoliv drift parametrů je okamžitě spláchne. Robustní systémy naopak těží ze širokých "flat maximums", které driftu odolávají.
* **Kvantifikace přes Kernel Density Estimation (KDE):** Pomocí 1D KDE vizualizuji rozdělení hustoty ziskovosti v parametrickém prostoru. Data exaktně potvrzují, že těžiště nejlepších výsledků se mezi In-Sample a Out-of-Sample epochami plynule posouvá. Zároveň dochází k postupné degradaci celkového ziskového potenciálu těchto parametrů.

![Deformace ziskové zóny](https://cichra-quant.cz/assets/03_1d_drift_levy_window.webp)

### Závěr výzkumu

Edge není statická konstanta, ale pohyblivý cíl. Optimalizace na historický vrchol PnL je matematickou pastí, protože vybíráte parametry, které již v minulosti dosáhly svého limitu. Profesionální přístup vyžaduje hledání širších zón stability, které jsou vůči strukturálnímu driftu imunní.

🔗 **[Přečíst kompletní výzkum o parameter driftu a degradaci edge](https://cichra-quant.cz/posts/parameter-drift-a-strukturalni-rozpad-edge/)**
