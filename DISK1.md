# Logika
- Věda o správném usuzování, studuje **formy** (usuzování musí mít správnou formu), na obsahu usuzování nezáleží.
- Má **symbolický charakter** (také můžeme říct *formální* logika), symboly umožňují snadněji odhlédnout od obsahu:
  - Symboly pro tvrzení např. - A, B
  - Symboly logických spojení - -> (implikace), atd...
  - Symbol formy - A -> B
- Dále se logika dělí na klasickou a neklasickou:
  - Klasická - má 2 pravdivostí hodnoty (pravda, nepravda), a tzv. klasické logické spojky (např. implikace).
  - Neklasická - používá i neklasické spojky (modální logika), může v ní hrát roli čas (temporální logika), může nabývat více pravdivostních hodnot (fuzzy logika)

Logika nám umožňuje srozumitelně a jednoznačně se vyjadřovat a argumentovat. V informatice nám umožňuje snadněji komunikovat s PC (např. "if then else"). \
Kód musí být srozumitelný. Logika nás učí srozumitelnosti a přesnosti.

## Výroky a logické spojky
- **Výrok** je tvrzení, u kterého má smysl uvažovat zdali je pravdivé nebo ne.
- **Logické spojky** nám umožňují vytvářet složitější výroky
- Pravdivostní hodnoty: 1 (pravda), 0 (nepravda)

## Pravdivostní hodnota výroku
- Pravdivostní hodnotu výroku **V** označujeme **||V||** (např. ||V|| = 1 (výrok je pravda))
- **Atomický výrok** - neobsahuje žádné logické spojky (prostě A), pravdivostní hodnota je dána z "venčí" (1 nebo 0) ||V||e (to *e* je jako externí zdroj, proto by jsme měli spíše psát ||V||e místo ||V||, jinak řečeno e přiřazuje atomickému výroku V pravdivostní hodnotu)
- **Složený výrok** - obsahuje logické spojky (A -> B), musíme jeho pravdivostní hodnotu "spočítat" ||A -> B|| = ||A|| -> ||B|| (nejdřív ohodnotíme atomické výroky a poté spočítáme pomocí pravdivostních funkcí spojek (tabulek spojek)), také se často používají ve složených výrocích závorky, aby jsme jednoznačně vyznačili strukturu výroku

Každá logická spojka má své označení (symbol) a význam (pravdivostní fuknci)
### Základní logické spojky:
![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/3f2ff78c-d1e3-42b0-8d21-c979f7c0d1aa)
### Postup určování pravdivostní hodnoty výroku:
![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/f8919fde-3371-4b4c-83b2-7952fa58d868)
![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/8fed6af1-36b2-4d39-8eb2-c9c44c92d5e7)

## Kvantifikátory a pravdivostní hodnoty výroků s kvantifikátory
Výraz obsahující proměnou není výrok, výrok se z něj stane až po dosazení za proměnou.\
Takovému výrazu se říká **výroková forma**

Výroky se označovali písmenem - např. V \
Výrokové formy se označují písmenem s proměnými, které výrok obsahuje, v závorkách za ním - např. V(x, y) \
Pro každou *x* ve výrokové formě bychom měli zadat **obor hodnot** (množinu D<sub>x</sub>), kterých může proměnná *x* nabývat.

Další způsob jak z výrokové formy vytvořit výrok je za pomocí **kvantifikátorů**. \
V klasické logice jsou 2 kvantifikátory:
- **Obecný** (∀x) "Pro každý x platí, že..."
- **Existenční** (∃x) "Existuje x tak, že platí..."
  - Příklad: ”(∃x) (x je větší nebo rovno 1).“, popř. ”(∃x) (x ≥ 1)“

*Volný výskyt* - když proměnná není v dosahu platnosti kvantifikátoru

**Pravdivostní hodnotu kvantifikátoru** určujeme pravidly ||(∀x)V(x)|| a ||(∃x)V(x)||
![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/71fa0e2c-5a71-4a9d-9102-9c363ad59c74)
![obrazek](https://github.com/Rexpes/upol_matros/assets/84129869/96f968d3-d21b-4df2-a367-50065c620610)

# Množiny
Množina je neuspořádané uskupení prvků (např. čísla, jména, auta, atd.)
Nezáleží na pořadí ani na tom kolikrát tam daný prvek je. 

## _(*Tonda: jakoby on tam ten prvek podle mě ani nemůže být víckrát. Že jakoby když ho tam napíšeš dvakrát, tak to znamená, že tam je jednou, protože tam nemůže být víckrát než jednou)_

# Vennův diagram
