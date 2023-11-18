# Symbolické výrazy
- **Listener**\
Okno skrz které můžeme pracovat s programem LispWorks (můžeme do něj zadávat výpočty)
  - Čísla s desetinnou čárkou nemusí být přesná, ale čísla bez des. čárky a zlomky přesné jsou
- **Symbolický výraz**\
Je text, kterému Listener rozumí a bere ho jako zadání výpočtu
  - *Jednoduchý výraz* (atom)
  - *Složený výraz* (seznam)
- **Atom**
  - *Číslo* - (1; 0; -2; 1/3; 0.49; #(0.0 1.0))
  - *Symbol* - posloupnost písmen, případně čísel (ale nesmí to být jen čísla), jiných znaků (*5* není symbol, protože to je číslo, *x5* symbol je)
- **Složený výraz** (sezman)\
Posloupnost jednoho nebo více výrazů, říkáme jim **prvky složeného výrazu (seznamu)**.\
Prvky jsou odděleny mezerami a začíná/končí závorkou. Např.: **(+ 1 2)** nebo **(+)**
- **Vytváření složených výrazů:**\
![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/f3dcc90a-d844-45df-8e42-af499ab302a1)\
![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/e398ed82-f915-4c36-9e3c-6c89f939bbea)

- **Operátor**\
Je vždy před ostatními výrazy složeného výrazu (*prefixová notace*) a říká co se má udělat.\
![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/37c4444b-96ed-46c6-a5e7-d4bf8b183151)

- **Vyhodnocování symbolických výrazů**
  - *Hodnota symbolického výrazu* - Např. 2 je hodnotou sym. vyr. (+ 1 1), prostě výsledek, který nám dá listener
  - Počítač k hodnotě výrazu dojde přesně popsaným procesem, kterému se říká *vyhodnocovací proces*.
  - Vyhodnocovací proces:

![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/e8a5e763-9abd-4443-b696-db842d3f2d4d)

- *Hodnota symbolu* - Symbol může sloužit jako jméno jiné hodnoty. Např *cislo1* může mít hodnotu 1.\
Pokud je symbol jméno hodnoty, pak mu říkáme **proměnná** (variable). Také říkáme, že je symbol na
svou hodnotu **navázán** (bound). Symbol *cislo1* nemá hodnotu (není navázán na žádnou hodnotu; is unbound)

- *Funkce* - ucelená část programu obsahující nějaký výpočet, který počítač umí vykonávat. (Např. aritmetické operace, nebo matematické funkce (kosinus, sinus))\
V Lispu jsou funkce označovány symboly. (+ označuje funkci pro sčítání)\
Symbol označující funkci se nazývá její *název*.\
(+-*/ funkce počítají hodnoty matematických operací; sin,cos,sqrt funkce počítají hodnoty matematických funkcí)

- *Argumenty* - jsou **hodnoty** (vyhodnocené výrazy), které se použijí při aplikaci funkce.

- *Aplikace funkce* - Výpočet výsledku funkce se spustí tak, že se funkce aplikuje na hodnoty (argumenty). Samotnou aplikací rozumíme spuštění kódu, kterým funkce počítá požadovaný výsledek.

- **Logické hodnoty a predikáty**
Relace narozdíl od operací a funkcí (které mají výsledek hodnotu číslo) popisují vztah mezi hodnotami.\
Základní relace mezi čísly: =, <, >, ≤, ≥\
Relace nám říkají zda jsou dvě čísla v určitém vztahu.\
Výraz ve kterém je použita relace se dá chápat jako *tvrzení*, které platí nebo ne.\
Lisp nám k realizaci relací poskytuje *logické (pravdivostní) hodnoty* **t** a **nil**.\
Relace jsou poté realizovány funkcemi, které vracejí t nebo nil jako výsledek. Takové funkce se nazývají **predikáty**.\
t a nil jsou symboly, které se stejně jako čísla vyhodnocují na sebe:

![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/fdbf080b-f8df-46c9-b143-e8f5f0b5df02)

Se symboly t a nil nelze používat jako argumenty funkcí, které pracují s čísly. (+ 1 nil) nefunguje

Pomocí logických hodnot můžeme pracovat s **podmíněnými výrazy**

![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/f64bba6b-d3d1-493d-9b40-3cd91b853a2a)

- **Speciální operátory a makra**
Pro ně neplatí klasický vyhodnovací proces, mají svůj vlastní!

![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/344feebb-916a-4c2e-a434-9bb5aec73ef0)

**Podmíněný výraz** je složený výraz s operátorem **if** (if musí mít 3 podvýrazy)\
If je **speciální operátor**.

![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/c1cb86f8-5eb2-4d30-978d-38cce8a7032d)

Ze 3. bodu plyne, že hodnotou prvního podvýrazu za operátorem if může být i jiná hodnota než t nebo nil.

Operátor setf musí mít za operátorem 2 podvýrazy z nichž první musí být symbol, kterému setf nastaví hodnotu druhého podvýrazu. Hodnota prvního podvýrazu se nevyhodnocuje.\
Setf je **makro**.

![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/f17b13ac-fc75-4250-9f68-867199aecc4f)

- **Obecnější popis vyhodnocovacího procesu**

![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/725e18ca-4fd0-4433-943d-505aa5817be7)
