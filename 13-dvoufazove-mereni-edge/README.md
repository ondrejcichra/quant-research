# Dvoufázové měření statistického edge: Předcházení overfittingu

Kvantitativní přístup nespočívá v tom, že naslepo spustíte optimalizační engine na miliony iterací. Pokud enginu předložíte nekvalitní surová data nebo logicky chybnou strategii, algoritmus pouze přeoptimalizuje (overfit) vstupy tak, aby v historii generovaly zisk (fenomén Garbage In, Overfitted Garbage Out).

Tento výzkum ukazuje, proč je nutné syrový signál nejprve exaktně izolovat a statisticky změřit ještě předtím, než se vůbec zapojí do komplexní Walk-Forward optimalizace (WFO).

![Měření edge](https://cichra-quant.cz/assets/EVC-Cum_Net_PMFE10_PMAE10-comb_signed.webp)

### Klíčové principy výzkumu:

* **Triangulace tržní mechaniky:** Edge není o nalezení dokonalého matematického vzorce, ale o zachycení reálné tržní mechaniky (např. absorpce likvidity). Výzkum ukazuje, jak jeden logický scénář testovat napříč odlišnými filtry (divergence vs. kumulativní posun) pro potvrzení existence signálu.
* **Asymetrický klam (Long-Bias):** Ukázka zrádnosti akciových indexů (ES, NQ), které mají přirozenou tendenci růst. Strategie, která vykazuje zisk na dlouhé straně (LONG), může být pouhým svezením se s trhem, což se odhalí drastickým selháním totožné logiky na straně krátké (SHORT).
* **Flat Maxima a penalizace šumu:** Ukázka konkrétního zdrojového kódu z WFO selektoru, který matematicky penalizuje izolované vrcholy pomocí vzorce `mean_val - std_val`. Engine je tak nucen vybírat stabilní parametrické clustery, které odolají budoucímu strukturálnímu posunu trhu.

### Kompletní datová analýza

Detailní rozbor problému, odhalení rozdílu mezi surovým MFE/MAE a vlastním konceptem PMFE/PMAE a zdrojové kódy parametrů najdete v celém článku.

🔗 **[Přečíst kompletní výzkum o měření edge a Flat Maxima](https://cichra-quant.cz/posts/dvoufazove-mereni-statistickeho-edge/)**
