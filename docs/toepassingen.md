# Samenspel en toepassingen

## Input + Output combineren
Dimmen van een LED met een potmeter, of een knop die de toonhoogte van een buzzer verandert.

### Mini verkeerslicht

```cpp
// Arduino (C++) voorbeeld
int ledR = 10, ledG = 11, ledY = 12, button = 2;
void setup() {
  pinMode(ledR, OUTPUT);
  pinMode(ledG, OUTPUT);
  pinMode(ledY, OUTPUT);
  pinMode(button, INPUT);
}
void loop() {
  if (digitalRead(button) == HIGH) {
    digitalWrite(ledR, HIGH);
    delay(1000);
    digitalWrite(ledR, LOW);
    digitalWrite(ledG, HIGH);
    delay(1000);
    digitalWrite(ledG, LOW);
    digitalWrite(ledY, HIGH);
    delay(500);
    digitalWrite(ledY, LOW);
  }
}
```

```python
# MicroPython voorbeeld
from machine import Pin
import time
ledR = Pin(15, Pin.OUT)
ledG = Pin(14, Pin.OUT)
ledY = Pin(13, Pin.OUT)
button = Pin(12, Pin.IN)
while True:
    if button.value():
        ledR.value(1)
        time.sleep(1)
        ledR.value(0)
        ledG.value(1)
        time.sleep(1)
        ledG.value(0)
        ledY.value(1)
        time.sleep(0.5)
        ledY.value(0)
```

> **Projectideeën:**
- Reaction game met knop en LED
- Toonhoogte veranderen met knop en buzzer

![Plaats voor verkeerslicht-schema](PLACEHOLDER_VERKEERSLICHT_SCHEMA)
