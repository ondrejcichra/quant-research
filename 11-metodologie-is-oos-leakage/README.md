# Metodologie In-Sample a Out-of-Sample: Prevence Data Leakage

Chybná aplikace IS/OOS (In-Sample / Out-of-Sample) metodologie je jednou z nejčastějších příčin selhání algoritmických strategií v realitě. Mnoho výzkumníků používá OOS jako "filtr" pro výběr strategií, čímž ho degradují na druhou trénovací sadu a připravují se o jakoukoliv objektivní validaci.

Tento výzkum definuje přísný inženýrský přístup, jak oddělit fázi vývoje od fáze finálního soudce a jak zabránit úniku informací (Data Leakage) v databázové vrstvě.

![Segmentace dat a validace](https://cichra-quant.cz/assets/deleni-is-oos.webp)

### Inženýrské principy validace:

* **Separace rolí:** In-Sample (IS) fáze slouží výhradně pro trénink a ladění modelu. Out-of-Sample (OOS) fáze je binární arbitr – strategie ji buď projde, nebo je bez dalšího ladění vyřazena. Jakákoliv úprava parametrů po pohledu na OOS výsledky vede k fatálnímu selhání (cherry-picking).
* **Fyzická izolace (Data Leakage Prevention):** Únik dat z OOS do IS (např. nahlédnutím do grafu budoucích dat) je častější, než se zdá. Řešením je tvrdá fyzická separace v databázi (např. pomocí `WHERE sample_type != 'OOS'`), která znemožňuje výpočetnímu enginu k těmto datům vůbec přistoupit během tréninkové fáze.
* **Segmentace pro diagnostiku:** Namísto jednoduchého rozdělení 80/20 využívám pokročilejší techniky, jako je sendvičová architektura nebo roztříštěné fragmenty dat po celé časové řadě. To umožňuje detekovat, zda strategie selhává kvůli overfittingu, nebo zda došlo ke skutečnému strukturálnímu rozpadu tržní neefektivity.

### Kompletní metodologie

Detailní rozbor toho, jak správně krájet dataset, proč je selekce na OOS datech klamná a jak fyzicky izolovat tréninkové prostředí v rámci DuckDB, naleznete v celém článku.

🔗 **[Přečíst kompletní výzkum o IS/OOS metodologii](https://cichra-quant.cz/posts/in-sample-out-of-sample-metodologie-a-data-leakage/)**
