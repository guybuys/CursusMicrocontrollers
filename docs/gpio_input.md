# GPIO Input – dingen meten

GPIO als ingang: hiermee kun je bijvoorbeeld een knop uitlezen.

## Knop indrukken

```cpp
// Arduino (C++) voorbeeld
int buttonPin = 2;
int ledPin = 13;
void setup() {
  pinMode(buttonPin, INPUT);
  pinMode(ledPin, OUTPUT);
}
void loop() {
  if (digitalRead(buttonPin) == HIGH) {
    digitalWrite(ledPin, HIGH); // LED aan
  } else {
    digitalWrite(ledPin, LOW);  // LED uit
  }
}
```

```python
# MicroPython voorbeeld
from machine import Pin
button = Pin(14, Pin.IN)
led = Pin(25, Pin.OUT)
while True:
    if button.value():
        led.value(1)
    else:
        led.value(0)
```

> **Debouncing:** Soms "stuitert" een knop, daar kun je later meer over leren.

![Plaats voor schema knop](PLACEHOLDER_KNOP_SCHEMA)
