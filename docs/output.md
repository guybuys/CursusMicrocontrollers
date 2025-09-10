# Output – Dingen aansturen

Output betekent dat de microcontroller iets aanstuurt of laat gebeuren. Dit kan bijvoorbeeld een LED, een motor, een buzzer of een display zijn.

We kunnen dit *voorstellen* door te veronderstellen dat er een SPDT schakelaar in de microcontroller zou zitten die het signaal verbind met de **VCC** (dit is de voedingsspanning, meestal 5V of 3,3V) of met de **GND** (grond, ground of 0V).

 **Schema:** 
 ![Schema Actief Hoog Aan](img\ac_output_ah_on.png)

In het bovenstaande voorbeeld zien we dat pin 3 aangesloten is aan een **LED** met een **serie weerstand**. De microcontroller (of het microcontroller bord) is ook aan gesloten aan een spanningsbron of voeding. De uitgang op *pin 3* kan verbonden worden met ofwel **VCC** ofwel **GND**. Zoals het in het schema staat, is de uitgang op dit moment verbonden met **VCC** waardoor er stroom door de LED en serieweerstand loopt en de LED licht geeft. 

We bekijken nu hoe we, in **C++**, de taal die **Arduino** gebruikt, de uitgang met **VCC** moeten verbinden om de LED te laten branden:

```cpp
// cpp
digitalWrite(3, HIGH); // Pin 3 hoog, LED aan
```
In **MicroPython** ziet het er net iets anders uit. Daar moeten we eerst laten weten dat *led* aan pin 3 aangesloten is. Hoe dat moet, volgt later nog.

```python
# MicroPython
led.value(True); # Uitgang hoog of LED aan
``` 
of
```python
# MicroPython
led.value(1); # Uitgang hoog of LED aan
``` 

We kunnen ook de LED uit zetten, zoals aangegeven in dit **schema:** 
 ![Schema Actief Hoog Uit](img\ac_output_ah_off.png)
Er kan nu geen stroom van **+** naar **-** lopen. In de *code* doen we dit zo:

```cpp
// cpp
digitalWrite(3, LOW); // Pin 3 laag, LED uit
```

In **MicroPython** gaat het zo:
```python
# MicroPython
led.value(False); # Uitgang laag of LED uit
```
of
```python
# MicroPython
led.value(0); # Uitgang laag of LED uit
```
Om de LED uit te zetten, moeten we in dit geval de uitgang ***hoog*** zetten:

**Schema:**
![Schema Actief Laag Uit](img\ac_output_al_off.png)
```cpp
// cpp
digitalWrite(3, HIGH); // Pin 3 hoog, LED uit
```

In **MicroPython** gaat het zo:
```python
# MicroPython
led.value(True); # Uitgang hoog of LED uit
```
of
```python
# MicroPython
led.value(1); # Uitgang hoog of LED uit
``` 


Een **1** of een **0**, **HIGH** of **LOW**, **True** of **False** hebben in beide schema's dus een andere uitwerking. Het is belangrijk om hiermee rekening te houden!
