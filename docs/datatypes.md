# Meer datatypes

## Van 1 bit naar 8 bits

We hebben al gezien dat **1 bit** maar 2 waarden kan hebben: **0** of **1**.  
Maar wat als we meer verschillende waarden of grotere getallen willen opslaan? Dan combineren we meerdere bits!

### Met 8 bits kun je 256 verschillende waarden maken

Stel je voor dat je **8 lampjes** naast elkaar hebt. Elk lampje kan **aan** (1) of **uit** (0) zijn.  
Door verschillende combinaties te maken, kun je **256 verschillende patronen** creëren!

Voorbeelden:

- `00000000` = 0
- `00000001` = 1  
- `00000010` = 2
- `00000011` = 3
- `11111111` = 255

> Met **8 bits** kun je dus getallen van **0 tot 255** voorstellen!

|Bit 7|Bit 6|Bit 5|Bit 4|Bit 3|Bit 2|Bit 1|Bit 0|
|-----|-----|-----|-----|-----|-----|-----|-----|
| 2⁷  | 2⁶  | 2⁵  | 2⁴  | 2³  | 2²  | 2¹  | 2⁰  |
| 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   |

Bijvoorbeeld: het getal 42 zou er zo uitzien:

42 = 32 + 8 + 2 = `00101010`

### Waarom is dit handig?

- **Tellen**: In plaats van alleen 0 en 1, kun je nu tot 255 tellen.
- **Sensoren**: Een temperatuursensor kan waarden van 0°C tot 255°C meten.
- **Kleuren**: Elk van de kleuren rood, groen en blauw gebruikt 8 bits (0-255).

---

## Datatypes in C++ (Arduino)

In **C++** moet je altijd aangeven welk **datatype** je gebruikt. Dit helpt de computer om te weten hoeveel geheugen hij moet reserveren.

### unsigned char

#### Klein geheel getal zonder minteken (8 bits)

```cpp
unsigned char helderheid = 255;  // Kan waarden van 0 tot 255 bevatten
unsigned char percentage = 75;   // Perfect voor percentages
```

**Gebruik:** Voor kleine getallen die precies in de 8-bit range passen:

- LED helderheid (0-255)
- Percentages (0-100)
- Sensor waarden die al geschaald zijn naar 0-255
- RGB kleurwaarden (rood, groen, blauw elk 0-255)

> Zie je het verband? Dit gebruikt precies de 8 bits die we net hebben uitgelegd!

### char

#### Karakter of klein getal

```cpp
char letter = 'A';     // Voor letters
char kleinGetal = 42;  // Voor getallen van -128 tot +127
```

**Waarom heet dit datatype 'char'?**

`char` is de afkorting van **'character'** (karakter). Oorspronkelijk was dit datatype bedoeld om letters en tekens op te slaan.

**Het geheim:** Karakters worden eigenlijk opgeslagen als **kleine gehele getallen**!
Elk karakter heeft een nummer in de ASCII-tabel:

- 'A' = 65
- 'B' = 66
- '0' = 48
- '1' = 49

> **Let op!** Bij een karakter staat er in C++ steeds een enkele quote ``` ' ``` voor en na het karakter.

**Voorbeelden:**

```cpp
char letter = 'A';        // Slaat eigenlijk het getal 65 op
char getal = 65;          // Dit is hetzelfde als 'A'!
char cijfer = '5';        // Slaat het getal 53 op (niet het getal 5!)
```

**Gebruik:**

- Voor een letter of teken
- Voor heel kleine getallen (-128 tot +127) om geheugen te besparen
- Bij communicatie waar elke byte telt

> **Interessant:** Je kunt *rekenen* met karakters! 'A' + 1 geeft 'B'.

### unsigned int

**Geheel *groter* getal zonder minteken**

 Hiervoor worden 16 bits gebruikt

```cpp
unsigned int teller = 0;  // Kan waarden van 0 tot 65535 bevatten
```

**Gebruik:** Voor getallen die nooit negatief worden, zoals:

- Aantal keer dat je op een knop drukt
- Sensor waarden (0-1023 van een potmeter)
- Tijd in milliseconden

### (signed) int

#### Geheel getal met minteken

``` cpp
int temperatuur = -5;  // Kan waarden van -32768 tot +32767 bevatten
```

**Gebruik:** Voor getallen die ook negatief kunnen zijn, zoals:

- Temperatuur (kan onder 0°C zijn)
- Positie (links/rechts van een startpunt)
- Verschil tussen twee metingen

### float

#### Kommagetal (decimaal getal)

```cpp
float temperatuur = 23.5;     // Kan decimalen hebben
float spanning = 3.14159;     // Pi met decimalen
```

**Wat is een float?**

Een **float** is een getal met een **komma** (eigenlijk punt in code). Het kan dus ook ***gebroken* getallen** voorstellen.

**Voorbeelden:**

- Temperatuur: `20.3°C` in plaats van alleen `20°C`
- Spanning: `3.7V` in plaats van alleen `3V`
- Afstand: `12.45 meter`

**Gebruik:** Voor metingen die preciezer moeten zijn dan hele getallen:

- Temperatuursensoren (23.4°C)
- Spanningsmetingen (3.7V)
- Afstandsmetingen (15.6 cm)
- Berekeningen (gemiddelden, procenten)

**Let op:** Floats zijn **minder nauwkeurig** dan je denkt! Soms krijg je `3.9999999` in plaats van `4.0`. Dit komt omdat ze *binair* opgeslagen worden.

## Datatypes in MicroPython

In **MicroPython** hoef je het datatype **niet expliciet** te vermelden. Python kiest automatisch het juiste type op basis van de waarde die je opslaat.

**Maar**: Het is nog steeds belangrijk dat **jij** weet welk datatype je gebruikt!

### Gehele getallen (integers)

```python
teller = 0        # Python kiest automatisch 'int'
temperatuur = -5  # Ook een 'int', maar kan negatief zijn
```

**Python is slim:** Het maakt automatisch genoeg ruimte voor je getal, ook als het heel groot wordt!

### Karakters en tekst (strings)

```python
letter = 'A'           # Eén karakter
tekst = "Hallo wereld" # Hele zin
```

### Kommagetallen (floats)

```python
temperatuur = 23.5      # Python herkent automatisch dat dit een float is
spanning = 3.14159      # Ook een float
```

**Python is nog slimmer:** Het herkent automatisch of je getal een **integer** (geheel getal) of **float** (kommagetal) is!

```python
geheel_getal = 25        # Dit is een int
komma_getal = 25.0       # Dit is een float (let op de .0)
```

## Samenvatting

### C++ (Arduino)

- Je moet het datatype aangeven
- Beperkte ruimte per datatype
- Sneller en gebruikt minder geheugen

### MicroPython

- Python **kiest** automatisch het datatype
- Onbeperkte ruimte (binnen grenzen van de microcontroller)
- Langzamer maar gemakkelijker te programmeren

> Tip: Ook in Python is het handig om te weten welk type je gebruikt, vooral bij sensoren die bepaalde waardenbereiken hebben!
