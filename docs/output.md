# Output – Dingen aansturen

Output betekent dat de microcontroller iets aanstuurt of laat gebeuren. Dit kan bijvoorbeeld een LED, een motor, een buzzer of een display zijn.

We kunnen dit begrijpen door in te beelden dat er een SPDT schakelaar in de microcontroller zou zitten die het signaal verbind met de **VCC** (dit is de voedingsspanning, meestal 5V of 3,3V) ofwel met de **GND** (grond, ground of 0V).

 **Schema:** 
 ![Schema Actief Hoog](img\ac_output_ah.png)

In het bovenstaande voorbeeld zien we dat pin 3 aangesloten is aan een **LED** met een **serie weerstand**. De microcontroller (of het microcontroller bord) is ook aan gesloten aan een spanningsbron of voeding. De uitgang op pin 3 kan verbonden worden met ofwel **VCC** ofwel **GND**. Zoals het in het schema staat, is de uitgang op dit moment verbonden met **VCC** waardoor er stroom door de LED en serieweerstand loopt en de LED licht geeft. Het is mogelijk in het programma van de microcontroller om de output te verbinden met **GND**. Wanneer dat gebeurd, zal er geen stroom vloeien en gaat de LED uit.

Om een uitgang, aangesloten op *ledPin* (in ons voorbeeld is *ledPin* gelijk aan 3), aan te zetten (of *"hoog"* te zetten), gebruiken we deze instructie in **C++**, de taal die **Arduino** gebruikt.

```cpp
// cpp
digitalWrite(ledPin, HIGH); // LED aan
```   
We kunnen de uitgang ook uit zetten, dit doen we dan zo:

```cpp
// cpp
digitalWrite(ledPin, LOW); // LED uit
``` 
In **MicroPython** zou het er zo uit zien:
```python
# MicroPython
led.value(True); # LED aan
``` 
En voor uit te schakelen:

```python
# MicroPython
led.value(False); # LED uit
```

Het is ook mogelijk om de LED op een andere manier aan te sluiten:

 **Schema:** 
 ![Schema Actief Laag](img\ac_output_al.png)

 Dit schema en de werking zijn nagenoeg hetzelfde maar de LED en de serieweerstand zijn aan **VCC** aangesloten in plaats van aan **GND**. Dit wil zeggen dat de LED nu zal licht geven wanneer de uitgang van de microcontroller met **GND** verbonden is en zal uit zijn wanneer hij met **VCC** verbonden is. Dit noemen we **actief laag** terwijl het eerste schema **actief hoog** genoemd wordt. Een 1 of een 0, HIGH of LOW, True of False hebben in beide schema's dus een andere uitwerking. Het is belangrijk om hiermee rekening te houden.
 