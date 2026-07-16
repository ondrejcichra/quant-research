# Architektura zpracování Level 2 dat a tržní mikrostruktury

Běžně dostupné agregované svíčky nedostačují pro robustní kvantitativní výzkum. Vývoj "heavy quant" systémů vyžaduje práci se surovými tickovými daty a order flow, což přináší specifické inženýrské výzvy při čištění a transformaci.

Tento koncept představuje metodologii konverze zašuměných tickových dat do kontinuální databáze (DuckDB / Parquet) připravené pro přesné vektorové testování a simulaci order booku.

![Ukázka datové struktury](https://cichra-quant.cz/assets/tape_es.webp)

### Řešení fundamentálních problémů při zpracování tržních dat:

* **Rozprostření času a zachování sekvence (Nanosecond Offsets):** Surová data (např. exporty z ATAS) často obsahují desítky ticků se stejnou časovou značkou (sekundovou). Aby databáze neztratila chronologii událostí při vektorových operacích, aplikuje engine rovnoměrné nanosekundové offsety (např. 0 ns, 333 ms, 666 ms). Order book tak zůstává dokonale sekvenční.
* **Eliminace děr v datech přes ASOF Join:** Naivní časové agregace generují mezery v okamžicích nulové likvidity, což destruuje ML modely a indikátory. Řešením je "Sparse-to-Dense" logika – vygenerování spojité časové mřížky a navázání dat pomocí As-Of (ASOF) joinu. Prázdné sloty automaticky přebírají `last_known_price`, čímž vzniká matematicky kontinuální řada bez falešných gapů.
* **Izolace Cash Volume Profilu:** Globex (asijská/evropská seance) deformuje rozložení objemu. Architektura provádí tvrdý reset profilu a Value Area (68,2 %) přesně v 15:30 SEČ. Zajišťuje se tak čistá izolace metrik (VAH, VAL, VPOC) výhradně pro likvidní americkou seanci.

![Struktura DuckDB exportu](https://cichra-quant.cz/assets/marketdata-overview.webp)

### Kompletní výzkum a vzorek dat

Detailní rozbor této datové pipeline a bezplatný DuckDB export čistých Level 2 dat (ES, NQ, RTY) pro vaše testování naleznete v kompletním článku.

🔗 **[Přečíst celý výzkum a stáhnout databázi](https://cichra-quant.cz/posts/zpracovani-level2-trznich-dat/)**
