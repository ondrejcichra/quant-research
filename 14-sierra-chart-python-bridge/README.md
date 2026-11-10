# Nízkolatenční můstek Sierra Chart → Python: Architektura a kód

Každý, kdo se vážně zabývá kvantitativním výzkumem na regulovaných futures trzích (CME), dříve či později narazí na kritický problém: jak dostat živá ticková data s milisekundovou přesností z burzy přímo do Pythonu, a to bez placení tisíců dolarů za institucionální API bez prostředníka.

Většina běžně dostupných retailových řešení spoléhá na zápis dat do CSV souborů nebo na blokující TCP spojení. Tato řešení však při otevření americké hlavní seance, kdy trhem protékají tisíce ticků za sekundu, okamžitě selhávají. Důsledkem je zahlcení I/O operací, desynchronizace order booku a fatální zamrznutí platformy.

Tento materiál představuje kompletní open-source architekturu plně odděleného (decoupled) můstku, který tento problém obchází pomocí neblokujícího UDP protokolu a paměťové optimalizace.

![Architektura datového můstku](https://cichra-quant.cz/assets/SC-to-ZMQ-architektura.webp)

### Klíčové principy architektury:

- **Minimalistická C++ vrstva (Zero Overhead):** Datovým zdrojem je ultralehká C++ studie (přes ACSIL) běžící přímo v paměti Sierra Chart. Namísto nákladného parsování textu (JSON, CSV) balí tržní data do pevné 58bajtové struktury (bez memory paddingu) a pomocí režimu `FIONBIO` je okamžitě vystřeluje na localhost. Obchodní platforma díky tomu na nic nečeká.

- **Asymetrie času a hybridní clocking:** Kód striktně rozlišuje mezi Trades (realizované obchody) a Quotes (změny v hloubce order booku). Zatímco obchody přebírají exaktní čas z burzovního matching enginu CME, kotacím je dynamicky přiřazován lokální NTP čas, aby nedocházelo k zamrznutí časové osy při pasivním doplňování likvidity.

- **Python Asynchronous Core:** Na straně přijímače běží vícevláknový engine s optimalizovaným zpracováním. Pro příjem dat dedikuje izolované vlákno se 256MB síťovým bufferem, manuálně vypíná Garbage Collector během datových špiček a ticky okamžitě překlápí přes rychlý ZeroMQ (PUB/ROUTER) broker k dalším systémům.


### Kompletní technický rozbor a zdrojové kódy

Kompletní dokumentaci, detailní vizualizaci paměťových bloků, kód pro zkompilování C++ studie v Sierra Chart i plný kód Python serveru s ukládáním do DuckDB naleznete v celém článku na mém webu.

🔗 **[Kompletní článek a zdrojové kódy můstku](https://cichra-quant.cz/posts/sierra-chart-python-bridge-tickova-data/)**
