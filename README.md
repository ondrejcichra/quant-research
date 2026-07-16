# Kvantitativní výzkum a analýza tržní mikrostruktury

Tento repozitář slouží jako technický archiv abstraktů a metodologických postupů z vývoje automatických obchodních systémů (AOS). Zaměřuji se na zpracování Level 2 dat, vývoj robustní infrastruktury (Python, DuckDB) a odstraňování kognitivních zkreslení z výzkumu historických dat.

Kompletní výzkumy, zdrojové kódy a datové exporty jsou dostupné na mém webu: **[cichra-quant.cz](https://cichra-quant.cz/)**

## Obsah výzkumné knihovny

* 📁 **[01. Architektura zpracování Level 2 dat a tržní mikrostruktury](01-zpracovani-level2-dat/)**
  * *Řešení časových offsetů, eliminace děr přes ASOF join a izolace Cash Volume Profilu v DuckDB.*

* 📁 **[02. Iluze timeframu: Kompromis mezi informací a statistickou četností](02-timeframy-informace-vs-sum/)**
  * *Proč je hledání trendu na vysokých timeframech past a jak agregace dat likviduje statistický edge.*
