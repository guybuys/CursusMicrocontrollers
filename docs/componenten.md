# Elektronische componenten

Hier vind je uitleg over de belangrijkste basiscomponenten die we nodig hebben bij het gebruik van microcontrollers of om de werking te beschrijven.

## DC Spanningsbron

**Symbool:** ![Symbool DC bron](img/ac_dc_bron.png)

De spanningsbron is de voeding voor je microcontroller. Dit kan een batterij zijn, een adapter of de USB-poort van je computer.

## Diode

**Symbool:** ![Symbool diode](img/ac_diode.png)

Een diode laat stroom maar in één richting door. Zoals het in dit symbool staat, kan de stroom van boven naar onder stromen maar niet omgekeerd.

## LED (Light Emitting Diode)

**Symbool:** ![Symbool LED](img/ac_led.png)

Een LED is een speciale diode, ze geeft licht als er voldoende stroom doorheen gaat. Gebruik altijd een serieweerstand om ervoor te zorgen dat er niet te veel stroom doorheen vloeit! Dan kan de LED of de uitgang van de microcontroller immers kapot gaan.

## Weerstand

**Symbool:** ![Symbool weerstand](img/ac_weerstand.png)

Een weerstand beperkt de stroom in een circuit. Dit hebben we bijvoorbeeld nodig bij het aansluiten van een LED!

<!--
## Serieweerstand bij LED

- **Schema:** ![Schema LED met weerstand](img/schema_led_weerstand.png)

De serieweerstand voorkomt dat de LED kapot gaat door te veel stroom.
-->

## Zekering (Fuse)

 **Symbool:** ![Symbool zekering](img/ac_fuse.png)

Een zekering beschermt tegen te hoge stroom. Wanneer de stroom te groot wordt, zal de zekering gecontrolleerd doorbranden. Let op: een zekering is geen weerstand, vele leerlingen tekenen een weerstand met het symbool van een zekering maar dat is helemaal verkeerd!

## Schakelaar (SPDT))

- **Foto:** ![SPDT switch](img/SPDT_drawing.jpg)
- **Symbool:** ![Symbool SPDT switch](img/ac_spdt.png)

Met een SPDT (Single Pole Dual Throw) schakelaar of tuimelschakelaar, kan je kiezen of hoe "middelste" contact verbonden wordt. In het model op de foto, kan je zorgen dat het met geen van beiden contact maakt maar dit kan meestal niet. Het is ofwel verbonden met het ene, ofwel met het andere en daar zit slechts een zeer korte "dode tijd" tussen. Deze schakelaar komt later terug bij GPIO output.
