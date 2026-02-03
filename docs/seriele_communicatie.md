# Seriële communicatie

Seriële communicatie is een manier om gegevens bit voor bit te verzenden tussen twee apparaten. Het is eenvoudig, betrouwbaar en zit standaard op bijna elke microcontroller.

## Inleiding: communiceren met pulsen

Stel je voor dat je geen letters kunt sturen, maar alleen een lampje dat **aan** of **uit** kan. Door dat lampje op het juiste moment te laten knipperen, kun je toch een boodschap doorgeven. Dat is in essentie **binair**: twee toestanden die veranderen in functie van de tijd.

Een bekend voorbeeld is **morsecode**. Daarin zijn er **korte** en **lange** signalen (punt en streep). Het beroemde SOS‑signaal is:

- **S** = `...` (kort‑kort‑kort)
- **O** = `---` (lang‑lang‑lang)
- **S** = `...` (kort‑kort‑kort)

Zo kun je met alleen aan/uit toch betekenis overbrengen. Dat idee is de basis van digitale communicatie.

![Placeholder: morse SOS timingdiagram](img/morse_sos_placeholder.png)

## Van morse naar ASCII

Morse is handig voor mensen, maar computers gebruiken liever vaste afspraken: **elke letter krijgt een getal**. Die afspraak heet **ASCII** (American Standard Code for Information Interchange).

Voorbeelden:

- `A` = 65
- `B` = 66
- `a` = 97
- `0` = 48

In een **ASCII‑tabel** staat precies welk getal bij welk teken hoort. Zo kan een computer een letter sturen als een **getal**, en dat getal wordt door de ontvanger weer omgezet naar hetzelfde teken.

Vanaf hier kijken we hoe microcontrollers die getallen echt verzenden, bit voor bit, via seriële communicatie.

## Leerdoelen

- Begrijpen wat UART/serial is
- Weten wat baudrate, databits, pariteit en stopbits betekenen
- Een basisverbinding kunnen maken tussen microcontroller en PC of tussen twee microcontrollers

## Hoe werkt het?

Bij UART (Universal Asynchronous Receiver/Transmitter) sturen apparaten data asynchroon: er is geen aparte kloklijn nodig. In plaats daarvan spreken beide kanten dezelfde **baudrate** af (bijv. 9600, 115200). Elke byte krijgt een startbit, databits, een optionele pariteitsbit en een stopbit.

## Belangrijkste begrippen

- **Baudrate**: snelheid in bits per seconde.
- **Databits**: meestal 8 bits per byte.
- **Pariteit**: extra foutcontrole (vaak `None`).
- **Stopbits**: meestal 1.

## Bekabeling

Een basisverbinding (TTL‑niveau) heeft minimaal:

- **TX → RX** (kruisen!)
- **RX → TX**
- **GND ↔ GND**

Let op: seriële pinnen werken op logische niveaus (bijv. 5V of 3.3V). Gebruik een level shifter als de spanningen verschillen.

## Voorbeeld (Arduino)

```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  Serial.println("Hallo via serial!");
  delay(1000);
}
```

## Voorbeeld (MicroPython)

```python
from machine import UART
import time

uart = UART(0, 9600)

while True:
    uart.write("Hallo via serial!\n")
    time.sleep(1)
```

## Toepassingen

- Debuggen via de seriële monitor
- Data loggen naar een PC
- Communicatie tussen meerdere microcontrollers

## Oefening

- Stuur om de seconde een tellerwaarde via de seriële poort.
- Laat de ontvanger de waarde terugsturen (echo) en toon dit op de seriële monitor.
