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


# Funkce a prostředí
- **Uživatelsky definované funkce** - k definování funkce můžeme použít makro *defun*\
V defun určíme název (libovolný symbol), parametry (symboly) a tělo (libovolný výraz) nové funkce\
*Parametry* (formální parametry) / *Argumenty* (aktuální parametry)\
Definice funkcí si můžeme ukládat do souborů, aby jsme je mohli používat při dalším spuštění LispWorks\
Uživatelsky definované funkce - funkce, které jsme si sami definovali\
Primitivní funkce (vestevěné) - funkce, které už v Lispu jsou (sqrt, +, -)

![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/bc7f40bf-9444-4b47-88c5-c5ee69ff71ac)\
![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/ba66cb7d-d1bc-4d71-81bd-52bfae20575a)\
![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/4a0ef3ac-283b-4f99-86e5-cd88d66aec87)

- **Funkce jako abstrakce** - programovaná abstrakce - nemusíme vědět **jak** funkce dojde k výsledku, stačí vědět co funkce dělá

![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/7a95f943-11a7-4536-9429-534b8a778b8b)

- **Výhody programové abstrakce**
  - nemusíme řešit tolik problémů (nemusíme řešit jak funkce počítá obsah trojúhelníka)
  - zvyšuje srozumitelnost
  - snadněji se dělají změny
  - snižuje opakování v kódu a tím chybovost
  - zvyšuje se možnost znovupoužitelnosti programu

- **Vazby**
  - Každý symbol může mít více *vazeb*
  - Jedna vazba může být *aktuální* a *zastiňuje* ostatní vazby (na obr. tučně)
  - Každá vazba má *hodnotu*
  - Hodnotu symbolu je vždy **hodnota jeho aktuální vazby**

![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/49562e35-1b94-43c1-92b1-1adf5129681a)

Při zavolání funkce se na parametr vytvoří nová vazba a ta se stane aktuální (zastíní ostatní),\
po vyhodnocení těla funkce vazba přestane být aktuální.

**Vazba na symbol pi se nevytváří a nenastavuje, aktuální zůstává původní vazba**

- **Prostředí**\
Vazby jsou organizovány v *prostředí* (Tabulka se symboly a hodnotami, ze které Lisp zjišťuje vazby mezi nimi)\
Globální prostředí - když Lisp nenajde vazbu pro symbol v aktuálním prostředí funkce, tak se podívá do předka, globální prostředí je "poslední" předek všech prostředí (globální prostředí nemá předka)\
Řádky v tabulce jsou vazby

![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/1f9c78ef-b907-449b-a2bd-6644a48ceee0)

![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/6bd7cd35-67bd-4e52-91e7-f98b9a5d5ad5)\
![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/81d27a9a-0042-4ac6-8370-95e37b417f38)

- Vyhodnocování - výraz se vždy vyhodnocuje v nějakém prostředí (správný pojem vyhodnocení je **vyhodnocení výrazu v prostředí**)
- *Aktuální prostředí* je prostředí, ve kterém je výraz vyhodnocován
- Jediné upřesnění ve vyhodnocování **složených výrazů** se týká vyhodnocování podvýrazů, to probíhá vždy ve stejném prostředí, jako vyhodnocování původního složeného výrazu (Pokud není uvedeno jinak)
- **Vyhodnocování symbolů** - nejdříve se hledá jeho vazba v aktuálním prostředí, pokud je nalezena, tak hodnota symbolu je hodnota vazby, pokud není nalezena, tak se hodnota hledá v předkovi aktuálního prostředí dokud nedojde do globálního prostředí, pokud není ani v globálním, tak dojde k chybě
- Při **aplikaci uživatelské funkce** se vytvoří nové prostředí s vazbami parametrů na argumenty (předkem se stane globální prostředí) v tomto prostředí se pak vyhodnotí tělo funkce, nové prostředí se vytváří při každé aplikaci znovu

#### Vytváření prostředí operátorem *let*
- speciální operátor *let* nám umožňuje explicitně vytvářet nová prostředí
  - **popis prostředí** - seznam libovolné délky, jeho prvky jsou popisy vazeb
  - **popis vazby** - dvouprvkový seznam, na 1. místě symbol, na 2. místě libovolný výraz
  - **tělo** - libovolný výraz

![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/9646e043-d522-4d24-864f-58ac73b83b2c)\
![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/49d9a9be-3bcb-4229-af74-5b377cadf4f3)

