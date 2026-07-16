# Iluze timeframu: Kompromis mezi informací a statistickou četností

Běžný retailový přístup k vývoji obchodních strategií velí přesun na vyšší timeframy (např. 4H nebo 1D) kvůli "čistšímu trendu" a eliminaci tržního šumu. Z pohledu kvantitativní analýzy jde o fundamentální chybu, která strategii připravuje o statistickou robustnost.

Tento výzkum dekonstruuje timeframe jako pouhou kompresi syrových dat a definuje, jak najít rovnováhu mezi ziskem detailních informací a výpočetní náročností.

![Porovnání timeframů](https://cichra-quant.cz/assets/timeframe_comparison_ohlc2.webp)

### Klíčové problémy časové agregace:

* **Ztráta mikrostruktury a komprese dat:** Žádný timeframe reálně neexistuje. Trh tiskne pouze ticky a plní limitní knihu. Hodinová svíčka je brutální kompresí milionů transakcí do čtyř absolutních hodnot (OHLC). Čím vyšší agregace, tím větší nenávratná ztráta informací o skutečném chování likvidity.
* **Kolaps statistické významnosti:** Testování na 4H datech vystaví strategii zlomku reálných tržních situací. Naproti tomu backtest na 10sekundových datech generuje miliony datových bodů. Zákon velkých čísel je pro potvrzení reálného edge kritický – malý vzorek svíček z vysokých timeframů vede k náhodným výkyvům a overfittingu.
* **Zákon kompromisu (Informace vs. Šum):** Práce na sekundových datech exponenciálně zvyšuje podíl stochastického šumu, který rozdrtí jednoduché indikátory. Řešením není nalezení "univerzálního" timeframu, ale přizpůsobení komprese logice alfa faktoru. Algoritmy těžící z order flow vyžadují hluboký detail (10-15s), zatímco swingové modely tuto granularitu nepotřebují.

### Kompletní výzkum

Detailní rozbor této problematiky a matematické argumenty pro volbu správné datové granularity naleznete v celém článku.

🔗 **[Přečíst kompletní výzkum o timeframech](https://cichra-quant.cz/posts/timeframy-informace-vs-sum/)**
