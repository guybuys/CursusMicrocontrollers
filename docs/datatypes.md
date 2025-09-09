# Meer datatypes

## Unsigned integer
Een teller die het aantal keer dat je op een knop drukt bijhoudt.

```cpp
// Arduino (C++) voorbeeld
unsigned int teller = 0;
int buttonPin = 2;
void setup() {
  pinMode(buttonPin, INPUT);
}
void loop() {
  if (digitalRead(buttonPin) == HIGH) {
    teller++;
    delay(200); // debounce
  }
}
```

```python
# MicroPython voorbeeld
from machine import Pin
button = Pin(14, Pin.IN)
teller = 0
while True:
    if button.value():
        teller += 1
        time.sleep(0.2) # debounce
```

## Signed integer
Negatieve getallen zijn handig, bijvoorbeeld bij temperatuurmetingen.

> Bijvoorbeeld: temperatuur = -5 °C

<!--![Plaats voor teller-schema](PLACEHOLDER_TELLER_SCHEMA)-->
