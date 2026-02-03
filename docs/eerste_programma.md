# Je eerste volledige programma

Nu we de basisconcepten kennen (input, output, GPIO, datatypes), gaan we een **volledig programma** schrijven!  
We leren hoe je je code moet structureren en hoe de microcontroller deze uitvoert.

---

## De structuur van een programma

### In C++ (Arduino)

Een Arduino-programma bestaat altijd uit **twee hoofdfuncties**:

```cpp
void setup() {
    // Deze code wordt EENMAAL uitgevoerd bij het opstarten
}

void loop() {
    // Deze code wordt HERHAALDELIJK uitgevoerd (eindeloze lus)
}
```

**setup()** - Voorbereiding

- Wordt één keer uitgevoerd wanneer de Arduino opstart
- Hier configureer je de GPIO pinnen
- Hier start je seriële communicatie, die we later nog zullen zien
- Hier stel je startwaardes in
  
**loop()** - Hoofdprogramma

- Wordt oneindig herhaald
- Hier lees je bijvoorbeeld sensoren uit
- Hier neem je beslissingen
- Hier stuur je actuatoren (zoals motoren, LEDs, ...) aan
  
### In MicroPython

In MicroPython schrijf je je programma van **boven naar beneden**:

``` python
from machine import Pin

# Configuratie (vergelijkbaar met Arduino's setup)
led = Pin(25, Pin.OUT)
button = Pin(14, Pin.IN, Pin.PULL_UP)

# Hoofdprogramma (vergelijkbaar met Arduino's loop)
while True:
    # Deze code wordt oneindig herhaald
    pass
```

**Bovenaan** - Voorbereiding

- Bibliotheken importeren
- GPIO pinnen configureren
- Variabelen initialiseren

**while True:** - Hoofdprogramma

- Oneindig herhalende lus (zoals Arduino's loop)
- Hier komt je hoofdcode
  
  ---

## Voorbeeld 1: LED knipperen

C++ (Arduino)

``` cpp
// Configuratie
int ledPin = 13;

void setup() {
    // Eenmalige voorbereiding
    pinMode(ledPin, OUTPUT);
}

void loop() {
    // Herhaal oneindig
    digitalWrite(ledPin, HIGH);  // LED aan
    delay(1000);                 // Wacht 1 seconde
    digitalWrite(ledPin, LOW);   // LED uit
    delay(1000);                 // Wacht 1 seconde
}
```

MicroPython

``` python
from machine import Pin
import time

# Configuratie
led = Pin(25, Pin.OUT)

# Hoofdprogramma
while True:
    led.value(1)      # LED aan
    time.sleep(1)     # Wacht 1 seconde
    led.value(0)      # LED uit
    time.sleep(1)     # Wacht 1 seconde
```

---

## Voorbeeld 2: LED met knop besturen

C++ (Arduino)

``` cpp
// Pin configuratie
int ledPin = 13;
int buttonPin = 2;

void setup() {
    // Configureer pinnen (eenmalig)
    pinMode(ledPin, OUTPUT);
    pinMode(buttonPin, INPUT_PULLUP);
}

void loop() {
    // Lees knop uit
    bool buttonPressed = !digitalRead(buttonPin);  // Pull-up: signaal omdraaien
    
    // Stuur LED aan
    if (buttonPressed) {
        digitalWrite(ledPin, HIGH);  // LED aan
    } else {
        digitalWrite(ledPin, LOW);   // LED uit
    }
}
```

MicroPython

``` python
from machine import Pin

# Configuratie
led = Pin(25, Pin.OUT)
button = Pin(14, Pin.IN, Pin.PULL_UP)

# Hoofdprogramma
while True:
    # Lees knop uit
    button_pressed = not button.value()  # Pull-up: False = ingedrukt
    
    # Stuur LED aan
    if button_pressed:
        led.value(1)  # LED aan
    else:
        led.value(0)  # LED uit
```

---

## Voorbeeld 3: Teller met knop

C++ (Arduino)

``` cpp
// Pin configuratie
int buttonPin = 2;

// Variabelen
unsigned int teller = 0;
bool vorigeKnopStatus = HIGH;

void setup() {
    pinMode(buttonPin, INPUT_PULLUP);
    Serial.begin(9600);  // Start seriële communicatie
    Serial.println("Teller gestart!");
}

void loop() {
    // Lees huidige knopstatus
    bool huidigeKnopStatus = digitalRead(buttonPin);
    
    // Detecteer druk op knop (overgang van HIGH naar LOW)
    if (vorigeKnopStatus == HIGH && huidigeKnopStatus == LOW) {
        teller++;  // Verhoog teller
        Serial.print("Teller: ");
        Serial.println(teller);
        delay(50);  // Korte pauze voor debouncing
    }
    
    // Onthoud status voor volgende loop
    vorigeKnopStatus = huidigeKnopStatus;
}
```

MicroPython

``` python
from machine import Pin
import time

# Configuratie
button = Pin(14, Pin.IN, Pin.PULL_UP)

# Variabelen
teller = 0
vorige_knop_status = True

print("Teller gestart!")

# Hoofdprogramma
while True:
    # Lees huidige knopstatus
    huidige_knop_status = button.value()
    
    # Detecteer druk op knop (overgang van True naar False)
    if vorige_knop_status and not huidige_knop_status:
        teller += 1  # Verhoog teller
        print(f"Teller: {teller}")
        time.sleep(0.05)  # Korte pauze voor debouncing
    
    # Onthoud status voor volgende loop
    vorige_knop_status = huidige_knop_status
```

---

## Belangrijke concepten

1. Variabelen buiten de lus

    **C++:**

    ``` cpp
    unsigned int teller = 0;  // Buiten setup() en loop()

    void setup() { }
    void loop() {
        teller++;  // Behoudt zijn waarde tussen loops
    }
    ```

    **MicroPython:**

    ``` python
    teller = 0  # Boven de while-lus

    while True:
        teller += 1  # Behoudt zijn waarde tussen loops
    ```

2. Debouncing

    Knoppen kunnen "stuiteren" (bounce) bij het indrukken, waardoor meerdere signalen gedetecteerd worden.

    **Oplossingen:**

   - Korte `delay()` of `time.sleep()` na detectie
   - Status alleen veranderen bij overgang (van HIGH naar LOW)
   - Hardware debouncing met condensator

3. Timing
    **C++:**

   - `delay(milliseconden)` - Blokkeert het programma
   - `millis()` - Geeft tijd sinds opstart (niet-blokkerend)

    **MicroPython:**

   - `time.sleep(seconden)` - Blokkeert het programma
   - `time.ticks_ms()` - Geeft tijd sinds opstart (niet-blokkerend)

---

## Oefeningen

1. Knipperende LED met variabele snelheid

   - Maak een LED die knippert
   - Gebruik een variabele voor de knippersnelheid
   - Verander de snelheid tijdens het programma

2. Twee knoppen, twee LED's

    - Knop A bedient LED 1
    - Knop B bedient LED 2
    - Beide onafhankelijk van elkaar
<!--  
3. Toerenteller

    - Tel hoe vaak een knop is ingedrukt
    - Toon het aantal op de seriële monitor
    - Reset de teller na 10 drukken
-->  