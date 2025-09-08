# GPIO – General Purpose Input/Output

GPIO staat voor General Purpose Input/Output. Dit zijn de pinnen op een microcontroller die je kunt gebruiken als input (iets meten) of output (iets aansturen).

- GPIO als output: bijvoorbeeld een LED aan/uit zetten.
- GPIO als input: bijvoorbeeld een knop uitlezen.

GPIO is de brug tussen de concepten input/output en de echte hardware.

## Voorbeeld: LED aansturen (output)

```cpp
// Arduino (C++) voorbeeld
int ledPin = 13;
void setup() {
  pinMode(ledPin, OUTPUT);
}
void loop() {
  digitalWrite(ledPin, HIGH); // LED aan
  delay(1000);
  digitalWrite(ledPin, LOW);  // LED uit
  delay(1000);
}
```

```python
# MicroPython voorbeeld
from machine import Pin
import time
led = Pin(25, Pin.OUT)
while True:
    led.value(1)  # LED aan
    time.sleep(1)
    led.value(0)  # LED uit
    time.sleep(1)
```

## Voorbeeld: Knop uitlezen (input)

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

> Meer weten? Bekijk de pagina's over input en output voor de concepten achter deze voorbeelden.
