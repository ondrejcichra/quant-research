# Architektura backtest enginu: Asymetrická penalizace a simulace order booku

Běžný backtest na historických datech probíhá ve sterilním, dokonale synchronním databázovém prostředí. Začátečníci často vyvíjejí logiku, která na historických OHLC datech exceluje, ale po nasazení do reality selže na reálném plnění, spreadu a latenci.

Tento koncept představuje architekturu vlastního dvoufázového testovacího enginu, který je záměrně navržen tak, aby strategie asymetricky penalizoval a simuloval nejhorší možné tržní podmínky.

![Porovnání OHLC enginu a Tape testu](https://cichra-quant.cz/assets/tick-vs-numpa-inverzni-divergence2.webp)

### Dvoufázová výzkumná architektura:

* **Ultra-rychlé vektorové jádro (Numba JIT):** Pro optimalizaci a průchod milionů iterací napříč roky dat je nutná extrémní rychlost (vektorizace/JIT kompilace). V tomto OHLC prostředí však nelze sekvenčně simulovat hloubku trhu. Engine proto aplikuje striktní *asymetrickou penalizaci*: Stop-loss vyžaduje pouhý dotek ceny (a přidává umělý slippage), zatímco Take-profit vyžaduje úplné proražení cenové hladiny (price penetration) a maže "gap bonus".
* **Sekvenční Tape Test (Ultimátní Arbitr):** Nalezená alfa z rychlého jádra je následně podrobena zátěžovému testu na vybraném okně. Nezávislý sekvenční engine zpracovává detailní order book tick po ticku v milisekundovém rozlišení. 
* **Simulace burzovního matcheru:** Limitní příkazy nejsou plněny při prvním doteku ceny, engine exaktně vyžaduje kompletní vyčištění dané úrovně v limitní knize. U market příkazů systém přičítá síťovou latenci a plní pozici za fyzicky dostupnou likviditu na opačné straně order booku včetně reálného spreadu.

Výsledkem této architektury je bezpečný pesimistický polštář – strategie z vektorového výzkumu jsou v reálu exekuovány s mírně lepšími výsledky, než predikoval tvrdý backtest.

### Kompletní inženýrský rozbor

Detailní analýzu problému rychlost vs. přesnost a ukázky logiky (Python kód) z exekučního a výzkumného enginu naleznete v celém článku.

🔗 **[Přečíst kompletní výzkum o simulaci order booku a plnění](https://cichra-quant.cz/posts/realisticky-backtest-slippage-order-book/)**
