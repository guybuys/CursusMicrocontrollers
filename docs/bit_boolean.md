# Bit en Boolean – de kleinste eenheid

## Wat is een bit?

Een **bit** is de kleinste eenheid van informatie in een computer.  
Een bit kan maar 2 waarden hebben: alleen de waarde **0** of **1**.

Deze 2 waarden kunnen, afhankelijk van de context, anders genoemd worden, zo kan een **0** ook *uit, laag* of *onwaar* genoemd worden en een **1** op zijn beurt *aan, hoog* of *waar*.

## Wat is een variabele?

Een **variabele** is een naam voor een stukje geheugen in de computer waar je informatie in kunt opslaan.  

Je kunt een variabele zien als een doosje met een label erop: je stopt er een waarde in, en je kunt die waarde later weer gebruiken of veranderen. Door het gebruik van variabelen, kunnen we krachtige en leesbare programma's maken.

Een variabele heeft altijd een **naam** en een **datatype**.

> Met variabelen kun je informatie onthouden met de naam van de *variabele* als `label`. Bijvoorbeeld: `spanning = 230` waarbij we naar de waarde *230* kunnen refereren als *spanning*.

## Wat zijn datatypes?

Een **datatype** bepaalt welk soort informatie een *variabele* kan opslaan in een programma.

- Voor een bit (waar/onwaar) gebruik je het datatype **boolean**.
- Andere datatypes, die we later nog uitgebreid gaan bespreken, bestaan uit meerdere bits. Bijvoorbeeld:
  - **integer**: een ***geheel getal*** of een getal zonder decimalen (meestal 8, 16 of 32 bits)
  - **float**: een  ***kommagetal*** of getal met decimalen
  - **string**: een stukje tekst

Hoe meer bits een datatype heeft, hoe meer verschillende waarden je ermee kunt opslaan.  

Een boolean kan maar twee waarden hebben (**0** of **1**), maar een *unsigned integer* (geheel getal zonder teken) van **8 bits** kan bijvoorbeeld waarden van **0** tot **255** bevatten.

> Het juiste ***datatype*** kiezen is belangrijk om je programma goed te laten werken!

## Boolean in code

In programmeertalen gebruik je het datatype **boolean** om met waar/onwaar te werken.

### In C++

In C++ moet je het datatype van een variabele altijd **expliciet** vermelden.

Bij een boolean betekent **0** hetzelfde als `false` en **1** hetzelfde als `true`.

```cpp
// cpp
bool ledAan = true;   // LED aan
bool knopIngedrukt = false; // Knop niet ingedrukt
```

> In het bovenstaande voorbeeld, hebben we 2 variabelen gemaakt: `ledAan` en `knopIngedrukt`. Ze zijn van het *type* **bool** (boolean) en hebben de respectievelijke *waarde* `true` en `false`.

### In MicroPython

In MicroPython hoef je het datatype van een variabele **niet expliciet** te vermelden. Python kiest zelf het type op basis van de waarde.

Toch is het **heel belangrijk** om zelf goed te weten welk type je gebruikt.  
Ook hier geldt: **0** is `False` en **1** is `True`. Let op: in Python schrijf je *True* en *False* altijd met een **hoofdletter**!

```python
# MicroPython
led_aan = True      # LED aan
knop_ingedrukt = False  # Knop niet ingedrukt
```

> In het bovenstaande voorbeeld, hebben we 2 variabelen gemaakt: `led_aan` en `knop_ingedrukt`. We kunnen enkel aan de waarde zien dat ze van het *type* **boolean**  zijn: ze hebben namelijk de respectievelijke *waarde* `True` en `False`.

## Waar kom je bits en booleans tegen?

- Bij het aansturen van uitgangen (LED aan/uit)
- Bij het uitlezen van ingangen (knop ingedrukt of niet)
- In logische beslissingen (if-statements)

> Een boolean is dus een handige manier om met *ja/nee*-vragen in je programma te werken!

## Boolean operatoren

Een **operator** is een symbool dat een bewerking uitvoert op één of meer waarden.  
Bij booleans hebben we drie belangrijke operatoren: **NOT**, **AND** en **OR**.

### NOT operator (omkeren)

De **NOT** operator keert een boolean waarde om:

- `NOT true` wordt `false`
- `NOT false` wordt `true`

**Gebruik:** Om het tegenovergestelde van een conditie te krijgen.  
Bijvoorbeeld: "Als de knop NIET ingedrukt is..."

### AND operator (beide waar)

De **AND** operator geeft alleen `true` als **beide** waarden `true` zijn:

- `true AND true` = `true`
- `true AND false` = `false`
- `false AND true` = `false`
- `false AND false` = `false`

**Gebruik:** Om te controleren of meerdere voorwaarden tegelijk waar zijn.  
Bijvoorbeeld: "Als knop A ingedrukt is EN knop B ingedrukt is..."

### OR operator (één van beide waar)

De **OR** operator geeft `true` als **minstens één** van de waarden `true` is:

- `true OR true` = `true`
- `true OR false` = `true`
- `false OR true` = `true`
- `false OR false` = `false`

**Gebruik:** Om te controleren of één van meerdere voorwaarden waar is.  
Bijvoorbeeld: "Als knop A ingedrukt is OF knop B ingedrukt is..."

### Syntax in C++

```cpp
bool knop1 = true;
bool knop2 = false;

// NOT operator (!)
bool nietKnop1 = !knop1;          // false

// AND operator (&&)
bool beideKnoppen = knop1 && knop2;  // false

// OR operator (||)
bool eenVanBeide = knop1 || knop2;   // true

```

Syntax in MicroPython

```python
knop1 = True
knop2 = False

# NOT operator (not)
niet_knop1 = not knop1          # False

# AND operator (and)
beide_knoppen = knop1 and knop2  # False

# OR operator (or)
een_van_beide = knop1 or knop2   # True
```

---

## Extra: Naamgeving van variabelen

Probeer altijd een naam te kiezen die **duidelijk** maakt wat de variabele voorstelt.

Bij het kiezen van een *variabelenaam* is het handig om een duidelijke *conventie* te volgen.  
Dit maakt je code beter leesbaar en begrijpelijk voor anderen (en jezelf!).

- **In C++** gebruiken programmeurs vaak de **camelCase**-notatie.  
  Hierbij begint de naam met een kleine letter en elk nieuw woord krijgt een hoofdletter.
  Bijvoorbeeld: `ledAan`, `knopIngedrukt`

- **In MicroPython** (en Python in het algemeen) wordt meestal de **snake_case**-notatie gebruikt.  
  Hierbij worden woorden gescheiden door een *underscore* (_), alles in kleine letters.
  Bijvoorbeeld: `led_aan`, `knop_ingedrukt`

> Het is **niet verplicht**, maar het volgen van deze *conventies* maakt je code **overzichtelijker**!
Het volgen van conventies maakt je code overzichtelijker en wordt vaak gewaardeerd door docenten en programmeurs.
