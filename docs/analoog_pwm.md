# Analoge signalen en PWM

## ADC (Analog-to-Digital Converter)
Sommige pinnen kunnen een spanning meten (0–3.3 V).

```cpp
// Arduino (C++) voorbeeld
int potPin = A0;
int waarde;
void setup() {
  Serial.begin(9600);
}
void loop() {
  waarde = analogRead(potPin); // 0–1023
  Serial.println(waarde);
}
```

```python
# MicroPython voorbeeld
from machine import ADC, Pin
pot = ADC(Pin(26))
waarde = pot.read_u16() # 0–65535
print(waarde)
```

## PWM (Pulse Width Modulation)
LED dimmen door het signaal snel aan/uit te schakelen.

```cpp
// Arduino (C++) voorbeeld
int ledPin = 9;
void setup() {
  pinMode(ledPin, OUTPUT);
}
void loop() {
  analogWrite(ledPin, 128); // halve helderheid
}
```

```python
# MicroPython voorbeeld
from machine import PWM, Pin
led = PWM(Pin(25))
led.duty_u16(32768) # halve helderheid
```

![Plaats voor schema potmeter/LED](PLACEHOLDER_POTMETER_LED_SCHEMA)
