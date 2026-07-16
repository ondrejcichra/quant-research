# Kvantitativní výzkum a analýza tržní mikrostruktury

Tento repozitář slouží jako technický archiv abstraktů a metodologických postupů z vývoje automatických obchodních systémů (AOS). Zaměřuji se na zpracování Level 2 dat, vývoj robustní infrastruktury (Python, DuckDB) a odstraňování kognitivních zkreslení z výzkumu historických dat.

Kompletní výzkumy, zdrojové kódy a datové exporty jsou dostupné na mém webu: **[cichra-quant.cz](https://cichra-quant.cz/)**

## Knihovna výzkumů

* 📁 **[01. Architektura zpracování Level 2 dat a tržní mikrostruktury](01-zpracovani-level2-dat/)**
  * *Řešení časových offsetů, eliminace děr přes ASOF join a izolace Cash Volume Profilu v DuckDB.*

* 📁 **[02. Iluze timeframu: Kompromis mezi informací a statistickou četností](02-timeframy-informace-vs-sum/)**
  * *Proč je hledání trendu na vysokých timeframech past a jak agregace dat likviduje statistický edge.*

* 📁 **[03. Metodologie: Idea-first vs. Brute-force datamining](03-idea-first-vs-brute-force/)**
  * *Syntéza logiky a výpočetní síly pro eliminaci kognitivních zkreslení při výzkumu dat.*

* 📁 **[04. Srovnání výkonnosti AOS s trhem: Alpha, Beta a Risk Parity](04-alpha-vs-beta-srovnani-s-trhem/)**
  * *Proč je procentuální PnL zavádějící a jak správně měřit výkonnost nezávisle na páce.*

* 📁 **[05. Měření edge: Kvantitativní metriky a zátěžové testy](05-mereni-edge-strategie/)**
  * *Robustní metriky (SQN, Sortino) a inženýrské testy (Jackknife) pro validaci systému.*

* 📁 **[06. Architektura objective function: Prevence overfittingu](06-optimalizace-na-robustnost/)**
  * *Jak svázat ruce optimalizátoru pomocí kompozitního skóre a linearity ekvity.*

* 📁 **[07. Iluze backtestu: Statistická nevyhnutelnost náhody](07-overfitting-a-iluze-backtestu/)**
  * *Analýza In-Sample vs. OOS degradace a paradox přeoptimalizace u brute-force systémů.*

* 📁 **[08. Realistický backtest: Asymetrická penalizace a order book](08-realisticky-backtest-slippage/)**
  * *Simulace tržní mikrostruktury, ochrana před nereálným plněním a detailní Tape test.*

* 📁 **[09. Strukturální rozpad edge: Nestacionarita trhu](09-parameter-drift-rozpad-edge/)**
  * *Analýza Parameter Driftu, vizualizace posunu ziskových zón přes KDE a proč statické parametry selhávají.*

* 📁 **[10. Limity technické analýzy: Vizuální artefakty vs. order flow](10-iluze-technicke-analyzy/)**
  * *Proč jsou svíčkové formace produktem časové agregace, nikoliv kauzality v trhu.*

* 📁 **[11. In-Sample a Out-of-Sample metodologie: Prevence Data Leakage](11-metodologie-is-oos-leakage/)**
  * *Jak segmentovat dataset, proč je OOS finálním soudcem a jak zabránit úniku dat.*
