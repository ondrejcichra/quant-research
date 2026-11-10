# Kvantitativní výzkum a vývoj algoritmických obchodních systémů

Tento repozitář slouží jako technický archiv metodologických postupů a výzkumů z vývoje mých vlastních algoritmických systémů. Zastávám hybridní přístup: tržní hypotézy tvořím na základě logiky, ale o existenci reálného statistického edge nechávám s konečnou platností rozhodnout data a výpočetní sílu.

Cílem mé práce není najít ziskovou křivku z historie. Zaměřuji se na budování inženýrské infrastruktury (Python, DuckDB, C++, Optuna), odhalování iluzí backtestů, asymetrickou penalizaci strategií a identifikaci robustních parametrických klastrů, které dokážou přežít strukturální rozpad trhu.

Kompletní výzkumy, zdrojové kódy a datové exporty jsou dostupné zde: **[cichra-quant.cz](https://cichra-quant.cz/)**  

**[Přehled všech výzkumů a článků zde](https://cichra-quant.cz/posts)**  

## Knihovna výzkumů

- 📁 **[14. Nízkolatenční můstek Sierra Chart → Python: Architektura a kód](14-sierra-chart-python-bridge/)**
  * *Nativní C++ konektor, obcházení I/O bottlenecků a asynchronní ZeroMQ/DuckDB engine pro non-blocking přenos živých dat.*

- 📁 **[13. Dvoufázové měření statistického edge: Předcházení overfittingu](13-dvoufazove-mereni-edge/)**
  * *Triangulace logiky před WFO, eliminace long-biasu a návrh funkcí pro stabilitu clusteru.*

- 📁 **[12. Hledání klastrů pravděpodobností vs. mýtus jedné ziskové strategie](12-klastry-pravdepodobnosti/)**
  * *Proč je masivní backtesting pouhou rutinou a jak v zašuměném prostředí identifikovat stabilní strukturální edge.*

- 📁 **[11. In-Sample a Out-of-Sample metodologie: Prevence Data Leakage](11-metodologie-is-oos-leakage/)**
  * *Jak segmentovat dataset, proč je OOS finálním soudcem a jak zabránit úniku dat.*

- 📁 **[10. Limity technické analýzy: Vizuální artefakty vs. order flow](10-iluze-technicke-analyzy/)**
  * *Proč jsou svíčkové formace produktem časové agregace, nikoliv kauzality v trhu.*

- 📁 **[09. Strukturální rozpad edge: Nestacionarita trhu](09-parameter-drift-rozpad-edge/)**
  * *Analýza Parameter Driftu, vizualizace posunu ziskových zón přes KDE a proč statické parametry selhávají.*

- 📁 **[08. Realistický backtest: Asymetrická penalizace a order book](08-realisticky-backtest-slippage/)**
  * *Simulace tržní mikrostruktury, ochrana před nereálným plněním a detailní Tape test.*

- 📁 **[07. Iluze backtestu: Statistická nevyhnutelnost náhody](07-overfitting-a-iluze-backtestu/)**
  * *Analýza In-Sample vs. OOS degradace a paradox přeoptimalizace u brute-force systémů.*

- 📁 **[06. Architektura objective function: Prevence overfittingu](06-optimalizace-na-robustnost/)**
  * *Jak svázat ruce optimalizátoru pomocí kompozitního skóre a linearity ekvity.*

- 📁 **[05. Měření edge: Kvantitativní metriky a zátěžové testy](05-mereni-edge-strategie/)**
  * *Robustní metriky (SQN, Sortino) a inženýrské testy (Jackknife) pro validaci systému.*

- 📁 **[04. Srovnání výkonnosti AOS s trhem: Alpha, Beta a Risk Parity](04-alpha-vs-beta-srovnani-s-trhem/)**
  * *Proč je procentuální PnL zavádějící a jak správně měřit výkonnost nezávisle na páce.*

- 📁 **[03. Metodologie: Idea-first vs. Brute-force datamining](03-idea-first-vs-brute-force/)**
  * *Syntéza logiky a výpočetní síly pro eliminaci kognitivních zkreslení při výzkumu dat.*

- 📁 **[02. Iluze timeframu: Kompromis mezi informací a statistickou četností](02-timeframy-informace-vs-sum/)**
  * *Proč je hledání trendu na vysokých timeframech past a jak agregace dat likviduje statistický edge.*

- 📁 **[01. Architektura zpracování Level 2 dat a tržní mikrostruktury](01-zpracovani-level2-dat/)**
  * *Řešení časových offsetů, eliminace děr přes ASOF join a izolace Cash Volume Profilu v DuckDB.*
