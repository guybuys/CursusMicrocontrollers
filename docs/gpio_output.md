# GPIO Output – dingen besturen

GPIO als uitgang: hiermee kun je bijvoorbeeld een LED aan of uit zetten.

## LED schakelen

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

> **Let op:** HIGH (1) / LOW (0) betekent aan/uit (Boolean).

**Boolean variabelen:**
- C++: `true` / `false`
- Python: `True` / `False`

![Plaats voor LED-schema](PLACEHOLDER_LED_SCHEMA)
